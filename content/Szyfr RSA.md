# Szyfr RSA
Jest to, tak jak szyfr plecakowy, szyfr asymetryczny.

- [[#Generowanie kluczy]]
- [[#Szyfrowanie]]
	- [[#Przykład szyfrowania]]
- [[#Deszyfrowanie]]
	- [[#Jak obliczyć d?]]
	- [[#Przykład obliczania d]]
- [[#Bezpieczeństwo]]
- [[#Przykład użycia RSA]]

Oprócz tego warto zobaczyć:
- [[Podpis elektroniczny]]

## Małe twierdzenie Fermata
Jeśli $p$ jest liczbą pierwszą, to dla dowolnej liczby całkowitej $a$ liczba $a^{p}-a$ jest podzielna przez $p$.

Wnioski:
- $a_{p-1}\mod p=1$
- $a^{p-1}-1\mod p=0$

## Generowanie kluczy
W przypadku RSA, każda para kluczy posiada dwie liczby:
- Klucz publiczny $(e,N)$
- Klucz prywatny $(d,N)$

>Gdzie $e$ od encryption a $d$ od decryption.

W celu wygenerowania kluczy potrzebujemy pary dwóch liczb pierwszych $p$ oraz $q$.

Niech $p=11$ a $q=3$

1. Wyznaczamy $p$ i $q$
2. Obliczamy $N=p\cdot q=11\cdot 3=33$
3. Obliczamy $\Phi(N)=(p-1)(q-1)=10\cdot2=20$
4. Wyznaczamy takie $e$, które $1<e<\Phi(N)$ oraz $NWD(e,\Phi(N))=1$, np. $e=3$
5. Wyznaczamy takie $d$, które $d\cdot e (\mod\Phi(N))=1$, np. $d=7$
6. Definiujemy parę kluczy asymetrycznych
	   - publiczny: $(e,n)$
	   - prywatny: $(d,n)$
7. Usuwamy wszystko to czego użyliśmy do stworzenia kluczy by nie dało ich się odtworzyć, tzn. $p,q,\Phi$

## Szyfrowanie
Szyfrowanie polega na podstawieniu wartości jawnej do następującego wzoru:
$$S=x^{e}\mod N$$

### Przykład szyfrowania
$p=17, q=23, e=7$
$x=A=66$
$$N=17*23=(20-3)(20+3)=400-9=391$$
$$S=66^{7}\mod391=297$$

## Deszyfrowanie
Deszyfrowanie polega podobnemu wzorowi co przy okazji szyfrowania, jednak zamiast $e$ podstawiamy $d$
$$x=S^{d}\mod N$$

### Jak obliczyć d?
Liczymy $NWD(e, \Phi(N))$, podobnie jak z plecakowym (dla którego liczyliśmy $NWD(m,w)$)

### Przykład obliczania d
$x=297^{151}\mod 391$
$297\mod 391=297$
$297^{2}\mod391=234$
$297^{4}\mod391=234\cdot234\mod391=16$
$297^{8}\mod391=256$
$297^{16}\mod391=239$
$297^{32}\mod391=35$
$297^{64}\mod391=52$
$297^{128}\mod391=358$

$297^{151}\mod391=358*239*16*234*297=66$

## Bezpieczeństwo
Dlaczego RSA jest skutecznym algorytmem?
- Próba odczytania wiadomości wymaga znalezienia $d$
- Aby znaleźć $d$ trzeba znaleźć $p$ i $q$
- Liczby $p$ i $q$ są jednoznacznym wynikiem faktoryzacji $n$

![](https://i.imgur.com/cvb85QL.png)

## Przykład użycia RSA

Więc co tu się dzieje? Chcemy wysłać odbiorcy wiadomość, ale RSA nie jest najszybszym algorytmem, a szyfrowanie całej wiadomości może trochę potrwać.

W tym celu:
1. Pobieramy od odbiorcy jego klucz publiczny do RSA
2. Wybieramy jakiś symetryczny szyfr (który po prostu jest dużo szybszy od asymetrycznego RSA)
3. Szyfrujemy naszą wiadomość tym szyfrem symetrycznym
4. Kluczem RSA szyfrujemy nasz klucz symetryczny
5. Wysyłamy zaszyfrowaną wiadomość i zaszyfrowany klucz symetryczny
6. Odbiorca odszyfrowuje klucz symetryczny swoim kluczem prywatnym
7. Odszyfrowanym kluczem symetrycznym odszyfrowuje wiadomość


![](https://i.imgur.com/Dmle9FD.png)




#pk #it 