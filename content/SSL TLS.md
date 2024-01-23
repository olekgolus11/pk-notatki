# SSL TLS

Secure Sockets Layer / Transport Layer Security - Protokoły nawiązywania i utajniania połączeń pomiędzy urządzeniami w sieci.

W rzeczywistości TLS jest ulepszeniem SSL: [TLS vs. SSL - wszystko, co musisz wiedzieć](https://jchost.pl/blog/tls/)

- [[#Cechy]]
- [[#Jak działają SSL/TLS]]

## Cechy

Tyczy się to obu protokołów

- Połączenie w sieci przez dany protokół jest bezpieczne, ponieważ **wszystkie** wymieniane dane są **szyfrowane kluczem symetrycznym** (możemy wybrać algorytm)
- Połączenie jest niezawodne, bo do każdej wiadomości dodawana jest checksuma
- Można zweryfikować tożsamość nadawcy korzystając z szyfrowania asymetrycznego (coś jak w [[Podpis elektroniczny|podpisie elektronicznym]])

## Jak działają SSL/TLS:

Serwer i klient w ramach protokołu SSL/TLS ustalają jeden wspólny klucz symetryczny, który będzie używany do szyfrowania danych przekazywanych w sesji:

1. **Nawiązanie połączenia (Handshake)**:

   - **Hello messages**: Na samym początku klient wysyła do serwera wiadomość `ClientHello` zawierającą, między innymi, informacje o obsługiwanych wersjach protokołu, proponowanych algorytmach szyfrowania i sesji. Serwer odpowiada wiadomością `ServerHello`, w której m.in. potwierdza wybraną wersję protokołu i algorytm szyfrowania.
   - **Certyfikat i autentykacja serwera**: Serwer przesyła następnie swój certyfikat cyfrowy (i ewentualnie żąda certyfikatu od klienta), który pozwala na weryfikację jego tożsamości.

   - **Wymiana kluczy**: Serwer może wysłać także `ServerKeyExchange` wiadomość, jeśli jest to potrzebne do ustalenia klucza wymiany, a klient może odpowiedzieć swoją informacją o wymianie kluczy `ClientKeyExchange`.

2. **Wymiana kluczy**:

   - W TLS najczęściej używa się algorytmu wymiany kluczy opartego na szyfrowaniu asymetrycznym (np. RSA) lub na algorytmie Diffiego-Hellmana. Przy RSA, klient generuje tzw. "pre-master secret" i szyfruje go używając publicznego klucza serwera, a serwer deszyfruje ten secret swym prywatnym kluczem.
   - W przypadkach wymiany kluczy Diffiego-Hellmana, zarówno klient jak i serwer współpracują, aby wypracować wspólny sekret bez bezpośredniej jego wymiany.

3. **Pochodne klucze**:

   - Mając "pre-master secret", zarówno klient jak i serwer niezależnie wykorzystują funkcje wypracowania kluczy (Key Derivation Functions, KDF), aby ze wspólnego sekretu utworzyć klucz sesji, który będzie wykorzystywany do szyfrowania i deszyfrowania informacji przekazywanych w danej sesji.

4. **Finalizacja handshake i szyfrowanie danych**:
   - Obydwie strony wysyłają sobie nawzajem wiadomości `Finished`, które są już zaszyfrowane wypracowanym kluczem sesji, co pozwala również na weryfikację, czy cały proces się powiódł i czy od tej pory mogą komunikować się bezpiecznie.

#pk #it
