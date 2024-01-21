# Szyfr AES
Jest to współczesny szyfr symetryczny. Na chwilę obecną jest uważany za bezpieczny i nie został złamany w sensie praktycznym; jest standardem przyjętym i zalecanym przez rządy i wiele organizacji na całym świecie.


## Cechy
- Wykorzystuje klucz **128**, **192** lub **256**-bitowy
- Szyfruje wiadomości w bloach **128**-bitowych
- Polega na wykonaniu pewnej liczby iteracji (innej dla różnych rozmiarów klucza)

## Kroki algorytmu
Też nie warto się tego uczyć, warto wiedzieć tylko tyle że są iteracje tak jak w przypadku DES, ale tutaj na macierzach


1. Podział danych na 128-bitowe bloki ułożone w tablice 4x4B
2. Generowanie klucza dla pierwszej rundy
3. Runda inicjująca - XOR danych i pierwszego klucza
4. Rundy szyfrujące - **9**, **11** lub **13** dla kolejno kluczy **128**, **192** i **256**
	1. Zastąpienie każdego bajtu danych innym na podstawie z góry znanej tablicy Rijandela
	2. Przesuwanie wierszy w trzech ostatnich macierzach stanu
	3. Mnożenie kolumn przez stałą macierz z liczbami 1, 2, 3
	4. Generowanie podklucza dla danej iteracji i wykonanie operacji XOR z macierzą danych
5. Runda końcowa – skrócona runda szyfrująca


#pk #it 