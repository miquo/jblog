---
layout: post
title: Skrypt makedict.sh
---
<blockquote>
<img src="../../../../images/scripts.gif" alt="[scripts]" />
<p><pre>
   </pre>"Bo od skryptów można oszaleć..."
   </p>

</blockquote>

##{{ page.title }}

Poprawiony skrypt:
<pre>
#!/bin/bash

E_BADARGS=64
if [ ! -r "$1" ]                                                  
then                                                             
  echo "Usage: $0 files-to-process"
  exit $E_BADARGS
fi
cat $* |                                                          
        tr A-Z a-z |
        tr Ą ą |
        tr Ć ć |
        tr Ę ę |
        tr Ł ł |
        tr Ń ń |
        tr Ó ó |
        tr Ś ś |
        tr Ż ż |
        tr Ź ź |                                                  
        tr ' ' '\012' |                                           
        tr -c '\012aąbcćdeęfghijklłmnńoóprsśtuwxyzżź' '\012' |   
                                                                  
        sort |                        
        uniq |                                                    
        grep -v '^#' |                                            
        grep -v '^$'                                              

exit 0
</pre><pre>
</pre>
Program po wypisaniu pliku zamienia wszystkie wielkie litery na małe, nastepnie każda spację zamienia na nową linie nastepnie usuwa wszystkie znaki nie należące do zbioru (aąbcćdeęfghijklłmnńoóprsśtuwxyzżź) zamieniając je na nowe linie nastepnie sortuje otrzymane wyrazy
usuwa duplikaty i puste linie, a wiec w końcowym efekcie otrzymujemy wyrazy z tekstu posortowane w kolejności alfabetycznej:)







 <pre>
</pre>
<pre>
</pre>Działannie na przykładzie:
<pre>
</pre><pre>
</pre>
[mgemba@sigma ~]$ cat 1.txt<pre>
</pre><pre>
</pre>
<pre>
ącki ąbki
ćab
Ćabka
Ącab
Ńber
ńścer
Śnier
12ąsafs
1asxva
1e31
-=2a
+_b
_.,g
</pre>

[mgemba@sigma ~]$ ./makedict.sh 1.txt<pre>
</pre><pre>
</pre>
<pre>
a
asx
ąbki
ącab
ącki
ąsafs
b
ćab
ćabka
e
g
Ņścer
ńber
śnier
</pre>

Jest jeden błąd w działaniu programu niespowodowany błędem w kodzie tj. program zamienia małe ń na odwrócone wielkie Ņ
ale powód tego hmm nie jest do końca jasny ponieważ skyrp jest poprawny:) 