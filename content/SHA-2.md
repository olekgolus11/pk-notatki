# SHA-2
Secure Hash Algorithm 2

- [[#Cechy]]
- [[#Sposób działania]]
- [[#Zastosowania]]
- [[#Przykładowe hashe]]

## Cechy
### Rozmiar wyjściowy
Rodzina SHA-2 zawiera kilka funkcji haszujących o różnych długościach skrótu: 
- SHA-224 (224 bity), 
- SHA-256 (256 bitów), 
- SHA-384 (384 bity), 
- SHA-512 (512 bitów).

### Ograniczenia
SHA-2 jest uważany za bezpieczny przy obecnym poziomie technologii i nie ma znanych praktycznych ataków, które podważyłyby jego wiarygodność.

### Szybkość
Algorytmy SHA-2 są generalnie wolniejsze niż [[MD5]] i [[SHA-1]], ale różnica prędkości jest akceptowalna w zamian za zwiększone bezpieczeństwo.

### Bezpieczeństwo
SHA-2 oferuje znacznie silniejsze zabezpieczenia niż [[MD5]] i [[SHA-1]]. Istnieje jednak jeden potencjalny atak, który nie występuje już w SHA-3
> [!info]- Length Extension Attack (poza materiałem, ciekawostka)
> > [!question]+ User
> > Opowiedz o Length Extension Attacks w kontekście SHA2
>
> > [!quote]+ GPT
> > Atak rozszerzenia długości to technika wykorzystywana przeciwko funkcjom haszującym opartym na konstrukcji Merkle–Damgårda, jak SHA-1 i SHA-2, pozwalająca na dodanie danych do znanego skrótu haszującego bez potrzeby znajomości oryginalnych danych. Atakujący, dysponując skrótem i długością oryginalnej wiadomości, dodaje wypełnienie i nowe dane, a następnie oblicza nowy skrót. Atak ten umożliwia fałszowanie wiadomości, wstrzykiwanie kodu, ominięcie ochrony API, przechwytywanie sesji i fałszowanie dokumentów, jeżeli system nie stosuje dodatkowych zabezpieczeń jak HMAC czy SHA-3. Aby się przed nim chronić, rekomendowane jest używanie HMAC, weryfikowanie całkowitej długości danych lub przechodzenie na algorytmy haszujące odporne na taki atak, jak SHA-3.

## Sposób działania

Rodzina SHA-2 zawiera kilka wariantów, ale wszystkie one działają według podobnego schematu:
1. __Wypełnienie wiadomości__: Wiadomość jest wypełniana aby jej długość była wielokrotnością odpowiedniego rozmiaru bloku (512 lub 1024 bity, w zależności od wariantu SHA-2).
2. __Dodanie długości__: Do wiadomości dodaje się reprezentację bitową jej oryginalnej długości.
> [!tip]- Zarówno wypełnianie jak i dodanie długości omówione jest w [[MD5]] i [[SHA-1]], działa to wszędzie tak samo
4. __Inicjalizacja buforów__: Inicjalizuje się zestaw stałych inicjalizacyjnych o długości odpowiadającej rozmiarowi wariantu SHA-2 (np. 256-bitów dla SHA-256).
5. __Przetwarzanie bloków__: Wiadomość przetwarzana jest w blokach, z użyciem funkcji kompresujących. Te funkcje wykorzystują bitowe operacje logiczne, nieliniowe funkcje, operacje modulo i słowa stałe dla każdego bloku, podobnie jak w [[SHA-1]].

## Zastosowania
- __Certyfikaty SSL/TLS__: SHA-256 z rodziny SHA-2 jest standardem dla tworzenia cyfrowych podpisów w certyfikatach SSL/TLS, zapewniając bezpieczeństwo komunikacji w Internecie.
- __Oprogramowanie i bezpieczeństwo systemów operacyjnych__: Używany do weryfikacji aktualizacji oraz integralności plików systemowych.
- __Aplikacje kryptowalutowe__: SHA-256 jest podstawą algorytmu wydobywczego Bitcoina, a SHA-2, ogólniej, znajduje zastosowanie w wielu innych blockchainach i systemach finansowych.
- __Systemy zapobiegające nadużyciom__: SHA-2 jest wykorzystywany w systemach identyfikacji malware, gdzie szybkie i bezpieczne haszowanie pomaga w detekcji i analizie szkodliwego oprogramowania.

## Przykładowe hashe
- $sha256(siema)$=
```
587dff1f72440ab053be2faa39313149fe84fd9ef4f096f50dcc5731c3759c9e
```
- $sha384(siema)$= 
```
b9c8b86f525c1c54d081f20e7604b7daf70ba1a13059d997221f06c5cbee05dfd29d9a38c50e1abdb6eb63ee3d9c8e57
```
- $sha256(siema)$= 
```
638b2488c3e94d6d6f73f8e875f99aa62325152885aa81441b8315245264cebf2b090b60cfe7591a892798094809437915061cb9dd939d6cd35e6a370df669f3
```

#pk #it 