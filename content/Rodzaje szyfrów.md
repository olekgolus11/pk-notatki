# Rodzaje szyfrów
Wyróżniamy dwa typy szyfrów:
- [[#Szyfr symetryczny]]
- [[#Szyfr asymetryczny]]

Porównanie obu typów szyfrów:
- [[#Zarządzanie kluczami]]
- [[#Bezpieczeństwo]]
- [[#Wydajność]]
- [[#Zastosowania]]

## Typy szyfrów
### Szyfr symetryczny
- Używają tego samego klucza do szyfrowania i deszyfrowania danych.
- Szybkie w działaniu.
- Klucz musi być bezpiecznie przekazany obu stronom.
- Przykłady: AES, DES

![](https://i.imgur.com/yfyyloy.png)


## Szyfr asymetryczny
- Używają pary kluczy: publicznego do szyfrowania i prywatnego do deszyfrowania.
- Wolniejsze od szyfrów symetrycznych.
- Umożliwiają dystrybucję klucza publicznego bez ryzyka bezpieczeństwa.
- Przykłady: RSA

![](https://i.imgur.com/jKR7XPT.png)

Tutaj trochę dziwnie się to czyta, ale chodzi w obrazku poniżej o to, że chcemy wysłać jakąś wiadomość bezpiecznie do odbiory, w tym celu:
1. Bierzemy od odbiorcy jego klucz publiczny
2. Szyfrujemy wiadomość przekształcając ją w kryptogram
3. Odsyłamy zaszyfrowaną wiadomość
4. Odbiorca może (i tylko on może) odszyfrować wiadomość

W taki sposób wiadomości, które przechodzą przez np. internet mogą być odczytywane tylko przez odbiorcę, a jeśli "wypłyną" w jakiś sposób z konwersacji, to jako zaszyfrowane.

![](https://i.imgur.com/kZf2Tmf.png)


## Porównanie typów szyfrów
### Zarządzanie kluczami

- W szyfrach symetrycznych zarządzanie kluczami może być wyzwaniem, ponieważ wymaga bezpiecznego wymieniania klucza między stronami, co może być trudne w dużych systemach.
- Szyfry asymetryczne ułatwiają zarządzanie kluczami, ponieważ klucze publiczne mogą być swobodnie dystrybuowane, a klucz prywatny pozostaje tajny.

### Bezpieczeństwo
- Szyfry symetryczne mogą być bardzo bezpieczne, ale bezpieczeństwo zależy od zachowania tajności współdzielonego klucza.
- W szyfrach asymetrycznych bezpieczeństwo opiera się na trudności matematycznych problemów, takich jak faktoryzacja dużych liczb pierwszych w przypadku RSA, co pozwala na bezpieczne trzymanie klucza publicznego.

### Wydajność
- Szyfry symetryczne są zazwyczaj szybsze i bardziej efektywne zasobowo niż asymetryczne, co sprawia, że lepiej nadają się do szyfrowania dużych ilości danych.
- Szyfry asymetryczne są wolniejsze i wymagają więcej zasobów obliczeniowych, co czyni je mniej efektywnymi do szyfrowania dużych ilości danych, lecz użytecznymi do szyfrowania kluczy lub małych bloków danych.


### Zastosowania
- Szyfry symetryczne są często stosowane wtedy, kiedy dwie lub więcej stron posiada bezpieczny kanał do wymiany klucza. Idealnie nadają się do szyfrowania danych w spoczynku oraz do szyfrowania danych przesyłanych na duże odległości.
- Szyfry asymetryczne wykorzystywane są do zabezpieczenia komunikacji w otwartych sieciach, takich jak Internet, gdzie strony nie mogą łatwo wymienić kluczy. Są podstawą dla takich technologii jak SSL/TLS, cyfrowe podpisy oraz systemy certyfikatów.


#pk #it 