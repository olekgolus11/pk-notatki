# O kryptoanalizie

- [[#Brute force]]
- [[#Złamanie Vigenere - kryptoanaliza szyfrów podstawieniowych]]
- [[#Kryptoanaliza szyfrów blokowych]]

## Brute force

- Sprawdzenie pojedynczego klucza wymaga czasu
- Dla klucza o długości L bitów sprawdzenie wszystkich kombinacji zajmie $2^{L}T$ czasu
- Przeciętny czas potrzebny do znalezienia poprawnej kombinacji wynosi $2^{L-1}T$
- Istnieją sposoby przyspieszenia metody brutalnego ataku poprzez odrzucenie niemożliwych kombinacji.

### Brute force DES

Przykład: Brutalny atak na DES

- Klucz: $**************$
- Przeciętny czas potrzebny do znalezienia klucza: $2^{55}T$
- Klucz: $*****\ 9********$
- Przeciętny czas potrzebny do znalezienia klucza: $2^{51}T$
- Znajomość jednego znaku (hex) w kluczu szesnastokrotnie skraca czas brutalnego ataku.

### Brute force RSA

- Znamy N będące iloczynem różnych liczb pierwszych p i q
- Gdy istnieje k liczb pierwszych < N, mamy k(k – 1) kombinacji
- Możemy skorzystać z właściwości: Gdy p\*q = N oraz p ≠ q, to p < sqrt(N) oraz q > sqrt(N)
- Istnieje k1 liczb pierwszych < sqrt(N) oraz k2 liczb pierwszych > sqrt(N) i < N. Mamy k1 k2 możliwych kombinacji.

## Złamanie Vigenere - kryptoanaliza szyfrów podstawieniowych

- Szyfr Vigenere wykorzystuje klucz dowolnej długości składający się z elementów danego alfabetu.
- Naiwne bezpieczeństwo szyfru Vigenere to ∞

Dlaczego więc ten szyfr jest łatwy do złamania?

### Łamanie przez długość klucza

- Metoda Kasiskiego – wyszukiwanie powtarzających się ciągów znaków w zakodowanej wiadomości.
- Indeks koincydencji: prawdopodobieństwo, że przy porównaniu dwóch tekstów znak po znaku kolejne znaki będą takie same.
- Metoda Friedmana – obliczenie indeksu koincydencji zaszyfrowanego tekstu i jego kolejnych przesunięć.

## Kryptoanaliza szyfrów blokowych

### Metoda anagramowa

- Dla każdego języka można obliczyć częstotliwość występowania poszczególnych symboli.
- Kryptogram może być przeanalizowany pod kątem częstotliwości występowania danych symboli, par oraz trójek.
- Otrzymany rezultat może być porównany ze średnią dla danego języka w celu uzyskania przesunięć

### Metoda różnicowa

- Polega na równoległym szyfrowaniu dwóch jawnych (różnych) tekstów danym algorytmem
- Analizujemy zmiany w tych tekstach w kolejnych iteracjach
- Wyznaczamy charakterystyki – zmiany w poszczególnych iteracjach pojawiające się często dla danej różnicy
- Wykorzystując charakterystyki przypisujemy prawdopodobieństwa do różnych kluczy

### Metoda liniowa

- Polega na aproksymacji przekształceń wykonanych w jednej rundzie algorytmu funkcją liniową z pewnym prawdopodobieństwem występowania.
- Złożenie takich funkcji daje nam relację probabilistyczną pomiędzy bitami wejścia-wyjścia.
- Uzyskane prawdopodobieństwa pomagają dotrzeć do klucza użytego przy szyfrowaniu.

#pk #it
