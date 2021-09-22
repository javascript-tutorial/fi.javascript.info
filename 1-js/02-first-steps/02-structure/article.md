# Koodin rakenne

Ensimmäisenä opiskelemme koodin rakennuspalikoita.

## Lausekkeet

Lausunnot ovat syntaksirakenteita ja -komentoja, jotka suorittavat toimintoja.

Olemme jo nähneet yhden lausekkeen: `alert('Hei maailma!')`, joka näyttää viestin "Hei maailma!".

Koodissa voi olla niin monta lauseketta kuin haluamme. Lausekkeet voi erottaa toisistaan puolipisteellä.

Esimerkiksi tässä jaamme "Hei maailma" lausekkeen kahteen lausekkeeseen:

```js run no-beautify
alert('Hei'); alert('maailma');
```

Tavallisesti lausekkeet kirjoitetaan eri riveille, jotta koodia on helpompi lukea:

```js run no-beautify
alert('Hei');
alert('maailma');
```

## Puolipisteet [#semicolon]

Puolipisteet voidaan useimmiten jättää kirjoittamatta, jos käytämme rivinvaihtoa.

Tämä toimisi myös:

```js run no-beautify
alert('Hei')
alert('maailma')
```

Tässä JavaScript tulkitsee rivinvaihdon "implisiittisenä" puolipisteenä. Tätä kutsutaan [puolipisteen automaattiseksi sijoitukseksi](https://tc39.github.io/ecma262/#sec-automatic-semicolon-insertion).

**Puolipisteen voi useimmiten korvata rivinvaihdolla, mutta "useimmiten" ei ole sama asia kuin "aina"!**

On myös tapauksia, joissa rivinvaihtoa ei tulkita puolipisteeksi. Esimerkiksi:

```js run no-beautify
alert(3 +
1
+ 2);
```

Koodin tulos on `6`, koska JavaScript ei tässä tapauksessa sijoita puolipisteitä. Intuitiivisesti on selvää, että merkkiin `"+"` päättyvä rivi on "epätäydellinen lauseke", joten olisi väärin käyttää tässä puolipistettä ja tässä tapauksessa homma toimii oletetulla tavalla.

**On kuitenkin olemassa tilanteita, joissa JavaScript ei osaa olettaa puolipistettä, vaikka sitä oikeasti tarvittaisiin.**

Tällaisista tilanteista johtuvia virheitä on vaikea löytää ja korjata.

````smart header="Esimerkki virheestä"
Jos olet utelias näkemään konkreettisen esimerkin tällaisesta virheestä, katso alla olevaa koodia:

```js run
alert("Hello");

[1, 2].forEach(alert);
```

Sinun ei tarvitse vielä miettiä, mitä hakasulkeet `[]` ja `forEach` tarkoittaa. Opiskelemme niitä myöhemmin. Nyt voit vain muistaa, että koodi näyttää ensin `Hello`, sitten `1` ja sitten `2`.

Jätetäänpä sitten puolipiste pois `alert` komennon jälkeen:

```js run no-beautify
alert("Hello")

[1, 2].forEach(alert);
```

Tämän ja ylempänä olevan koodin välillä on vain yhden merkin ero: ensimmäisen rivin perästä puuttuu puolipiste.

Jos suoritamme tämän koodin, vain ensimmäine `Hello` näkyy (minkä jälkeen on virhe, saatat joutua avaamaan konsolin nähdäksesi sen). Enää ei näy numeroita.

Tämä johtuu siitä, että JavaScript ei osaa olettaa puolipistettä ennen hakasulkeita `[...]`. Tällöin edellisen esimerkin koodia käsitellään yhtenä lausekkeena.

Näin moottori näkee koodin:

```js run no-beautify
alert("Hello")[1, 2].forEach(alert)
```

Eikö näytäkkin kummalliselta? Tällainen yhdistyminen on yksinkertaisesti väärin. Meidän on sijoitettava puolipiste `alert` komennon perään, jotta koodi toimisi oikein.

Näin voi tapahtua muissakin tilanteissa.
````

Suosittelemme käyttämään puolipisteitä lausekkeiden välissä, vaikka ne olisivatkin erotettu toisistaan rivinvaihdolla. Yhteisö soveltaa tätä sääntöä laajalti. Mainitaan vielä kerran, että puolipisteet -- *on mahdollista* -- jättää pois useimmissa tapauksissa. On kuitenkin turvallisempaa -- varsinkin aloittelijalle -- käyttää niitä.

## Kommentit [#code-comments]

Ajan kuluessa ohjelmista tulee kokoajan monimutkaisempia. Jossain vaiheessa tulee tarpeelliseksi lisätä *kommentteja*, jotka selittävät, miten ja miksi koodi toimii.

Kommentteja voi sijoittaa mihin tahansa kohtaan skriptissä. Ne eivät vaikuta koodin suoritukseen, koska moottori yksinkertaisesti jättää ne huomioimatta.

**Yhden rivin kommentit alkavat kahdella vinoviivalla `//`.**

Loput rivistä luetaan kommentiksi. Kommentti voi olla kokonaan oma rivinsä tai se voidaan sijoittaa lausekkeen perään.

Kuten tässä:
```js run
// Tämä koko rivi on pelkkää kommenttia
alert('Hei');

alert('maailma'); // Tämä kommentti on sijoitettu lausekkeen perään
```

**Monen rivin pituiset kommentit aloitetaan vinoviivalla ja asteriskilla <code>/&#42;</code> ja päättyvät asteriskilla ja vinoviivalla <code>&#42;/</code>.**

Kuten tässä:

```js run
/* Esimerkki, jossa on kaksi riviä.
Tämä on monirivinen kommentti.
*/
alert('Hei');
alert('maailma');
```

Kommenttien sisältö jätetään huomioimatta, joten niiden sisälle kirjoitettua koodia <code>/&#42; ... &#42;/</code> ei suoriteta.

Tämä voi joskus olla kätevää, jos haluamme väliaikaisesti ottaa koodinpätkän pois käytöstä:

```js run
/* Pois kommentoitua koodia
alert('Hei');
*/
alert('maailma');
```

```smart header="Käytä pikanäppäimiä!"
Useimmissa editoreissa koodirivin voi kommentoida pois käytöstä painamalla `key:Ctrl+/` pikanäppäimiä yhden rivin kommenteille ja esimerkiksi `key:Ctrl+Shift+/` monirivisille kommenteille (valitse koodinpätkä ja paina pikanäppäimiä). Jos käytät Macciä, kokeile käyttää `key:Cmd` näppäintä `key:Ctrl` näppäimen sijaan ja `key:Option` näppäintä `key:Shift` näppäimen sijaan.
```

````warn header="Sisäkkäisiä kommentteja ei tueta!"
Kommentin `/*...*/` sisällä ei voi olla toista kommenttia `/*...*/`.

Tällainen koodi kaatuu virheeseen:

```js run no-beautify
/*
  /* sisäkkäinen kommentti ?!? */
*/
alert( 'maailma' );
```
````

Älä epäröi kommentoida koodiasi.

Kommentit kasvattavat koodin jalanjälkeä, mutta se ei ole mikään ongelma. On olemassa monia työkaluja, jotka lyhentävät koodia ennen julkaisemista tuotantopalvelimelle. Ne poistavat kommentit, jotta ne eivät näy lopullisissa skripteissä. Kommenteilla ei siis ole mitään kielteistä vaikutusta lopulliseen koodiin.

Myöhemmin tässä tutoriaalissa on kappale nimeltä <info:code-quality>, jossa käydään läpi myös hyvien kommenttien kirjoittamista.
