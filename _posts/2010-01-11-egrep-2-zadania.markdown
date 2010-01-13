---
layout: post
title: 2 zadania używające polecenia egrep
---


##{{ page.title }}
zad 1.

Wyszukaj w pliku 1.txt kombinacje wyrazu fir1k2  gdzie na
miejscu 1 ma znaleźć się 'c' lub 'y' a na miejscu 2 ma 
znaleźć sie 'a' lub 'y'
 
Plik 1.txt zawiera:<pre>
</pre>
[mgemba@sigma ~]$ cat 1.txt<pre>
fircyk
fir(c|y)k
firck
firyk
fircyka
fircyku
fircyk(a|u)
fircka
fircku
firyka
firyku
fir(c|y)k(a|u)
fir(c|y)ka
fir(c|y)ku
firck(a|u)
firyk(a|u)</pre><pre>
</pre>
[mgemba@sigma ~]$ egrep 'fir(c|y)k(a|u)' 1.txt<pre>
fircka
fircku
firyka
firyku
</pre>
Gdzie normalny grep znalazłby:<pre>
</pre>
[mgemba@sigma ~]$ grep 'fir(c|y)k(a|u)' 1.txt<pre>
fir(c|y)k(a|u)
</pre>

zad 2.

Wyszukaj w pliku 1.txt kombinacje wyrazu as1|234a gdzie na
miejscu 1 ma znaleźć się 'g' w dowolnej ilości powtórzeń tzn
g lub gg lub ggg itd., na miejscu 2 ma znaleźć sie 'a' lub 'g',
na miejscu 3 ma znaleźć się 's' lub 'f' i na miejscu 4 ma znaleźć 
się 'o' w dowolnej ilości powtórzeń (tak jak 'g' w 1) 

Plik 1.txt zawiera:

[mgemba@sigma ~]$ cat 1.txt<pre>
</pre><pre>
asgg|asoooa
asggg|gfooa
asgggg|aasoa
asg||gfooa
asg|afa
asg|afoa
asg|ofaa
asgg|gsoooooa
aso+a
afo+a
gso+a
</pre>
<pre>
</pre>
[mgemba@sigma ~]$ egrep 'asg+\|[ag][sf]o+a' 1.txt <pre>
</pre><pre>
asgg|asoooa
asggg|gfooa
asg|afoa
asgg|gsoooooa
</pre>
<pre>
</pre>
Gdzie normalny grep potraktowałby znak \| jako znak "lub" oraz + jako znak plusa i znalzłby:<pre>
</pre>

[mgemba@sigma ~]$ grep 'asg+\|[ag][sf]o+a' 1.txt<pre>
</pre><pre>
aso+a
afo+a
gso+a
</pre>