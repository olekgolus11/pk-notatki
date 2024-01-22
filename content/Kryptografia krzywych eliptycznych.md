# Kryptografia krzywych eliptycznych (ECC)
ECC opisuje zestaw współczesnych algorytmów asymetrycznych.

- [[#Charakterystyka ECC]]
- [[#Krzywa eliptyczna]]
- [[#Materiały wyjaśniające]]
- [[#Schemat działania]]
- [[#Szyfrowanie]]
- [[#Deszyfrowanie]]

## Charakterystyka ECC
- Względnie wysoka wydajność obliczeniowa
- Krótkie klucze w porównaniu do RSA
- Wysokie bezpieczeństwo

## Krzywa eliptyczna
W kryptografii stosujemy postać Weierstrassa

$$y^{2}=x^{3}+ax+b$$

<iframe src="https://www.desmos.com/calculator/gwsbplymof?embed" width="100%" height="500" style="border: 1px solid #ccc" frameborder=0></iframe>

## Materiały wyjaśniające
- [Elliptic Curves - Computerphile](https://www.youtube.com/watch?v=NF1pwjL9-DE) - polecanko
- [Obszerny artykuł](https://cryptobook.nakov.com/asymmetric-key-ciphers/elliptic-curve-cryptography-ecc) - tutaj jest wszystko ale za długie żeby czytać

## Schemat działania
1. Wybieramy dużą liczbę pierwszą p (tu przykład $17$)
2. Dla wybranych parametrów krzywej eliptycznej a i b definiujemy skończone ciało p punktów leżących na krzywej 
3. Każdy punkt w wybranym ciele ma całkowite x i y z zakresu od 0 do p-1 
4. Działania na elementach tego ciała realizowane są w arytmetyce modulo p
5. Tworzymy krzywą oraz nałożone na nią skończone ciało składające się z punktów o współrzędnych całkowitych

![](https://i.imgur.com/jFG1eEo.png)

6. Wybieramy punkt $G$ w zaprojektowanym ciele (tzw. generator)
7. Wybieramy liczbę całkowitą d z zakresu $0, 1, …, p-1$.
8. Obliczamy $P=d\cdot G$ - będzie to również punkt w ciele
9. Wyróżniamy klucz prywatny $d$ oraz publiczny $P$

## Szyfrowanie
   1. Alice chce przesłać bezpiecznie wiadomość (W), którą reprezentuje jako punkt na krzywej.
> [!tip]- O co chodzi z tym że wiadomość jest punktem na krzywej?
> > [!cite]+ GPT
> > W kryptografii krzywych eliptycznych (ECC), reprezentacja wiadomości jako punktu na krzywej jest niezbędna do wykonania operacji kryptograficznych, takich jak szyfrowanie, podpis cyfrowy czy wymiana kluczy. Nie możemy bezpośrednio operować na tekstach czy słowach, musimy je najpierw zamienić na elementy z których składa się krzywa eliptyczna – punkty leżące na niej. Oto proces, za pomocą którego możemy zamienić wiadomość, jak na przykład słowo "motocykl", na punkt krzywej eliptycznej:
> > 
> > "motocykl" może zostać zakodowane jako ciąg bajtów (jeżeli użyjemy ASCII) 109 111 116 111 99 121 107 108, który może zostać potraktowany jako duża liczba, lub przekształcony w system szesnastkowy.
> > 
> > Liczba uzyskana w pierwszym kroku musi następnie zostać "umiejscowiona" na krzywej, co oznacza znalezienie takiego punktu \( (x, y) \), który leży na krzywej i którego pierwsza współrzędna \( x \) jest równa liczbie reprezentującej wiadomość, lub pochodnej tej liczby. W praktyce proces ten może być bardziej skomplikowany i wymagać zastosowania specjalnych technik i założeń, aby zapewnić, że na krzywej znajdziemy punkt odpowiadający naszej wiadomości.
   
   2. Alice losuje tymczasowy klucz (k) i oblicza dwa punkty: (C_1 = kG), który jest punktem dołączonym do zaszyfrowanej wiadomości, oraz (C_2 = W + kP), gdzie (W) to wiadomość reprezentowana jako punkt na krzywej, a (kP) to mnożenie klucza publicznego odbiorcy (P) przez losowy skalar (k).
   3. Zaszyfrowana wiadomość to para ((C_1, C_2)).
## Deszyfrowanie

1. Odbiorca (Bob) otrzymuje zaszyfrowaną wiadomość ((C_1, C_2)) oraz zna swój klucz prywatny (d) i oblicza (C_1' = dC_1).

2. Bob, mając (C_1') (który jest równy (kdG)), może odwrócić działanie zastosowane przez Alice, obliczając (W = C_2 - C_1'). Odejmuje (kdG) od (C_2), ponieważ (kdG) był użyty przez Alice do „przesunięcia” wiadomości (W) na krzywej, a Bob może takie przesunięcie odwrócić.

3. Rezultatem jest otryzmywanie punktu, który odpowiada oryginalnej wiadomości (W) - Bob pomyślnie deszyfrował wiadomość.


#it #pk  