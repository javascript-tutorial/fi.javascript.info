# Tietotyypit

JavaScriptissa arvo on aina jotain tiettyä tyyppiä, esimerkiksi merkkijono tai luku.

JavaScriptissa on kahdeksan perustietotyyppiä. Käymme ne tässä läpi yleisellä tasolla, ja seuraavissa kappaleissa käsittelemme jokaista niistä yksityiskohtaisesti.

Muuttujaan voi laittaa mitä tahansa tyyppiä olevan arvon. Muuttujassa voi esimerkiksi olla ensin merkkijono ja sen jälkeen luku:

```js
// ei virhettä
let message = "hello";
message = 123456;
```

Ohjelmointikieliä, jotka sallivat tällaisen, kuten JavaScript, kutsutaan "dynaamisesti tyypitetyiksi". Se tarkoittaa, että tietotyyppejä on olemassa, mutta muuttujat eivät ole sidottuja mihinkään niistä.

## Luku

```js
let n = 123;
n = 12.345;
```

Tyyppi *number* (luku) kattaa sekä kokonaisluvut että liukuluvut.

Luvuille on monia operaatioita, esimerkiksi kertolasku `*`, jakolasku `/`, yhteenlasku `+`, vähennyslasku `-` ja niin edelleen.

Tavallisten lukujen lisäksi on niin sanottuja "erityisiä numeerisia arvoja", jotka myös kuuluvat tähän tietotyyppiin: `Infinity`, `-Infinity` ja `NaN`.

- `Infinity` tarkoittaa matemaattista [ääretöntä](https://fi.wikipedia.org/wiki/Äärettömyys) ∞. Se on erityinen arvo, joka on suurempi kuin mikään luku.

    Saamme sen tuloksena, kun jaamme nollalla:

    ```js run
    alert( 1 / 0 ); // Infinity
    ```

    Tai voimme viitata siihen suoraan:

    ```js run
    alert( Infinity ); // Infinity
    ```
- `NaN` tarkoittaa laskuvirhettä. Se on virheellisen tai määrittelemättömän matemaattisen operaation tulos, esimerkiksi:

    ```js run
    alert( "not a number" / 2 ); // NaN, tällainen jakolasku on virheellinen
    ```

    `NaN` on "tarttuva". Mikä tahansa myöhempi matemaattinen operaatio `NaN`:lle palauttaa `NaN`:

    ```js run
    alert( NaN + 1 ); // NaN
    alert( 3 * NaN ); // NaN
    alert( "not a number" / 2 - 1 ); // NaN
    ```

    Jos siis matemaattisessa lausekkeessa on jossain `NaN`, se leviää koko tulokseen (tähän on vain yksi poikkeus: `NaN ** 0` on `1`).

```smart header="Matemaattiset operaatiot ovat turvallisia"
Laskeminen on JavaScriptissa "turvallista". Voimme tehdä mitä tahansa: jakaa nollalla, käsitellä muita kuin numeerisia merkkijonoja lukuina ja niin edelleen.

Skripti ei koskaan pysähdy kohtalokkaaseen virheeseen ("kuole"). Pahimmassa tapauksessa saamme tulokseksi `NaN`.
```

Erityiset numeeriset arvot kuuluvat muodollisesti "number"-tyyppiin. Tavallisessa merkityksessä ne eivät tietenkään ole lukuja.

Lukujen käsittelystä kerrotaan lisää kappaleessa <info:number>.

## BigInt [#bigint-type]

JavaScriptissa "number"-tyyppi ei pysty esittämään luotettavasti kokonaislukuja, jotka ovat suurempia kuin <code>(2<sup>53</sup>-1)</code> (eli `9007199254740991`) tai negatiivisina pienempiä kuin <code>-(2<sup>53</sup>-1)</code>.

Tarkalleen ottaen "number"-tyyppiin voi tallentaa suurempiakin kokonaislukuja (aina lukuun <code>1.7976931348623157 * 10<sup>308</sup></code> asti), mutta turvallisen kokonaislukualueen <code>±(2<sup>53</sup>-1)</code> ulkopuolella syntyy tarkkuusvirhe, koska kaikki numerot eivät mahdu kiinteään 64-bittiseen tallennustilaan. Tallennettu arvo voi siis olla "likimääräinen".

Esimerkiksi nämä kaksi lukua (heti turvallisen alueen yläpuolella) ovat samat:

```js
console.log(9007199254740991 + 1); // 9007199254740992
console.log(9007199254740991 + 2); // 9007199254740992
```

Voidaan siis sanoa, että parittomia kokonaislukuja, jotka ovat suurempia kuin <code>(2<sup>53</sup>-1)</code>, ei voi tallentaa "number"-tyyppiin lainkaan.

Useimpiin tarkoituksiin alue <code>±(2<sup>53</sup>-1)</code> riittää hyvin, mutta joskus tarvitsemme koko todella suurten kokonaislukujen alueen, esimerkiksi salauksessa tai mikrosekunnin tarkkuisissa aikaleimoissa.

Tyyppi `BigInt` lisättiin kieleen hiljattain esittämään mielivaltaisen pituisia kokonaislukuja.

`BigInt`-arvo luodaan lisäämällä kokonaisluvun loppuun `n`:

```js
// lopussa oleva "n" tarkoittaa, että kyseessä on BigInt
const bigInt = 1234567890123456789012345678901234567890n;
```

Koska `BigInt`-lukuja tarvitaan harvoin, emme käsittele niitä tässä, vaan niille on oma kappaleensa <info:bigint>. Lue se, kun tarvitset näin suuria lukuja.

## Merkkijono

JavaScriptissa merkkijonon täytyy olla lainausmerkkien sisällä.

```js
let str = "Hello";
let str2 = 'Single quotes are ok too';
let phrase = `can embed another ${str}`;
```

JavaScriptissa on kolmenlaisia lainausmerkkejä.

1. Kaksinkertaiset lainausmerkit: `"Hello"`.
2. Yksinkertaiset lainausmerkit: `'Hello'`.
3. Takahipsut (engl. backticks): <code>&#96;Hello&#96;</code>.

Kaksinkertaiset ja yksinkertaiset lainausmerkit ovat "tavallisia" lainausmerkkejä. JavaScriptissa niiden välillä ei käytännössä ole eroa.

Takahipsut ovat "laajennetun toiminnallisuuden" lainausmerkit. Niiden avulla merkkijonoon voi upottaa muuttujia ja lausekkeita kirjoittamalla ne merkintöjen `${…}` sisään, esimerkiksi:

```js run
let name = "John";

// upotetaan muuttuja
alert( `Hello, *!*${name}*/!*!` ); // Hello, John!

// upotetaan lauseke
alert( `the result is *!*${1 + 2}*/!*` ); // the result is 3
```

Merkintöjen `${…}` sisällä oleva lauseke arvioidaan, ja tuloksesta tulee osa merkkijonoa. Sinne voi laittaa mitä tahansa: muuttujan kuten `name`, laskutoimituksen kuten `1 + 2` tai jotain monimutkaisempaa.

Huomaa, että tämä onnistuu vain takahipsujen kanssa. Muissa lainausmerkeissä tällaista upotusta ei ole!
```js run
alert( "the result is ${1 + 2}" ); // the result is ${1 + 2} (kaksinkertaiset lainausmerkit eivät tee mitään)
```

Käsittelemme merkkijonoja perusteellisemmin kappaleessa <info:string>.

```smart header="*Merkki*-tyyppiä ei ole."
Joissakin kielissä on erityinen "merkki"-tyyppi yksittäiselle merkille. Esimerkiksi C-kielessä ja Javassa sen nimi on "char".

JavaScriptissa tällaista tyyppiä ei ole. On vain yksi tyyppi: `string`. Merkkijonossa voi olla nolla merkkiä (se on tyhjä), yksi merkki tai monta merkkiä.
```

## Boolean (totuusarvo)

Boolean-tyypillä on vain kaksi arvoa: `true` ja `false`.

Tätä tyyppiä käytetään yleensä kyllä/ei-arvojen tallentamiseen: `true` tarkoittaa "kyllä, pitää paikkansa" ja `false` tarkoittaa "ei, ei pidä paikkaansa".

Esimerkiksi:

```js
let nameFieldChecked = true; // kyllä, nimikenttä on valittu
let ageFieldChecked = false; // ei, ikäkenttää ei ole valittu
```

Totuusarvoja saadaan myös vertailujen tuloksena:

```js run
let isGreater = 4 > 1;

alert( isGreater ); // true (vertailun tulos on "kyllä")
```

Käsittelemme totuusarvoja syvällisemmin kappaleessa <info:logical-operators>.

## Arvo "null"

Erityinen arvo `null` ei kuulu mihinkään edellä kuvatuista tyypeistä.

Se muodostaa oman erillisen tyyppinsä, jonka ainoa arvo on `null`:

```js
let age = null;
```

JavaScriptissa `null` ei ole "viittaus olemattomaan olioon" tai "nollaosoitin" kuten joissakin muissa kielissä.

Se on vain erityinen arvo, joka tarkoittaa "ei mitään", "tyhjä" tai "arvo tuntematon".

Yllä oleva koodi kertoo, että `age` on tuntematon.

## Arvo "undefined"

Myös erityinen arvo `undefined` on erillään muista. Se muodostaa oman tyyppinsä, samoin kuin `null`.

`undefined` tarkoittaa "arvoa ei ole sijoitettu".

Jos muuttuja on esitelty, mutta siihen ei ole sijoitettu arvoa, sen arvo on `undefined`:

```js run
let age;

alert(age); // näyttää "undefined"
```

Teknisesti muuttujaan on mahdollista sijoittaa `undefined` myös itse:

```js run
let age = 100;

// muutetaan arvoksi undefined
age = undefined;

alert(age); // "undefined"
```

...Emme kuitenkaan suosittele sitä. Tavallisesti "tyhjä" tai "tuntematon" arvo sijoitetaan muuttujaan käyttämällä `null`-arvoa, kun taas `undefined` on varattu oletusalkuarvoksi asioille, joihin ei ole sijoitettu arvoa.

## Oliot ja symbolit

Tyyppi `object` (olio) on erityinen.

Kaikkia muita tyyppejä kutsutaan "primitiivisiksi", koska niiden arvot voivat sisältää vain yhden asian (oli se sitten merkkijono, luku tai mitä tahansa muuta). Olioihin sen sijaan tallennetaan tietokokoelmia ja monimutkaisempia kokonaisuuksia.

Koska oliot ovat niin tärkeitä, ne ansaitsevat erityiskohtelun. Käsittelemme niitä myöhemmin kappaleessa <info:object>, kun olemme oppineet lisää primitiiveistä.

Tyyppiä `symbol` (symboli) käytetään olioiden yksilöllisten tunnisteiden luomiseen. Mainitsemme sen tässä kokonaisuuden vuoksi, mutta yksityiskohdat jätetään siihen asti, kun tunnemme oliot.

## typeof-operaattori [#type-typeof]

Operaattori `typeof` palauttaa operandin tyypin. Siitä on hyötyä, kun haluamme käsitellä eri tyyppisiä arvoja eri tavoin tai haluamme vain tarkistaa tyypin nopeasti.

Kutsu `typeof x` palauttaa merkkijonon, jossa on tyypin nimi:

```js
typeof undefined // "undefined"

typeof 0 // "number"

typeof 10n // "bigint"

typeof true // "boolean"

typeof "foo" // "string"

typeof Symbol("id") // "symbol"

*!*
typeof Math // "object"  (1)
*/!*

*!*
typeof null // "object"  (2)
*/!*

*!*
typeof alert // "function"  (3)
*/!*
```

Kolme viimeistä riviä saattavat vaatia lisäselitystä:

1. `Math` on sisäänrakennettu olio, joka tarjoaa matemaattisia operaatioita. Tutustumme siihen kappaleessa <info:number>. Tässä se on vain esimerkki oliosta.
2. `typeof null` palauttaa `"object"`. Kyseessä on virallisesti tunnustettu virhe `typeof`-operaattorissa. Virhe on peräisin JavaScriptin aivan alkuajoilta, ja se on säilytetty yhteensopivuuden vuoksi. `null` ei todellakaan ole olio. Se on erityinen arvo, jolla on oma erillinen tyyppinsä. `typeof` toimii tässä väärin.
3. `typeof alert` palauttaa `"function"`, koska `alert` on funktio. Opiskelemme funktioita seuraavissa kappaleissa, joissa näemme myös, että JavaScriptissa ei ole erityistä "function"-tyyppiä. Funktiot kuuluvat olio-tyyppiin. `typeof` kuitenkin käsittelee niitä eri tavalla ja palauttaa `"function"`. Tämäkin on peräisin JavaScriptin alkuajoilta. Teknisesti tällainen toiminta ei ole oikein, mutta se voi olla käytännössä kätevää.

```smart header="Syntaksi `typeof(x)`"
Saatat törmätä myös toiseen syntaksiin: `typeof(x)`. Se on sama asia kuin `typeof x`.

Selvyyden vuoksi: `typeof` on operaattori, ei funktio. Sulkeet eivät tässä ole osa `typeof`-operaattoria. Ne ovat samanlaiset sulkeet, joita käytetään matematiikassa ryhmittelyyn.

Yleensä tällaisten sulkeiden sisällä on matemaattinen lauseke, kuten `(2 + 2)`, mutta tässä niiden sisällä on vain yksi argumentti `(x)`. Syntaktisesti sulkeiden avulla voi jättää välilyönnin pois `typeof`-operaattorin ja sen argumentin välistä, ja jotkut pitävät siitä.

Jotkut suosivat muotoa `typeof(x)`, vaikka muoto `typeof x` on paljon yleisempi.
```

## Yhteenveto

JavaScriptissa on 8 perustietotyyppiä.

- Seitsemän primitiivistä tietotyyppiä:
    - `number` kaikenlaisille luvuille: kokonaisluvuille ja liukuluvuille. Kokonaislukujen alue on rajattu <code>±(2<sup>53</sup>-1)</code>.
    - `bigint` mielivaltaisen pituisille kokonaisluvuille.
    - `string` merkkijonoille. Merkkijonossa voi olla nolla tai useampia merkkejä, eikä erillistä yksittäisen merkin tyyppiä ole.
    - `boolean` arvoille `true`/`false`.
    - `null` tuntemattomille arvoille -- erillinen tyyppi, jolla on yksi arvo `null`.
    - `undefined` arvoille, joita ei ole sijoitettu -- erillinen tyyppi, jolla on yksi arvo `undefined`.
    - `symbol` yksilöllisille tunnisteille.
- Ja yksi ei-primitiivinen tietotyyppi:
    - `object` monimutkaisemmille tietorakenteille.

`typeof`-operaattorilla voi nähdä, minkä tyyppinen arvo muuttujassa on.

- Sitä käytetään yleensä muodossa `typeof x`, mutta myös `typeof(x)` on mahdollinen.
- Se palauttaa merkkijonon, jossa on tyypin nimi, esimerkiksi `"string"`.
- `null`-arvolle se palauttaa `"object"` -- tämä on virhe kielessä, sillä kyseessä ei oikeasti ole olio.

Seuraavissa kappaleissa keskitymme primitiivisiin arvoihin, ja kun ne ovat tuttuja, siirrymme olioihin.
