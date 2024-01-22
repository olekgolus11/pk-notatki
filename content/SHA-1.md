# SHA-1
Secure Hash Algorithm 1

- [[#Cechy]]
- [[#Sposób działania]]
- [[#Zastosowania]]
- [[#Przykładowe hashe]]

## Cechy
### Rozmiar wyjściowy
SHA-1 generuje skrót o długości 160 bitów (20 bajtów).

### Ograniczenia
Teoretyczne i praktyczne ataki wykazały możliwość generowania kolizji, co osłabia wiarygodność SHA-1 w zastosowaniach kryptograficznych (podobnie jak w przypadku [[MD5]])
### Szybkość
SHA-1 jest wolniejszy niż [[MD5]], ale w kontekście bezpieczeństwa szybkość nie zawsze jest pożądana z cechą. Oferuje lepsze bezpieczeństwo niż [[MD5]], ale obecnie również uważany za niewystarczająco bezpieczny.

### Bezpieczeństwo
Od 2017 roku eksperci zaliczają SHA-1 do grupy funkcji haszujących, których używanie w nowych systemach jest odradzane ze względu na słabości w odporności na kolizje.

## Sposób działania
1. __Wypełnienie wiadomości__: Wiadomość jest wypełniana do długości, która jest wielokrotnością 512 bitów, z wyjątkiem dodatkowych 64 bitów na długość oryginalnej wiadomości (czyli na samą wiadomość przewidywane jest 448 bitów).
2. __Dodanie długości__: Do wiadomości dodaje się 64-bitową reprezentację długości oryginalnej wiadomości przed wypełnieniem.
> [!tip]- Demonstracja paddingu (działa identycznie jak w MD5)
> <iframe style="width: 100%; height:300px" src="https://fthb321.github.io/MD5-Hash/MD5OurVersion2.html"></iframe>
3. __Inicjalizacja bufora__: SHA-1 korzysta z 160-bitowego bufora podzielonego na pięć 32-bitowych słów, które są inicjalizowane specyficznymi wartościami.
4. __Przetwarzanie bloków__: Tak jak w MD5, wiadomość jest przetwarzana blok po bloku. Każdy blok przetwarzany jest w serii czterech rund, gdzie każda z nich zawiera 20 operacji z użyciem nieliniowych funkcji, operacji bitowych i stałych.

![](https://i.imgur.com/XJqqeMM.png)


## Zastosowania
- Kiedyś szeroko stosowany, obecnie organizacje odchodzą od SHA-1 na rzecz bezpieczniejszych algorytmów z rodziny [[SHA-2]] i SHA-3.
- __Kompatybilność z starszymi systemami__: Niektóre starsze aplikacje i systemy nadal mogą wymagać SHA-1 z powodu historycznej kompatybilności.
- __Systemy kontroli wersji__: Takie jak Git, gdzie SHA-1 używany jest do identyfikacji i sprawdzania integralności zmian, jednakże prace nad migracją do bezpieczniejszych funkcji są już w toku.

## Przykładowe hashe
- $sha1(siema)$=`1df75881f71e2a25393d3089b668206f5d54d56f`
- $sha1(omegabrug)$=`3c60ca308fa451c08ad616583c7747d8b5a984e4`

#it #pk 