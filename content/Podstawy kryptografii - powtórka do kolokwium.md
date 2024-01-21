# Powtórka do kolokwium
1. [[#Szyfr cezara]]
2. [[#Szyfr Vigenere]]
3. [[#Szyfr plecakowy]]
4. [[#RSA]]
5. Funkcje hashujące (skrótu)
6. Podpis cyfrowy
7. Algorytm Diffie-Hellmana
8. DES

- [[RSA laby]]
- [[Bezpieczne hasła wg Manuel'a Blum'a]]
- [[Funkcja skrótu]]

## Szyfr Cezara
Szyfr cezara to najprostszy typ szyfru, polega na przesunięciu danych liter w alfabecie o kilka pozycji. Można go zdefiniować jako:

$$E(x)=(x+k)\mod n$$
Gdzie:
- $x$ to dana litera
- $k$ to liczba przesunięcia
- $n$ to liczba liter w alfabecie

## Szyfr Vigenere
To bardziej zaawansowany szyfr, polega na tym, że każdą literę w haśle przesuwamy zgodnie z odpowiadającą jej literą w kluczu. Można go zdefiniować jako:

$$E(x_i)=(x_i+k_i)\mod n$$

## Szyfr plecakowy
Jest to szyfr asymetryczny. Posiada dwa rodzaje kluczy: publiczny oraz prywatny.

Klucz **publiczny** służy do **zaszyfrowania** wiadomości, natomiast klucz **prywatny** do jej **rozszyfrowania**.

### Specyfikacja algorytmu plecakowego
Mamy tzw. wektor załadunku $a=(a_1,a_2,a_3,...,a_n)$, w którym wszystkie wartości $a$ są różne od siebie.

Jest to taki wektor, który możemy interpretować jaki wagi poszczególnych przedmiotów, które mogą znaleźć się w plecaku. 

Tekst jawny natomiast w przypadku tego szyfru to skończony ciąg binarny, czyli $x=(x_1,x_2,...,x_{n)}$ gdzie $x\in\{0,1\}, i\in\{1,...,n\}$. 

Zatem **szyfrogram** (jako waga całego plecaka) wyraża się wzorem $S=a\cdot x = \sum\limits a_{i}x_{i}$

Podsumowując:
- Klucz publiczny - wektor załadunku **a**
- Tekst jawny (to co szyfrujemy) - wektor binarny **x**
- Szyfr (to co zaszyfrowaliśmy) - iloczyn dwóch wektorów **S**

### Problem deszyfrowania
Jeśli udało nam się dany tekst jawny zaszyfrować, co stanie się w momencie, gdy zechcemy do odszyfrować? Czy da się uzyskać jednoznaczną odpowiedź jeśli wektor załadunku jest dowolnym wektorem?

No niekoniecznie, zauważmy, że jeśli wektor $a=(1,2,3,4,5,6)$ oraz $x=(0,0,1,0,0,0)$, otrzymamy wynik $S=3$. To po jego deszyfracji otrzymamy dwie różne możliwości, albo będzie to $x=(1,1,0,0,0,0)$ albo $x=(0,0,1,0,0,0)$.

Wychodzi na to, że wektor $a$ musi spełniać konkretne warunki, by móc jednoznacznie odszyfrować szyfr.

W tym celu zastosowano użycie **wektora superrosnącego**. Jest to taki wektor, którego suma poprzednich elementów jest mniejsza, niż każdy następujący element.

Na przykład $a=(1,2,4,8,16)$

W ten sposób z łatwością możemy odszyfrować daną wiadomość, ponieważ otrzymamy tylko jeden wynik.

### Klucz prywatny
Ogólnie, można odszyfrować szyfr **S** znając tylko klucz publiczny **a**, natomiast zadanie to stanie się bardzo trudne dla bardzo dużych n (tj, gdy klucz publiczny **a** jest dłuuuugi).

Zadanie rozszyfrowania możemy ułatwić znając klucz prywatny, który możemy uzyskać po następujących krokach:

- Należy przekształcić klucz publiczny **a** na wektor superrosnący **a'**
- Należy przekształcić aktualny szyfr(ogram) **S** na odpowiadający nowemu wektorowi załadunku szyfrogram **S'**, gdzie pierwotna wiadomość **x** nie może ulec zmianie:
$$S'=a'*x'=a'*x$$
- Należy znaleźć takie **m**, które jest większe niż suma wszystkich elementów wektora superrosnącego **a'**.
- Należy znaleźć takie **w**, że $NWD(m,w)=1$
W efekcie, szukamy pary (m,w) liczb pierwszych. Nastęnie, zmodyfikowany wektor załadunku i zmodyfikowany szyfrogram otrzymujemy następująco:
$$a'=w^{-1}a\mod m$$
$$S'=w^{-1}S\mod m$$

Tylko skąd wziąć to **w<sup>-1</sup>**? W tym celu należy posłużyć się szybkim algorytmem euklidesa:
1. Bierzemy nasze $m,w$
2. Rozpisujemy równanie 
$$NWD(m,w)=1$$
$$m : w = a\ r\  r_{1}$$
$$w : r_{1} = b\ r\ r_{2}$$
$$itd...$$
3. Gdy mamy już resztę równą 0, należy rozpisać równiania pomocnicze, które opisują daną resztę (np. $r_{1}=1\cdot m - w\cdot a$)
4. Następnie, pod ostatnie równanie podstawiamy tak liczby, by w efekcie uzyskać:
   $$1=x\cdot m+w^{-1}\cdot w$$

## RSA
Jest to, tak jak szyfr plecakowy, szyfr asymetryczny. Posiada dwa rodzaje kluczy: publiczny oraz prywatny.

Klucz **publiczny** służy do **zaszyfrowania** wiadomości, natomiast klucz **prywatny** do jej **rozszyfrowania**.

### Generowanie kluczy
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

### Szyfrowanie
Szyfrowanie polega na podstawieniu wartości jawnej do następującego wzoru:
$$S=x^{e}\mod N$$

#### Przykład
$p=17, q=23, e=7$
$x=A=66$
$$N=17*23=(20-3)(20+3)=400-9=391$$
$$S=66^{7}\mod391=297$$

### Deszyfrowanie
Deszyfrowanie polega podobnemu wzorowi co przy okazji szyfrowania, jednak zamiast $e$ podstawiamy $d$
$$x=S^{d}\mod N$$

#### Jak obliczyć d?
Liczymy $NWD(e, \Phi(N))$, podobnie jak z plecakowym (dla którego liczyliśmy $NWD(m,w)$)

#### Przykład
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

## Zadanka

[[PK-Kolokwium.excalidraw]]