# Zadania z krypto

![](https://i.imgur.com/yZofNDw.png)

> [!example]- Odpowiedź na zadanie 1
>
> - ✅ Tak, po prostu musi tak być, inaczej nie będziemy mogli tego wyliczyć - [[Arytmetyka modularna#Warunek konieczny istnienia odwrotności modularnej]]
> - ✅ Tak, zachodzi taka właściwość [[Szyfr RSA#Małe twierdzenie Fermata]]
> - ❌ Nie, działamy na modulo B, więc ile byśmy B nie dodali, i tak wielokrotności B znikną
> - ❌ Nie, wynikiem będzie liczba z zakresu $0,1,2,...,B-1$

> [!example]- Odpowiedź na zadanie 2
>
> - ✅ Tak, nie ma ku temu żadnych przeszkód
> - ❌ Nie, generalnie $\phi$ lub jak ktoś miał na labach $N$ to mnożenie dwóch liczb pierwszych $p$ i $q$. W przypadku gdy jedna z nich jest równa $2$ ($2$ to liczba pierwsza), to wtedy $phi=2\cdot q$, czyli może być parzysta
> - ❌ Chyba nie, liczbę $\phi$ dobieramy w zupełnie inny sposób, czyli poprzez mnożenie dwóch liczb pierwszych $p$ i $q$. Liczby $d$ i $e$ mają z nimi niewiele wspólnego.
> - ✅ Tak, $n=p\cdot q$, gdzie $p$ i $q$ to liczby pierwsze.

> [!example]- Odpowiedź na zadanie 3
> Skoro chcemy wysłać wiadomość szyfrowaną hybrydową, to na pewno treść wiadomości szyfrujemy AESem. Skorzystamy ze swojego klucza symetrycznego. Musimy teraz w jakiś sposób przesłać wiadomość razem z kluczem symetrycznym, no ale nie wyślemy klucza jawnie. Możemy skorzystać z asymetrycznego klucza publicznego odbiorcy, którym zaszyfrujemy nasz klucz symetryczny. Wtedy odbiorca bezpiecznie go sobie odszyfruje swoim prywatnym.
>
> Czyli podsumowując:
> ✅ Asymetryczny klucz publiczny odbiorcy
> ✅ Symetryczny klucz nadawcy
>
> Inne opcje nie wchodzą w grę. Musimy mieć cokolwiek od odbiorcy, ponieważ jeśli wszystkie szyfry wychodziły by tylko od nadawcy, to każdy mógłby je odebrać i odszyfrować, skoro akurat ten jeden konkretny odbiorca też może.
>
> Klucz symetryczny odbiorcy też wchodzi w grę. Zakładając, że chciałby nam go wysłać, musiałby go najpierw zaszyfrować, a czym? No naszym kluczem publicznym. Mielibyśmy więc dostęp do klucza symetrycznego, zaszyfrowalibyśmy wiadomość, i odesłali bez niczego więcej. Jednak nie jest to stosowana taktyka:
>
> > [!cite]- GPT
> > W sytuacji, którą opisujesz, gdzie odbiorca wysyła swój klucz symetryczny do nadawcy, rzeczywiście musiałby go zaszyfrować kluczem publicznym nadawcy, aby zapewnić bezpieczeństwo przesyłania. Jednak nie jest to standardowa praktyka w szyfrowaniu hybrydowym, ponieważ wymagałoby to, aby odbiorca najpierw bezpiecznie przekazał swój klucz symetryczny nadawcy, co komplikuje proces i wprowadza dodatkowe ryzyko bezpieczeństwa.
> > Standardowa procedura szyfrowania hybrydowego nie wymaga, aby nadawca posiadał klucz symetryczny odbiorcy. Zamiast tego nadawca generuje własny klucz symetryczny, który jest używany tylko raz (tzw. klucz sesyjny) i jest bezpiecznie przekazywany do odbiorcy zaszyfrowany kluczem publicznym odbiorcy.

> [!example]- Odpowiedź na zadanie 4
>
> - ✅ Tak, funkcje hashujące zawsze zwracają jednakowo długie hashe
> - ❌ Nie, wiadomości z hasha nie da się odtworzyć
> - ❌ Fałsz, można uzyskać, nazywa to się kolizją
> - ✅ Tak, to jest jedna z cech funkcji hashujących

> [!example]- Odpowiedź na zadanie 5
> Szyfrowanie: - $S=W^{e}\mod n$
> Deszyfrowanie: - $W=S^{d}\mod n$

> [!example]- Odpowiedź na zadanie 6
> Klucz symetryczny w AES może mieć 128, 192 albo 256. Wystarczająco bezpieczna jest długość 128 bitów.

> [!example]- Odpowiedź na zadanie 7
> Pojęcie naiwnego bezpieczeństwa to ocena skuteczności bezpieczeństwa danego szyfru bazująca jedynie na ilości możliwych kluczy. Przykładowo, szyfrowanie wiadomości szyfrem vigenere może wyeskalować do nieskończoności możliwych kluczy, jednak nie czyni go to w żaden sposób bezpiecznym, ponieważ jest podatny na wiele innych ataków poza brute forcem.

> [!example]- Odpowiedź na zadanie 8
>
> 1. RSA:
>    - Plusy:
>      - Jest szyfrem bezpiecznym
>      - Posiada parę kluczy, co umożliwia wymianę wiadomości bez ryzyka że ktoś inny ją odczyta
>    - Minusy:
>      - Jest dużo wolniejszy od szyfrów symetrycznych
>      - Wymaga dużo większej mocy obliczeniowej by zapewnić podobne bezpieczeństwo co AES
> 2. AES:
>    - Plusy:
>      - Jest szyfrem bezpiecznym
>      - Jest bardzo szybki, bazuje na prostych operacjach matematycznych
>    - Minusy:
>      - Jest szyfrem symetrycznym, co uniemożliwia korzystanie z niego w sposób publiczny tak jak RSA. Nie podeślemy komuś klucza by zaszyfrował wiadomość i nam ją odesłał
>
> Dlaczego są wykorzystywane wspólnie? Ponieważ idealnie się uzupełniają. Skoro RSA jest w stanie "nadawać" klucz publiczny, by móc pozwolić potencjalnym nadawcom coś do nas wysłać, to należy jedynie jeszcze pozwolić im zaszyfrować daną wiadomość efektywnie. A mogą to zrobić przy wykorzystaniu AES. Tworzą sobie klucz "sesji", którym szyfrują wiadomość, a następnie kluczem publicznym RSA szyfrują ten klucz sesji i nam go odsyłają. My możemy sobie ten klucz odszyfrować i przeczytać wiadomość.

![](https://i.imgur.com/El3dJUm.png)

> [!example]- Odpowiedź
>
> - ❓ To jest albo błąd, albo pułapka (hasło w kontekście kryptografii to to samo co szyfr, czyli zaszyfrowana wiadomość, a czytając to polecenie myślimy od razu o kluczu)
> - ✅ Tak, skoro mamy klucz to i kłódka powinna od razu puścić
> - ✅ Tak, inaczej mielibyśmy do czynienia z hashem
> - ✅ Tak, np. RSA o $p=7$ i $q=3$ ma chujowe naiwne bezpieczeństwo, i przez to też łatwo jest ten przypadek zbruteforceować

![](https://i.imgur.com/sH0Kq4f.png)

> [!example]- Odpowiedź
>
> - ✅ $Y=X^{e}\mod \phi$
> - ✅ $X=Y^{d}\mod n$
>
> Ważna uwaga, $\phi$ to to samo co $n$. Nie rozumiem po co wykładowca dorzuca zbędne komplikacje

![](https://i.imgur.com/wVK8yzK.png)

> [!example]- Odpowiedź
> SPZAVWHK

![](https://i.imgur.com/vzajOcV.png)

> [!example]- Odpowiedź na zadanie 13
>
> - ❌ Oj nie bracje, wektor plecaka odpowiada wektorowi binarnemu, czyli 3 to byłoby $1234+599$
> - ✅ Tak, bo każdy znak w ASCII to jeden bajt, czyli 8 bitów, a wektor załadunku tutaj ma 8 bitów więc gituwa
> - ❌ Nie mogą być, bo to są liczby które służą do przekształcenia plecaka łatwego w trudny, one muszą mieć $NWD=1$. To nie są liczby które dorzucamy do plecaka!!!
> - ❌ Spełnia, wektor jest superrosnący

> [!example]- Odpowiedź na zadanie 14
>
> - $(2,5,15,33,67,150,313,750)$
> - $(0,1,0,0,1,1,1,0)$

> [!example]- Odpowiedź na zadanie 15
> Jest jako pierwsze zadanie w teście na górze

![](https://i.imgur.com/vi8dnHq.png)

> [!example]- Odpowiedź na zadanie 9
> ✅ - Tak, to główna charakterystyka hasha, dlatego są bezpieczne bo nie prezentują żadnych widocznych zależności
> ❌ - W teorii funkcja powinna to zapewniać, ale jest to matematycznie niemożliwe, nawet jeśli [[SHA-2|SHA512]] generuje $2^512$ możliwych hashy, to i tak jest to skończona liczba, nieważne jak duża, zawsze istnieje prawdopodobieństwo kolizji
> ❌ - LIE, hash z danego algorytmu ma zawsze tą samą długość
> ✅ - Dokładnie tak, pisałem o tym wyżej

> [!example] Odpowiedź na zadanie 10
> [[SSL TLS#Jak działają SSL/TLS:]]

> [!example]- Odpowiedź na zadanie 11
> Zakładając, że przyjmujemy, że klucz posiada 56 bitów (oczywiście zabrakło w specyfikacji zadania ale staram się nie wkurwiać), to należy policzyć to tak:
>
> 1. Od 56 bitów odejmujemy 3\*4 bity (bo jedna szesnastkowa liczba to 4 bity), zostaje nam 44 bity
> 2. Czas średni to ilość kombinacji / 2, czyli $2^44/2=2^{43}$

> [!example] Odpowiedź na zadanie 12
> No tego akurat w notatkach nie mam :D

![](https://i.imgur.com/KrQYjti.png)

> [!example] Odpowiedź na zadanie 6
> Dla [[Szyfr AES|AES]] może być 128, 192 i 256

> [!example] Odpowiedź na zadanie 7
> Wyjaśniałem wyżej

> [!example] Odpowiedź na zadanie 8
> Niezłe gówno, zauważcie że to się zapętla po prostu

![](https://i.imgur.com/QaUqva0.png)

> [!example] Odpowiedź na zadanie 4
>
> - ❌ Nie, wyjaśniałem wyżej
> - ❌ Musi być, na tym polega algorytm
> - ✅ Tak, po prostu tak
> - ✅ Niby tak, ale czemu to chuj wie, nie ma to żadnego uzasadnienia, nie ma nic w internecie, wartości e i d nie mają żadnego bezpośredniego powiązania.

![](https://i.imgur.com/lfpu8tf.jpg)

> [!example] Odpowiedź na zadanie 5
> A było wyżej hehe

> [!example] Odpowiedź na zadanie 6
> Nie gwarantuje, ponieważ istnieje wiele innych metod złamania szyfru. Świetnym przykładem jest [[Szyfr Vigenere]] który pomimo tego że posiada nieskończenie wiele różnych kombinacji, można szybko zawęzić poszukiwanie poprzez kryptoanalizę z użyciem np. [[O kryptoanalizie#Metoda anagramowa|metody anagramowej]].

> [!example] Odpowiedź na zadanie 7
> Dobrze, zatem:
>
> 1. Funkcja skrótu musi być jednokierunkowa - odwrócenie hasha nie ma być możliwe
> 2. Funkcja skrótu musi być wrażliwa - mała zmiana musi bardzo znacząco wpływać na generowanego hasha by niemożliwe było szukanie patternów przy ewentualnym odwracaniu hasha
> 3. Funkcja skrótu powinna generować wystarczająco duże hashe - w ten sposób unika się ewentualnych kolizji, a sama funkcja jest bezpieczniejsza
> 4. Funkcja skrótu powinna być szybka - funkcje hashujące są wykorzystywane do hashowania min. dużych dokumentów, zatem ich wydajność jest kluczowa
> 5. No i najważniejsze - funkcja skrótu powinna generować takiego samego hasha dla tej samej wiadomości, w przeciwnym wypadku funkcje hashujące byłyby nieużyteczne

> [!example] Odpowiedź na zadanie 8
> Szyfr stosuje operacje XOR na każdym bicie wiadomości. Szyfr sam w sobie raczej rzadko o ile w ogóle używany, jednakże operacja XOR jest wykorzystywana w wielu innych algorytmach szyfrujących, np. w [[Szyfr AES|AES]].

#pk #it
