# Szyfr DES
Całkiem szybki szyfr symetryczny, który wykonuje podstawowe operacje na bitach, obecnie rzadko stosowany, gdyż ani bezpieczeństwem, ani wydajnością nie ma podjazdu do [[Szyfr AES|AES]].

- [[#Cechy]]
- [[#Ograniczenia]]
- [[#Kroki algorytmu]]

## Cechy
- Podstawową cechą tego szyfru jest to że wykonuje elementarne operacje na bitach.
- Długość klucza wynosi **56** lub **64** bity.
- Sam algorytm szyfruje **64**-bitowe bloki danych.
- Proces szyfrowania składa się z **16** iteracji
- Do każdej iteracji **generowany jest inny klucz**
- No i skoro jest symetryczny to **każda iteracja jest odwracalna**

## Ograniczenia
- $2^{56}$ możliwych kombinacji
- Znajomość fragmentu klucza znacznie ułatwia kryptoanalizę
- Współcześnie możliwy do złamania w ciągu kilku dni
- Z uwagi na charakterystykę szyfru, próba zastosowania go dwukrotnie z dwoma różnymi kluczami nie zwiększy bezpieczeństwa
- Posiada pewną liczbę kluczy słabych, których należy unikać

## Kroki algorytmu

Nie ma co się tego uczyć na pamięć ale warto kojarzyć

1. Permutacja 64-bitowego bloku danych
2. Podział na dwie 32-bitowe części
3. Wybór 56 bitów klucza i podział na dwie części
4. Funkcja Feistela (16 iteracji)
	1. Przesunięcie bitów klucza o 1 lub 2 miejsca
	2. Permutacja wybierająca 48 bitów klucza
	3. Rozszerzenie prawej połowy danych z 32 do 48 bitów
	4. XOR klucza z prawą połową
	5. Podział na 6 bitowe części przesyłane do S-bloków
	6. Łączenie i permutacja danych z S-bloków
	7. XOR z lewą połową i zamiana miejsc
5. Ponowne złączenie lewej i prawej strony bloku danych
6. Permutacja końcowa (odwrotna do tej z punktu pierwszego)

![](https://i.imgur.com/NjIqIiP.png)
![](https://i.imgur.com/QskLST0.png)



#pk #it