---
layout: post
title: egrep ściąga
---

<blockquote>
<img src="../../../../images/egrep.png" alt="[Egrep logo]" />
<p>
  Grep - (Global Regular Expression Print)
  <pre>
  </pre>
    Egrep (to samo co grep -E) przeszukuje wskazane pliki wejściowe 
  (lub standardowe wejście jeśli nie podano żadnych), szukając linii
  zawierających coś pasującego do podanego wzorca. Domyślnie, egrep 
  wypisuje pasujące linie, tak samo jak grep z różnicą, że w grepie
  w wyrażeniach regularnych metaznaki:<pre>
   </pre>?, +, {, |, ( oraz )<pre>
   </pre> tracą swoje
  szczególne znaczenie; zamiast nich należy użyć wersji z odwrotnym 
  ukośnikiem: <pre>
  </pre>\?, \+, \{, \|, \( oraz \).<pre>
  </pre> W erepie metaznaki nie tracą
  swojego znaczenia.
  </pre>
</p>

</blockquote>



## Egrep - wyrażenia regularne:



  Znaki zwyczajne:

a, A,, b, B, z, Z, 0, 1, 9, , ! …

  Znaki specjalne (metaznaki):

Rozróżnia się dwa zbiory metaznaków: metaznaki
rozpoznawane w dowolnym miejscu wzorca poza
nawiasami kwadratowymi:

^, $,, *, +, ?, ., (, ), [, ], {, }, \

oraz metaznaki rozpoznawane wewnątrz nawiasów
kwadratowych.

\, ^,, -, ]

I tak jak wczesniej napisałem metaznaki nie traca swojego znaczenia czyli:

egrep - grep -E, jest to rozszerzony grep z dodatkową obsługą metaznaków w 
wyrażeniach regularnych ?,+,| ()  



## Przykłady:
<pre>
Plik 1.txt zawiera:

??bla bla &^% :)
?
*
.*
sdfghjk
)ab)s
sadfa|sdf
sad^^aa
</pre>
polecenie grep '?' 1.txt wyszuka nam nastepujace linie:
<pre>
[mgemba@sigma ~]$ grep '?' 1.txt :

??bla bla &^% :)
?
</pre>
czyli dopasuje wiersze w ktory zawarty jest znak zapytania '?'

natomiast polecenie egrep '?' 1.txt wyszuka nam:
<pre>
[mgemba@sigma ~]$ egrep '?' 1.txt

??bla bla &^% :)
?
*
.*
sdfghjk
)ab)s
sadfa|sdf
sad^^aa
</pre>
Dzieje sie tak ponieważ metaznak '?' nie traci swojego znaczenia.

##Znaczenia metaznaków: (Ściąga)

  Kropka "." oznacza dowolny znak

  Gwiazdka "*" oznacza dowolny znak 

  Pałka "|" to operator OR (lub).

  Podwzorzec może być zamknięty w niepodzielnej grupie za
pomocą nawiasów "( )". W ten sposób można użyć gałęzi nie
tylko dla całego wzorca, ale też dla jego fragmentów

  Zestaw znaków między nawiasami kwadratowymi oznacza
dowolny znak objęty nawiasami kwadratowymi "[]"

  Daszek "^" oznacza początek wiersza np. wyrażenie ^A wyszuka wszystkie 
wersze zaczynjące się na A

  Dolar "$" oznacza koniec wiersza np. A$ wyszuka wszystkie wiersze 
kończące się na A

  Podwzorzec może być zamknięty w niepodzielnej grupie za
pomocą nawiasów "[ ]"np. [abc] wyszuka wszystkie wiersze, które zawierają
 a , b lub c
 
  [^ ] 	pasuje do każdego znaku, oprócz tych zawartych w nawiasach

  Znak zapytania "?" po symbolu oznacza najwyżej jedno (być
może zero) wystąpienie poprzedzającego wyrażenia

  Gwiazdka "*" po symbolu, (nawiasie, pojedynczym znaku)
nazywana jest dopełnieniem Kleene'a i oznacza zero lub więcej
wystąpień poprzedzającego wyrażenia

  Plus "+" po symbolu oznacza co najmniej jedno wystąpienie
poprzedzającego go wyrażenia






