# Podpis elektroniczny
Na przykładzie szyfru [[Szyfr RSA|RSA]] oraz dowolnej funkcji hashującej.
- [[#Tworzenie podpisu elektronicznego]]
- [[#Weryfikacja podpisu elektronicznego]]

## Tworzenie podpisu elektronicznego:

1. __Generacja kluczy__: Użytkownik, który chce tworzyć podpis, musi wygenerować parę kluczy RSA: klucz prywatny (używany do podpisywania) i klucz publiczny (używany do weryfikacji podpisu). Klucz prywatny jest tajny i musi być chroniony. Klucz publiczny może być dystrybuowany otwarcie.

2. __Hashowanie wiadomości__: Pierwszym krokiem jest wygenerowanie skrótu (hashu) przekazywanej wiadomości. Używa się do tego funkcji skrótu, takich jak SHA-256, która przekształca wiadomość każdej długości w krótki, stały ciąg bajtów.

3. __Szyfrowanie skrótu__: Otrzymany skrót wiadomości jest następnie szyfrowany za pomocą klucza prywatnego nadawcy. W kontekście RSA, szyfrowanie skrótu za pomocą klucza prywatnego tworzy podpis elektroniczny.

4. __Dołączenie podpisu do wiadomości__: Podpisany skrót jest dołączany do wiadomości lub przesyłany oddzielnie w zależności od implementacji systemu.

## Weryfikacja podpisu elektronicznego:

1. __Otrzymanie wiadomości i podpisu__: Odbiorca otrzymuje wiadomość razem z podpisem. Odbiorca musi mieć dostęp do klucza publicznego nadawcy, który może być rozpowszechniony przez serwis certyfikatów cyfrowych lub w inny zaufany sposób.

2. __Hashowanie otrzymanej wiadomości__: Odbiorca generuje skrót otrzymanej wiadomości za pomocą tej samej funkcji haszującej, której użył nadawca.

3. __Deszyfrowanie podpisu__: Odbiorca używa klucza publicznego nadawcy do deszyfrowania podpisu, co powinno zwrócić skrót wiadomości, jeśli podpis jest prawidłowy.

4. __Porównanie skrótów__: Odbiorca porównuje skrót wyliczony z wiadomości z tym uzyskanym po deszyfrowaniu podpisu. Jeżeli skróty są identyczne, oznacza to, że wiadomość nie została zmieniona w trakcie transmisji i że została podpisana kluczem prywatnym nadawcy, co autentycznego pochodzenia.

![](https://i.imgur.com/LZSSENF.png)

#pk #it