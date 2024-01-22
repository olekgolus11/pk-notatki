# MD5
- [[#Cechy]]
- [[#Zastosowania]]
- [[#Sposób działania]]
- [[#Przykładowe hashe]]

## Cechy
### Rozmiar wyjściowy
Skrót MD5 ma długość 128 bitów (16 bajtów).

### Ograniczenia
Słabe bezpieczeństwo. Słabe odporności na kolizje - mogą być generowane stosunkowo łatwo.

### Szybkość
MD5 jest szybką funkcją haszującą, co przyczyniło się do jego popularności w przeszłości, ale współcześnie jest to postrzegane jako wada w kontekście bezpieczeństwa.

### Bezpieczeństwo
MD5 nie jest już uważany za bezpieczny i nie zaleca się jego używania w aplikacjach wymagających integralności i autentyczności danych.

## Sposób działania
1. __Wypełnienie wiadomości__: Wiadomość jest wypełniana do długości, która jest wielokrotnością 512 bitów, z wyjątkiem dodatkowych 64 bitów na długość oryginalnej wiadomości (czyli na samą wiadomość przewidywane jest 448 bitów).
2. __Dodanie długości__: Do wiadomości dodaje się 64-bitową reprezentację długości oryginalnej wiadomości przed wypełnieniem.
> [!tip]- Demonstracja paddingu
> <iframe style="width: 100%; height:300px" src="https://fthb321.github.io/MD5-Hash/MD5OurVersion2.html"></iframe>
4. __Inicjalizacja bufora__: Wprowadzany jest 4-elementowy bufor, gdzie każdy element jest 32-bitowym rejestrem inicjalizowanym konkretnymi wartościami hexadecymalnymi.
5. __Pretwarzanie bloków__: Wiadomość podzielona jest na 512-bitowe bloki, które są przetwarzane przez główną pętlę funkcji MD5, stanowiącą serię specyficznych operacji matematycznych i bitowych na każdym bloku przy użyciu bufora.

## Zastosowania
- __Weryfikacja plików__: MD5 nadal używany jest do weryfikacji integralności plików, sprawdzając, czy pobrane dane nie uległy zmianie, ale nie jest to zalecane dla zastosowań związanych z bezpieczeństwem.
- __Generowanie identyfikatorów__: Stosowanie MD5 do generowania różnych identyfikatorów (np. w branży gier) gdzie gwarancja unikalności jest ważniejsza niż bezpieczeństwo.
- __Baza danych__: Używanie MD5 do tworzenia prostych skrótów haseł w systemach, gdzie bezpieczeństwo nie jest krytycznym aspektem, ale zalecane jest stosowanie soli.

## Przykładowe hashe

- $md5(czesc)$=`db58ccc1ea56c8cc5ecacabcc961d431`
- $md5(palgume)$=`684c06f28827e145c0a4cbf6fe633c11`
- $md5(kochamgoclawa)$=`5dc58a9890a7a5336bccc8fde1c85392`

#it #pk 