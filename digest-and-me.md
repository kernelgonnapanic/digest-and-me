#$Digest and me
### beginner programmer's thoughts
![angular](angular.png)

---

## About me
<div class="photo">
![ania](ggc-ania.jpg)
</div>
<div class="photo-info">
###Anna Konopka
- front-end developer in <span style="color:#ff385c">PGS Software</span>
- co-organizer of Wrocław<br><span style="color:#ff385c">Geek Girls Carrots</span>
- running a blog <br>[<span style="color:#ff385c">Bookie & Cookie</span>](bookieandcookie.blogspot.com)

Note:
- obecnie pracuje w PGS Software
- swoja przygode z front-endem zaczęłam 6 miesięcy temu
- w czasie wolnym organizuje spotkania wrocławskich Geek Girls Carrots
- comiesięczne spotkania na które zaprawszamy zainteresowanych szeroko pojętym
  światem IT oraz warsztaty
- prowadzę też blog bookie & cookie na którym dziele się swoim spojrzeniem na IT

---


##Angular - first impressions
![kitten](cat.gif)
<!-- .element: style="width:700px;" -->

Note:
- o Angularze dowiedziałam sie majac juz podstawy Html, Css, liznąwszy wcześniej
  JQuery
- postanowiłam napisać pracę inżynierską, w której stacku miał się znaleźć angular
  będąc jeszcze taką nieporadną jak ten kot
- punkt - zamieszczenie kota w prezentacji można zaliczyć ;)

- jakieś tam dyrektywy, serwisy - nie wiedziałam z czym to sie je

---

<!--.slide: data-background="./coding.gif"  -->


##Hello world!
<!-- .element: style="color:white;" -->

Note:
- pierwsze małe aplikacje
- odkrycie 2-way data binding (zazwyczaj działał ;)
- dependency injection
- łatwość mockowania
- pierwsze WOW miałam za sobą

---

##But...

Note:
- trafiłam do komercyjnego projektu, dość specyficznego bo
pod urządzenia mobilne
operującego na dużej ilości danych do tego zmiennych w czasie

- no i pojawił się problem

---

![](huston.jpg)
<!-- .element: style="width: 400px;" -->


Note:
- pewnego dnia gdy na ekranie komputera zauważyłam, że Angular zwija sie z bólu i płacze
- a tak na serio - to po prostu było wolne
- timeline w dev toolsach nie kłamie
- Angular nie wyrabia

---

## Why?

Note:
- okazało się, że Angular nie robi niczego automagicznie, bo niby dlaczego by miał
- za 2-way data bindingiem stoi mechanizm digest loop i dirty checkingu
- każdy utworzony binding np. reagujący na click, tworzy nowy $$watcher

---

##<span class="tex2jax_ignore">$$watchers</span>

Note:
- w reakcji na eventy (np. click) Angular wywołuje pętlę digestu, która
  evaluuje wszystkie watch na danych scopie, sprawdza czy ich wartość jest różna od
  poprzedniej a nastepnie uruchamia digest na scopach potomnych, gdy którykolwiek z watchy stwierdzil, ze wartosc sie zmienila uruchamiamy caly proces od nowa
- zatrzymujemy sie w punkcie rownowagi gdy zaden z watcherów nie zauwazyl zmiany

---

##<span class="tex2jax_ignore">$scope.$apply()</span>
## vs
##<span class="tex2jax_ignore">$scope.$digest()</span>

Note:
- digest mozemy rowniez wywolac z zewnatrz angulara za pomoca apply
- musimy miec jednak swiadomosc ze jest to digest wywolany na rootscopie, ktory
  propaguje sie przez cala aplikacje
- mozemy rowniez wywolac digest na konkretnym scopie - wtedy jednak musimy miec pewnosc
  ze w jego wyniku nie zmieni sie cos na co powinnien zareagowac jakis scope nadrzedny
  poniewaz dirty checking przeprowadzony zostanie tylko dla tego scope'a i scopów dziedzi
- uwaga na digest in progress

---

##What to do?

Note:
- Angular radzi sobie rozsądnie z ok. 2000 watcherów, ale zalezy to od stabilności
  twojego systemu
- naszym zadaniem jest mu pomóc i sprawić, by digest był jak najkrótszy, a aplikacja
  jak najszybsza
- mamy na to wiele sposobów

---

<!--.slide: data-background="./cat.jpg"  -->

##Be aware of $$watchers
<!-- .element: style="color:white;" -->

Note:
- musimy wiedzieć skąd biorą się te watchers:
  binding w htmlu
  dyrektywy angularowe ng-if, ng-show, ng-hide etc
  $scope.$watch

---

##<span>Reasonable use of <span style="color:#FF385C">$apply</span> and <span style="color:#FF385C">$digest</span></span>

Note:
- używać apply tylko tam gdzie trzeba, a gdzie jest to możliwe zastępować go
  digest

---

## :: to the rescue
<code>{{::title}}</code>

Note:
- one-time binding tworzy watcher ale po pierwszym obliczeniu wartości watcher jest usuwany i nie jest brany pod uwage w trakcie digestu, zmniejsza to liczbe watcherów które są sprawdzane w każdym cyklu digest
- można używać gdy wartość się nie zmienia

---


## Be careful with ng-repeat
![](babies.jpg)
<!-- .element: style="width: 600px;" -->

Note:
- być ostrożnym co wkładamy do środka ng-repeatu, bo mnożymy liczbe watcherów
  przez ilosc stworzonych nowych scopów

---

## When to avoid Angular?

Note:
- kiedy nie potrzebujesz mechanizmu Angulara, mozesz go ominąć
- Ale: rób to tylko wtedy kiedy jesteś pewien, że daje Ci to realne korzyści
  w kontekście wydajnośći - timeline, dev Toolsy będą przydatne
- zeciemnia kod, tylko wtedy kiedy masz realny bonus w wydajnosci
- mozemy uzywac pure DOMu

---

<!--.slide: data-background="./promise.gif"  -->

##Promises
<!-- .element: style="color:#ff385c;" -->


Note:
- kazdy then jest źródłem nowego apply, 5 thenów na promisie powoduje
co najmniej 5 cykli digestu
- co wiecej kazdy then jest asynchroniczny wiec mamy okazje zobaczyc flashe
  na UI z tego powodu wynikajace

---

## Not only dirty-checking

Note:
- dirty checking nie jest zazwyczaj najwiekszym problemem
- problemem jest to gdy w wyniku zaobserwowanej zmiany manipulujemy DOM
  np. dodajemy usuwany elementy/modyfikujemy atrybuty
- jedne z najwolniejszych operacji w przegladarce
- rozwiazanie: np. cachowanie dom nodów zamiast ich usuwania (chowanie)
  lub korzystanie z puli dostepnych dom nodów i podmienianie ich zawartości

---

<!--.slide: data-background="./bye.gif"  -->

## Goodbye AngularJS...
<!-- .element: style="color:white;margin-top: 160px;" -->

Note:
- czasami musimy się po prostu pogodzić z tym, że Angular nie nadaje się
  do wszystkich zastosowań,
- i tak, gdy np. sprawdza się przy aplikacjach z dużą ilością formularzy
  i znacznie przyspiesza pracę albo nadaje się do prototypowania
- tak ma kłopoty z byciem wydajnym przy przetwarzaniu i aktualizowaniu dużych
  drzew DOM, zawierających wiele zmiennych elementów
- i gdy angular nie pasuje do profilu projektu, może warto będzie go zastąpić
  Reactem lub którąś z lekkich bibliotek do DOM diffingu jak virtual DOM

---

##Questions?

---

## Thanks for your attention!


###Anna Konopka

![](zdjecie.jpg)
<!-- .element: style="border-radius:50%; height:300px" -->

anna.konopka@zdwola.pl<br>
kernelgonnapanic.github.io
