# Moderni tila, "use strict"

JavaScript kehittyi pitkään ilman yhteensopivuusongelmia. Uusia toimintoja lisättiin samalla kun vanhat pysyivät ennallaan.

Tämän etuna oli, että vanha koodi ei koskaan lakannut toimimasta. Haittapuolena oli kuitenkin se, että jokainen JavaScriptin kehittäjien virhe tai epätäydellinen päätös jäi kieleen pysyvästi.

Tämä muuttui vuonna 2009, kun ECMAScript 5 (ES5) ilmestyi. Se lisäsi kieleen toimintoja ja samalla muutti joitain olemassa olevista toiminnoista. Vanhan koodin toimimisen varmistamiseksi, muokkaukset ovat oletuksena poissa käytöstä. Ne on erikseen otettava käyttöön `"use strict"` (suom. "käytä täsmällistä") direktiivillä.

## "use strict"

Direktiivi näyttää merkkijonolta: `"use strict"` tai `'use strict'`. Kun se sijoitetaan skriptin alkuun, koko skripti toimii "modernilla" tavalla.

Esimerkiksi:

```js
"use strict";

// tämä koodi toimii modernilla tavalla
...
```

Tulemme pian oppimaan funktioista (tapa ryhmitellä komentoja), joten mainitaan jo etukäteen, että `"use strict"` toimii myös funktioiden alussa. Tällöin strict-tila on käytössä vain kyseisessä funktiossa. Useimmiten direktiiviä käytetään kuitenkin koko skriptille.

````warn header="Varmista, että \"use strict\" on heti alussa"
Pidä huolta, että `"use strict"` on sijoitettu heti skriptin alkuun. Muussa tapauksessa strict-tilaa ei välttämättä oteta käyttöön.

Strict-tila on käytössä tässä:

```js no-strict
alert("jotain koodia");
// "use strict" alla jätetään huomioimatta, sen on oltava heti alussa

"use strict";

// strict-tila ei ole käytössä
```

Vain kommentteja voi sijoittaa `"use strict"` direktiivin yläpuolelle.
````

```warn header="Strict-tilaa ei voi peruuttaa"
Ei ole olemassa direktiiviä kuten `"no use strict"` (suom. "ei-käytä täsmällistä"), joka palauttaisi moottorin vanhaan tapaan.

Kun otamme strict-tilan käyttöön, emme voi perua sitä.
```

## Selaimen konsoli

Muista, että strict-tila ei ole oletuksena käytössä, kun käytät [kehityskonsolia](info:devtools).

Joissain tilanteissa, joihin `use strict` vaikuttaa, voit saada vääränlaisia tuloksia.

No, miten strict-tilaa käytetään konsolissa?

Voit kokeilla ensin painaa `key:Shift+Enter` kirjoittaaksesi usealle riville ja kirjoittaa alkuun `use strict`, tähän tapaan:

```js
'use strict'; <rivinvaihto painamalla Shift+Enter>
//  ...sinun koodisi
<koodin suoritus painamalla Enter>
```

Tämä toimii useimmissa selaimissa, ainakin Firefoxissa and Chromessa.

Jos tämä ei toimi, esimerkiksi vanhassa selaimessa, voit käyttää rumaa, mutta varmaa tapaa. Sijoita `use strict` tällä tapaa:

```js
(function() {
  'use strict';

  // ...sinun koodisi tähän...
})()
```

## Pitääkö strict-tilaa käyttää?

Tämä saattaa vaikuttaa itsestäänselvältä, mutta se ei ole.

Joku voi suositella, että skriptien alkuun lisätään `"use strict"`... Mutta tiedätkö mikä on siistiä?

Moderni JavaScript tukee olioita (class) ja moduuleja (module) - kielen edistyneitä rakenteita (tutustumme niihin tietysti myöhemmin), jotka automaattiseti ottavat käyttöön strict-tilan. Meidän ei siis tarvitse käyttää `"use strict"` direktiivitä, jos käytämme niitä.

**Eli toistaiseksi `"use strict";` on tervetullut vieras skriptiesi alussa. Myöhemmin, kun koodisi on olioissa ja moduuleissa, voit jättää sen pois.**

Olemme nyt tutustuneet strict-tilaan yleisesti.

Myöhemminssä kappaleissa, kun opimme lisää JavaScriptista, näemme strict-tilan ja vanhan tilan eroavaisuuksia paremmin. Onneksi niitä ei ole kovin paljon ja ne itseasiassa tekevät elämästämme helpompaa.

Kaikki tämän tutoriaalin esimerkit olettavat strict-tilan olevan käytössä ellei (todella harvinaisissa tapauksissa) muuta ole mainittu.
