# Szyfr Plecakowy
Jest to szyfr asymetryczny więc posiada dwa rodzaje kluczy: publiczny oraz prywatny.

- [[#Specyfikacja algorytmu plecakowego]]
- [[#Odszyfrowanie - problemy]]
	- [[#Prosty szyfr plecakowy]]
		- [[#Przykład prostego szyfru plecakowego]]
	- [[#Trudny szyfr plecakowy]]

## Specyfikacja algorytmu plecakowego
Mamy tzw. wektor załadunku $a=(a_1,a_2,a_3,...,a_n)$, w którym wszystkie wartości $a$ są różne od siebie.

Jest to taki wektor, który możemy interpretować jaki wagi poszczególnych przedmiotów, które mogą znaleźć się w plecaku. 

Tekst jawny natomiast w przypadku tego szyfru to skończony ciąg binarny, czyli $x=(x_1,x_2,...,x_{n)}$ gdzie $x\in\{0,1\}, i\in\{1,...,n\}$. 

Zatem **szyfrogram** (jako waga całego plecaka) wyraża się wzorem $S=a\cdot x = \sum\limits a_{i}x_{i}$

Podsumowując:
- Klucz publiczny - wektor załadunku **a**
- Tekst jawny (to co szyfrujemy) - wektor binarny **x**
- Szyfr (to co zaszyfrowaliśmy) - iloczyn dwóch wektorów **S**

## Odszyfrowanie - problemy
Jeśli udało nam się dany tekst jawny zaszyfrować, co stanie się w momencie, gdy zechcemy do odszyfrować? Czy da się zawsze uzyskać jednoznaczną odpowiedź jeśli wektor załadunku jest dowolnym wektorem?

### Prosty szyfr plecakowy
Prostym szyfrem plecakowym nazywamy taki problem, w którym każda kombinacja elementów daje jednoznaczne rozwiązanie.

Aby mogło do tego dojść, wektor załadunku musi być **superrosnący**, to znaczy, że suma wszystkich elementów $(a_{1}, a_{2}..., a_{n-1})$ musi być mniejsza niż $a_{n}$.

Odszyfrowywanie przebiega wtedy bez problemu, bo dostajemy jednoznaczną odpowiedź.

#### Przykład prostego szyfru plecakowego
![](https://i.imgur.com/r60PRx6.png)


### Trudny szyfr plecakowy
Zakładamy, że posiadamy klucz do prostego szyfru plecakowego. W tym celu chcielibyśmy by nasz wektor załadunku nie był już wektorem superrosnącym co nie? Jeśli tak się stanie, naszej wiadomości nie będzie dało się rozszyfrować jednoznacznie.

W tym celu należy:
1. Wybrać taką liczbę $n$, która jest większa od sumy elementów prostego plecaka
2. Wybrać taką liczbę $c$, dla której $NWD(c,n)=1$
3. Znajdujemy taką liczbę $d$, która jest odwrotnością modularną $c$, tzn. $d=c^{-1}\mod n$, posłuży nam ona do odszyfrowywania

![](https://i.imgur.com/JXqEgZ5.png)
![](https://i.imgur.com/5pAbhZ0.png)



#pk #it 