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
![](https://i.imgur.com/sH0Kq4f.png)
![](https://i.imgur.com/wVK8yzK.png)
![](https://i.imgur.com/vzajOcV.png)
![](https://i.imgur.com/vi8dnHq.png)
![](https://i.imgur.com/KrQYjti.png)
![](https://i.imgur.com/QaUqva0.png)
![](https://i.imgur.com/lfpu8tf.jpg)
![](https://i.imgur.com/Am2leJs.jpg)

#pk #it
