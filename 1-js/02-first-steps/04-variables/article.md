# Muuttujat

JavaScript ohjelmien täytyy useimmiten käsitellä tietoa. Tässä on kaksi esimerkkiä:
1. Verkkokauppa -- tiedot voisivat sisältää myytäviä tuotteita ja ostoskorin.
2. Chat sovellus -- tiedot voisivat sisältää käyttäjiä, viestejä ja paljon muuta.

Näiden tietojen varastoimiseen käytetään muuttujia.

## Muuttuja

[Muuttuja](https://fi.wikipedia.org/wiki/Muuttuja_(ohjelmointi)) on nimetty tietovarasto tiedolle. Voimme käyttää muuttujia varastoimaan kaupan hyödykkeitä, vierailijoita ja muuta dataa.

Luodaksesi muuttujan JavaScriptissa, käytä avainsanaa `let`.

Alla oleva lauseke luo (toisin sanoen: *esittelee*) muuttujan, jonka nimi on "message":

```js
let message;
```

Voimme nyt varastoida siihen tietoja käyttämällä sijoitus operaattoria `=`:

```js
let message;

*!*
message = 'Hello'; // varastoidaan merkkijono 'Hello' muuttujaan nimeltä message
*/!*
```

Merkkijono on nyt varastoitu muistin osaan, joka on liitetty muuttujaan. Pääsemme siihen käsiksi muuttujan nimen avulla:

```js run
let message;
message = 'Hello!';

*!*
alert(message); // näyttää muuttujan sisällön
*/!*
```

Tiiviyden vuoksi voimme yhdistää muuttujan esittelyn ja arvon sijoituksen yhteen riviin:

```js run
let message = 'Hello!'; // esitellään muuttuja ja sijoitetaan arvo

alert(message); // Hello!
```

Voimme myös esitellä useamman muuttujan yhdellä rivillä:

```js no-beautify
let user = 'John', age = 25, message = 'Hello';
```

Tuo näyttää lyhyemmältä, mutta emme suosittele sitä. Paremman luettavuuden vuoksi kannattaa käyttää yhtä riviä per muuttuja.

Monirivinen versio on vähän pidempi, mutta se on helpompi lukea:

```js
let user = 'John';
let age = 25;
let message = 'Hello';
```

<<<<<<< HEAD
Jotkut ihmiset esittelevät useampia muuttujia monella rivillä myös tällaisella tavalla:
=======
Some people also define multiple variables in this multiline style:

>>>>>>> 34a80e70f8cce5794be259d25f815d7a7db7cbe3
```js no-beautify
let user = 'John',
  age = 25,
  message = 'Hello';
```

...Tai jopa "pilkku ensin" tyylillä:

```js no-beautify
let user = 'John'
  , age = 25
  , message = 'Hello';
```

Teknisesti kaikki nämä vaihtoehdot tekevät saman asian. On siis kyse lähinnä henkilökohtaisista mieltymyksistä ja estetiikasta. 

````smart header="`var` instead of `let`"
Vanhemmissa skripteissä saattaa esiintyä myös `var` avainsana `let`:n sijaan:

```js
*!*var*/!* message = 'Hello';
```

<<<<<<< HEAD
Tämä `var` avainsana on *lähes* sama asia kuin `let`. Myös se esittelee muuttujan, mutta vähän erilaisella, "vanhanaikaisella" tavalla.

Avainsanojen `let` ja `var` välillä on pieniä eroja, mutta ne eivät vielä vaikuta meihin. Käsittelemme niitä yksityiskohtaisesti kappaleessa <info:var>.
=======
The `var` keyword is *almost* the same as `let`. It also declares a variable but in a slightly different, "old-school" way.

There are subtle differences between `let` and `var`, but they do not matter to us yet. We'll cover them in detail in the chapter <info:var>.
>>>>>>> 34a80e70f8cce5794be259d25f815d7a7db7cbe3
````

## Tosielämän analogia

On helpompi ymmärtää "muuttuja" käsite, jos kuvittelemme sen olevan "laatikko" datalle, jossa on uniikki nimitarra.

<<<<<<< HEAD
Esimerkiksi muuttuja `message` voidaan kuvitella laatikoksi, joka on merkattu `"message"` tarralla ja jonka sisällä on arvo `"Hello!"`:
=======
For instance, the variable `message` can be imagined as a box labelled `"message"` with the value `"Hello!"` in it:
>>>>>>> 34a80e70f8cce5794be259d25f815d7a7db7cbe3

![](variable.svg)

Voimme laittaa laatikkoon minkä tahansa arvon.

<<<<<<< HEAD
Voimme myös muuttaa sitä niin usein kuin haluamme:
=======
We can also change it as many times as we want:

>>>>>>> 34a80e70f8cce5794be259d25f815d7a7db7cbe3
```js run
let message;

message = 'Hello!';

message = 'World!'; // arvo muuttuu

alert(message);
```

Kun arvoa muutetaan, vanha data poistetaan muuttujasta:

![](variable-change.svg)

Voimme myös esitellä kaksi muuttujaa ja kopioida dataa niiden välillä.

```js run
let hello = 'Hello world!';

let message;

*!*
// kopioidaan 'Hello world' hello-muuttujasta message-muuttujaan
message = hello;
*/!*

// nyt kahdessa muuttujassa on sama arvo
alert(hello); // Hello world!
alert(message); // Hello world!
```

````warn header="Kahdesti esitteleminen aiheuttaa virheen"
Muuttujan voi esitellä vain kerran.

Saman muuttujan esitteleminen useamman kerran aiheuttaa virheen:

```js run
let message = "This";

// toistuva 'let' johtaa virheeseen
let message = "That"; // SyntaxError: 'message' has already been declared
```
Meidän pitää siis esitellä muuttuja kerran ja sen jälkeen viitata siihen ilman `let` avainsanaa.
````

<<<<<<< HEAD
```smart header="Funktionaaliset kielet"
On mielenkiintoista huomata, että on olemassa [funktionaalisia](https://fi.wikipedia.org/wiki/Funktionaalinen_ohjelmointi) ohjelmointikieliä kuten [Scala](http://www.scala-lang.org/) tai [Erlang](http://www.erlang.org/), jotka kieltävät muuttujien arvojen muuttamisen.
=======
```smart header="Functional languages"
It's interesting to note that there exist so-called [pure functional](https://en.wikipedia.org/wiki/Purely_functional_programming) programming languages, such as [Haskell](https://en.wikipedia.org/wiki/Haskell), that forbid changing variable values.
>>>>>>> 34a80e70f8cce5794be259d25f815d7a7db7cbe3

Tällaisissa kielissä "laatikkoon" varastoitu arvo on siellä ikuisesti. Jos meidän täytyy varastoida jotain muuta, kieli pakottaa meidät luomaan uuden laatikon (esittelemään uuden muuttujan). Vanhaa ei voida käyttää uudelleen.

<<<<<<< HEAD
Vaikka tämä vaikuttaisi ensinäkemältä vähän oudolta, nämä kielet kykenevät hyvin vakavaan sovelluskehitykseen. Lisäksi on olemassa alueita, kuten rinnakkaislaskelmia, joilla tämä rajoitus tuo tiettyjä etuja. Tällaisen kielen opiskelu (vaikka et aio käyttää sitä pian) on suositeltavaa mielesi laajentamiseksi.
=======
Though it may seem a little odd at first sight, these languages are quite capable of serious development. More than that, there are areas like parallel computations where this limitation confers certain benefits.
>>>>>>> 34a80e70f8cce5794be259d25f815d7a7db7cbe3
```

## Muuttujien nimeäminen [#variable-naming]

JavaScriptissa on kaksi rajoitusta muuttujien nimille:

1. Nimen täytyy sisältää vain kirjaimia, numeroita tai merkkejä `$` ja `_`.
2. Ensimmäinen merkki ei saa olla numero.

Esimerkkejä pätevistä nimistä:

```js
let userName;
let test123;
```

Kun nimi sisältää useampia sanoja, käytetään yleensä [camelCasea](https://fi.wikipedia.org/wiki/CamelCase). Eli: sanat kirjoitetaan peräkkäin niin, että kaikki paitsi ensimmäinen alkaa isolla kirjaimella: `minunTosiPitkaNimi`.

On mielenkiintoista, että dollarimerkkiä `'$'` ja alaviivaa `'_'` voidaan käyttää nimissä. Ne ovat tavallisia symboleita samoin kuin kirjaimet, eikä niillä ole erityistä merkitystä.

Nämä nimet ovat päteviä:

```js run untrusted
let $ = 1; // esittelee muuttujan nimellä "$"
let _ = 2; // ja nyt muuttujan nimellä "_"

alert($ + _); // 3
```

Esimerkkejä vääristä nimistä:

```js no-beautify
let 1a; // ei voi alkaa numerolla

let my-name; // viivoja '-' ei sallita
```

<<<<<<< HEAD
```smart header="Kirjainkoolla on merkitystä"
Muuttujat `apple` ja `AppLE` ovat kaksi eri muuttujaa.
```

````smart header="Ei-latinalaiset kirjaimet ovat myös sallittuja, mutta niitä ei suositella"
On mahdollista käyttää mitä tahansa kieltä, mukaanlukien kyrilliset aakkoset ja jopa hieroglyfit, tähän tapaan:
=======
```smart header="Case matters"
Variables named `apple` and `APPLE` are two different variables.
```

````smart header="Non-Latin letters are allowed, but not recommended"
It is possible to use any language, including Cyrillic letters, Chinese logograms and so on, like this:
>>>>>>> 34a80e70f8cce5794be259d25f815d7a7db7cbe3

```js
let имя = '...';
let 我 = '...';
```

<<<<<<< HEAD
Periaattessa tässä ei ole virhettä. Tällaiset nimet ovat sallittuja, mutta kansainvälinen tapa on käyttää englantia muuttujien nimissä. Myös pienissä skripteissä, niillä voi olla pitkä elämä. Muista maista tulevien ihmisten on ehkä luettava sitä joskus.
=======
Technically, there is no error here. Such names are allowed, but there is an international convention to use English in variable names. Even if we're writing a small script, it may have a long life ahead. People from other countries may need to read it sometime.
>>>>>>> 34a80e70f8cce5794be259d25f815d7a7db7cbe3
````

````warn header="Varatut nimet"
On olemassa [lista varatuista sanoista](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#Keywords), joita ei voida käyttää, koska niitä käytetään kielessä itsessään.

Esimerkiksi `let`, `class`, `return`, ja `function` ovat varattuja.

Alla oleva koodi antaa syntaksivirheen:

```js run no-beautify
let let = 5; // muuttujan nimi ei voi olla "let", virhe!
let return = 5; // se ei voi olla myöskään "return", virhe!
```
````

````warn header="Sijoitus ilman `use strict` komentoa"

Tavallisesti meidän pitää esitellä muuttuja ennen sen käyttöä. Ennen vanhaan oli periaattessa mahdollista luoda muuttuja ihan vaan sijoittamalla arvo ilman, että käytti `let` avainsanaa. Tämä toimii edelleen, jos emme sijoita `use strict` komentoa skripteihimme, jotta yhteensopivuus vanhojen skriptien kanssa säilyy.

```js run no-strict
// huom: ei "use strict" komentoa

num = 5; // muuttuja "num" luodaan, jos sitä ei ole olemassa

alert(num); // 5
```

Tämä on huono tapa ja aiheuttaisi virheen strict tilassa:

```js
"use strict";

*!*
num = 5; // error: num is not defined
*/!*
```
````

## Vakiomuuttujat

Vakiomuuttujan (ei muutu) voi esitellä käyttämällä `const` avainsanaa `let` avainsanan sijasta:

```js
const myBirthday = '18.04.1982';
```

Muuttujia, jotka esitellään `const` avainsanalla kutsutaan "vakiomuuttujiksi". Niiden arvoa ei voida sijoittaa uudelleen. Yrittäminen aiheuttaisi virheen:

```js run
const myBirthday = '18.04.1982';

myBirthday = '01.01.2001'; // Error, can't reassign the constant!
```

<<<<<<< HEAD
Kun ohjelmoija on varma, ettei muuttuja koskaan muutu, se voidaan esitellä `const` avainsanalla, jolloin varmistutaan arvon pysyvyydestä ja se saadaan kommunikoitua kaikille.

=======
When a programmer is sure that a variable will never change, they can declare it with `const` to guarantee and communicate that fact to everyone.
>>>>>>> 34a80e70f8cce5794be259d25f815d7a7db7cbe3

### Isokirjaimiset vakiomuuttujat

<<<<<<< HEAD
Laajalle levinnyt käytäntö on käyttää vakiomuuttujia korvaamaan vaikeasti muistettavia arvoja, jotka tunnetaan ennen koodin suorittamista.
=======
There is a widespread practice to use constants as aliases for difficult-to-remember values that are known before execution.
>>>>>>> 34a80e70f8cce5794be259d25f815d7a7db7cbe3

Tällaiset vakiot kirjoitetaan suurten kirjainten ja alaviivojen avulla.

Luodaan esimerkiksi vakioita väreille niin sanotussa "web" (heksadesimaali) muodossa:

```js run
const COLOR_RED = "#F00";
const COLOR_GREEN = "#0F0";
const COLOR_BLUE = "#00F";
const COLOR_ORANGE = "#FF7F00";

// ...kun meidän tarvitsee valita väri
let color = COLOR_ORANGE;
alert(color); // #FF7F00
```

Hyödyt:

- `COLOR_ORANGE` on paljon helpompi muistaa kuin `"#FF7F00"`.
- On paljon helpompi kirjoittaa väärin `"#FF7F00"` kuin `COLOR_ORANGE`.
- Kun koodia lukee, `COLOR_ORANGE` on paljon kuvaavampi kuin `#FF7F00`.

Milloin käytämme suuria kirjaimia ja milloin nimeämme vakiot normaalisti? Tehdään siitä selvää.

<<<<<<< HEAD
Termillä "vakio" tarkoitetaan vain sitä, että muuttujan arvo ei koskaan muutu. On kuitenkin vakioita, jotka tunnetaan ennen koodin suoritusta (kuten värin punainen heksadesimaaliarvo) ja vakioita, jotka *lasketaan* koodin suorituksen aikana, mutta ne eivät muutu ensimmäisen arvon sijoituksen jälkeen.

Esimerkiksi:
=======
Being a "constant" just means that a variable's value never changes. But some constants are known before execution (like a hexadecimal value for red) and some constants are *calculated* in run-time, during the execution, but do not change after their initial assignment.

For instance:

>>>>>>> 34a80e70f8cce5794be259d25f815d7a7db7cbe3
```js
const pageLoadTime = /* aika, joka kuluu nettisivun lataamiseen */;
```

<<<<<<< HEAD
Muuttujan `pageLoadTime` arvoa ei tunneta ennen sivun lataamista, joten se kirjoitetaan normaalisti. Se on silti vakio, koska sen arvo ei muutu sijoittamisen jälkeen.

Toisin sanoen, suuria kirjaimia käytetään vain vakiomuuttujissa, joilla on "kovakoodattu" arvo.  
=======
The value of `pageLoadTime` is not known before the page load, so it's named normally. But it's still a constant because it doesn't change after the assignment.

In other words, capital-named constants are only used as aliases for "hard-coded" values.
>>>>>>> 34a80e70f8cce5794be259d25f815d7a7db7cbe3

## Oikeaoppinen nimeäminen

Muuttujista puhuttaessa on vielä yksi erittäin tärkeä asia.

Nimellä pitäisi olla selkeä, itsestäänselvä tarkoitus, joka kuvaa sen varastoimaa dataa.

<<<<<<< HEAD
Muuttujien nimeäminen on yksi tärkeimmistä ja vaikeimmista taidoista ohjelmoinnissa. Nopea muuttujien nimien vilkaisu voi paljastaa, minkä koodin on kirjoittanut aloittelija ja minkä kokenut sovelluskehittäjä.

Oikeassa projektissa suurin osa ajasta käytetään olemassa olevan koodin muokkaamiseen ja jatkamiseen sen sijaan, että kirjoitettaisiin jotain täysin tyhjästä. Kun palaamme koodin ääreen tehtyämme jotain muuta vähän aikaa, on paljon helpompi löytää tietoa, joka on merkitty hyvin. Toisin sanoen, kun muuttujilla on hyvät nimet.
=======
Variable naming is one of the most important and complex skills in programming. A glance at variable names can reveal which code was written by a beginner versus an experienced developer.

In a real project, most of the time is spent modifying and extending an existing code base rather than writing something completely separate from scratch. When we return to some code after doing something else for a while, it's much easier to find information that is well-labelled. Or, in other words, when the variables have good names.
>>>>>>> 34a80e70f8cce5794be259d25f815d7a7db7cbe3

Käytäthän aikaa hyvän muuttujan nimen keksimiseen ennen kuin esittelet sen. Tämä maksaa itsensä takaisin komeasti.

Muutamia hyviä sääntöjä:

<<<<<<< HEAD
- Käytä nimiä, jotka ihminen ymmärtää kuten `userName` tai `shoppingCart`.
- Vältä lyhenteitä ja lyhyitä nimiä kuten `a`, `b`, `c`, jollet todella tiedä mitä olet tekemässä.
- Tee nimistä maksimaalisen kuvaavia ja tiiviitä. Esimerkkejä huonoista nimistä ovat `data` ja `value`. Tällaiset nimet eivät kerro mitään. Niiden käyttäminen on okei vain silloin, kun koodin konteksti tekee erityisen itsestäänselväksi, mistä datasta ja arvosta on kyse.
- Sovi ehdoista tiimisi kesken ja omassa mielessäsi. Jos sivuston nykyinen käyttäjä on "user", siihen liittyville muuttujille annetaan nimeksi `currentUser` tai `newUser` sen sijaan, että käytetään nimiä `currentVisitor` tai `newManInTown`.
=======
- Use human-readable names like `userName` or `shoppingCart`.
- Stay away from abbreviations or short names like `a`, `b`, and `c`, unless you know what you're doing.
- Make names maximally descriptive and concise. Examples of bad names are `data` and `value`. Such names say nothing. It's only okay to use them if the context of the code makes it exceptionally obvious which data or value the variable is referencing.
- Agree on terms within your team and in your mind. If a site visitor is called a "user" then we should name related variables `currentUser` or `newUser` instead of `currentVisitor` or `newManInTown`.
>>>>>>> 34a80e70f8cce5794be259d25f815d7a7db7cbe3

Kuulostaa yksinkertaiselle? Se todellakin on, mutta kuvaavien ja tiiviiden muuttujien nimien keksiminen käytännössä ei ole helppoa. Anna palaa.

```smart header="Uudelleenkäyttö vai uuden luominen?"
Viimeinen huomio. On paljon laiskoja ohjelmoijia, joilla on tapana käyttää uudelleen olemassa olevia muuttujien nimiä uusien luomisen sijaan.

Tämän tuloksena, heidän muuttujansa ovat kuin laatikoita, joihin ihmiset heittelevät erilaisia asioita ilman, että niiden nimitarroja muutetaan. Mitä laatikossa on nyt? Meidän on katsottava lähemmin ja tarkistettava.

Tällaiset ohjelmoijat säästävät hieman aikaa muuttujien esittelyssä, mutta menettävät kymmenenkertaisen määrän aikaa virheenetsinnässä ja -korjauksessa.

Uusi muuttuja on hyvä, ei paha asia.

Nykyaikaiset JavaScriptin minimoijat ja selaimet optimoivat koodia tarpeeksi hyvin, joten se ei aiheuta suorityskykyongelmia. Eri muuttujien käyttö eri arvoille voi jopa auttaa moottoria optimoimaan koodisi.
```

## Tiivistelmä

Voimme esitellä muuttujia varastoidaksemme dataa käyttämällä `var`, `let` tai `const` avainsanoja.

- `let` -- on nykyaikainen muuttujan esittely.
- `var` -- on vanhanaikainen muuttujan esittely. Tavallisesti emme käytä sitä ollenkaan, mutta käsittelemme sen pieniä eroja `let` avainsanaan kappaleessa <info:var> siltä varalta, että tarvitset sitä
- `const` -- on kuin `let`, mutta sen arvoa ei voida muuttaa.

Muuttujat pitää nimetä niin, että ymmärrämme helposti, mitä ne sisältävät.
