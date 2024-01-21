# Arytmetyka modularna
Arytmetyka modularna jak sama nazwa wskazuje, tyczy się modulo, oznaczającego resztę z dzielenia.

- [[#Odwrotność modularna]]
- [[#Warunek konieczny istnienia odwrotności modularnej]]
- [[#Szukanie odwrotności modularnej]]

## Odwrotność modularna
O odwrotności modularnej mówimy że:
$$b=a^{-1}\mod c$$
<p style="text-align:center;">("b" jest odwrotnością "a" w arytmetyce modulo "c" wtedy gdy)</p>

$$a\cdot b\mod c=1$$

> [!warning]- Odwrotność modularna nie musi istnieć dla każdej liczby! 
> $2$ nie ma odwrotności w arytmetyce $\mod 4$
> $6$ nie ma odwrotności w arytmetyce $\mod 9$

## Warunek konieczny istnienia odwrotności modularnej
By istniała odwrotność modularna liczby $a$ w arytmetyce modulo $c$ konieczne jest by:
$$NWD(a,c)=1$$

## Szukanie odwrotności modularnej
Do szukania odwrotności modularnej danej liczby wykorzystujemy odwrócony algorytm Euklidesa

Załóżmy że szukamy odwrotności liczby $w$ w arytmetyce $\mod m$

1. Bierzemy nasze $w,m$
2. Rozpisujemy równanie 
$$NWD(w,m)=1$$
$$m : w = a\ r\  r_{1}$$
$$w : r_{1} = b\ r\ r_{2}$$
$$itd...$$
3. Gdy mamy już resztę równą 0, należy rozpisać równiania pomocnicze, które opisują daną resztę (np. $r_{1}=1\cdot m - w\cdot a$)
4. Następnie, pod ostatnie równanie podstawiamy tak liczby, by w efekcie uzyskać:
   $$1=x\cdot m+w^{-1}\cdot w$$

(łatwiej jest to zrozumieć na liczbach mimo wszystko)

#pk #it 