# Szyfr Vigenere
To bardziej zaawansowany szyfr symetryczny, polega na tym, że każdą literę w haśle przesuwamy zgodnie z odpowiadającą jej literą w kluczu. 

- [[#Wzór]]
- [[#Klucz]]
- [[#Autoklucz]]
- [[#Przykład szyfrowania]]

## Wzór

Szyfr można go zdefiniować jako:

$$E(x_i)=(x_i+k_i)\mod n$$

Gdzie:
- $x$ to dana litera
- $k$ to litera klucza
- $i$ to indeks zarówno litery hasła jak i litery klucza
- $n$ to liczba liter w alfabecie

## Klucz
Kluczem może być dowolny tekst. Jeśli klucz jest krótszy niż hasło, to klucz się zapętla.

Ważne jest to by klucz był w tym samym alfabecie co hasło.

## Autoklucz
Autokluczem jest wybrany tekst (chociaż tutaj uczymy się że jest to tylko jedna litera) z tekstem jawnym, który chcemy zaszyfrować.

Przykład:
- Tekst jawny: **BAŚKA MIAŁA FAJNY**
- Autoklucz: **OBAŚKA MIAŁA FAJNY**

Jak można się domyślić, bardzo łatwo jest zbruteforcować rozwiązanie takiego autoklucza, którego klucz składa się z jednej litery poprzedzającej, dlatego wykorzystuje się dłuższe klucze.



## Przykład szyfrowania

![](https://i.imgur.com/pZ3nuPY.png)


#pk #it 