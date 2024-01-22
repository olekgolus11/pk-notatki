# Funkcje skrótu
Funkcja skrótu (tzw. hash function) to funkcja generująca hash o konkretnej ustalonej długości dla dowolnych danych wejściowych.

Dane wejściowe są wypełniane dodatkowymi bitami (do wielokrotności 512 bitów, ale w niektórych [[SHA-2]] nawet do 1024)

Przykładowe działanie:

$$MD5("Ala\ ma\ kota") = 91162629d258a876ee994e9233b2ad87$$

## Cechy funkcji hashujących
- **Deterministyczna** - z tej samej wiadomości zawsze powstanie dokładnie ten sam hash
- **Jednokierunkowa** - hash nie może być w żaden sposób odtworzony do odtworzenia wiadomości
> [!attention]- Niektóre hashe da się odwtorzyć
> Istnieją bazy mapowań danych popularnych tekstów/słów na hashe. Dzięki nim możemy "odwrócić" hasha. Działa to jednak tylko w przypadku często używanych fraz, dlatego zaleca się tworzenie unikalnych i bezpiecznych haseł.
> <iframe style="width: 100%; margin-top: 20px; height:300px" src="https://md5.gromweb.com"></iframe>
- **Bezkolizyjna*** - niemożliwe jest uzyskanie dwóch wiadomości z tym samym hashem
> [!warning]- Nie jest to prawda
> Szczerze nie wiem czemu tak jest napisane na prezentacji wykładowej, ale to właśnie z tego powodu, że funkcje hashujące są kolizyjne (świetnym przykładem jest [MD5 Collision](https://www.mscs.dal.ca/~selinger/md5collision/)) stosuje się dodatkowe metody przeciwdziałania kolizjom:
> 1. __Przechodzenie na bezpieczniejsze algorytmy__:
> 	 - Przestawienie się na używanie silniejszych algorytmów haszujących, takich jak SHA-256 lub SHA-3, które mają wyższą odporność na kolizje i inne typy ataków.
> 2. __„Salting”__:
> 	- Dodawanie losowego ciągu bajtów, znanego jako "sól" (salt), do danych przed ich haszowaniem, co zmienia wynikowy skrót i utrudnia szukanie kolizji oraz brute forcy.
>1. __Strengthening („wzmocnienie”)__:
> 	- Użycie techniki zwaną "key stretching", która polega na wielokrotnym haszowaniu danych, zazwyczaj w połączeniu z solą, aby zwiększyć czas potrzebny do przeprowadzenia ataków.
- **Wrażliwa** - drobne zmiany w wiadomości skutkują dużymi zmianami w hashu
> [!example]- Przykład
> $md5(bailaela)=85dbe73d609a5863d03b63b6e28720c7$
> $md5(bailaelo)=405e3e57a1c16d4d890aeb021cd20e0c$
- **Wydajna** - hash generujemy bardzo szybko dla dowolnej wiadomości

## Popularne funkcje hashujące
- [[MD5]]
- [[SHA-1]]
- [[SHA-2]], rodzina funkcji takich jak: SHA224, SHA256, SHA384, SHA512

#it #pk