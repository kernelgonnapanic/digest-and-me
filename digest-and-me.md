#$Digest i ja
### przemyślenia początkującej programistki
![angular](angular.png)

---

## O mnie
<div class="photo">
![ania](ggc-ania.jpg)
</div>
<div class="photo-info">
###Anna Konopka
- front-end developer w PGS Software
- współorganizatorka spotkań wrocławskich Karotek
- prowadząca blog [Bookie & Cookie](bookieandcookie.blogspot.com)

Note:
- obecnie pracuje w PGS Software
- swoja przygode z front-endem zaczęłam 6 miesięcy temu
- w czasie wolnym organizuje spotkania wrocławskich Geek Girls Carrots
- comiesięczne spotkania na które zaprawszamy zainteresowanych szeroko pojętym
  światem IT oraz warsztaty
- prowadzę też blog bookie & cookie na którym dziele się swoim spojrzeniem na IT

---


##Angular - pierwsze wrażenia
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

##Ale...

Note:
- trafiłam do komercyjnego projektu, dość specyficznego bo
pod urządzenia mobilne
operującego na dużej ilości danych do tego zmiennych w czasie

- no i pojawił się problem

---

![](huston.jpg)
<!-- .element: style="width: 500px;" -->


Note:
- pewnego dnia gdy przyszłam do pracy zobaczyłam jak angular zwija się z bólu leżąc
między naszymi biurkami w biurze
- a tak na serio - to po prostu było wolne
- timeline w dev toolsach nie kłautomagicznie
- Angular nie wyrabia

---

## DLACZEGO?

Note:
- okazało się, że Angular nie robi niczego automagicznie, bo niby dlaczego by miał
- coś sprawdza czy

---

##<span class="tex2jax_ignore">$DIGEST, $APPLY, $WATCH</span>

Note:


---

## Co robić?


---

## <span class="tex2jax_ignore">$scope.$digest()</span>

---


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

##Pytania?

---

## Dziękuję za uwagę!


###Anna Konopka

![](zdjecie.jpg)
<!-- .element: style="border-radius:50%; height:300px" -->

anna.konopka@zdwola.pl<br>
kernelgonnapanic.github.io
