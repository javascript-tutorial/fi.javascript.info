# Vuorovaikutus: alert, prompt, confirm

Koska käytämme selainta esimerkkiympäristönämme, katsotaan muutamaa funktiota, joilla voi olla vuorovaikutuksessa käyttäjän kanssa: `alert`, `prompt` ja `confirm`.

## alert

Tämä onkin jo tuttu. Se näyttää viestin ja odottaa, että käyttäjä painaa "OK".

Esimerkiksi:

```js run
alert("Hei");
```

Pientä ikkunaa, jossa viesti näkyy, kutsutaan *modaali-ikkunaksi*. Sana "modaali" tarkoittaa, että vierailija ei voi käyttää muuta sivua, painaa muita painikkeita jne., ennen kuin hän on käsitellyt ikkunan. Tässä tapauksessa siihen asti, kunnes hän painaa "OK".

## prompt

Funktio `prompt` ottaa kaksi argumenttia:

```js no-beautify
result = prompt(title, [default]);
```

Se näyttää modaali-ikkunan, jossa on tekstiviesti, syöttökenttä vierailijalle sekä painikkeet OK ja Peru (engl. Cancel).

`title`
: Teksti, joka näytetään vierailijalle.

`default`
: Valinnainen toinen parametri, syöttökentän alkuarvo.

```smart header="Hakasulkeet syntaksissa `[...]`"
Hakasulkeet parametrin `default` ympärillä yllä olevassa syntaksissa tarkoittavat, että parametri on valinnainen eikä pakollinen.
```

Vierailija voi kirjoittaa jotain syöttökenttään ja painaa OK. Silloin saamme tekstin muuttujaan `result`. Vierailija voi myös perua syötteen painamalla Peru tai näppäintä `key:Esc`, jolloin `result` saa arvon `null`.

Funktion `prompt` kutsu palauttaa syöttökentän tekstin tai `null`, jos syöte peruttiin.

Esimerkiksi:

```js run
let age = prompt('Kuinka vanha olet?', 100);

alert(`Olet ${age} vuotta vanha!`); // Olet 100 vuotta vanha!
```

````warn header="IE:ssä: anna aina `default`"
Toinen parametri on valinnainen, mutta jos emme anna sitä, Internet Explorer lisää kehotteeseen tekstin `"undefined"`.

Aja tämä koodi Internet Explorerissa nähdäksesi sen:

```js run
let test = prompt("Testi");
```

Jotta kehotteet näyttäisivät hyviltä myös IE:ssä, suosittelemme antamaan aina toisen argumentin:

```js run
let test = prompt("Testi", ''); // <-- IE:tä varten
```
````

## confirm

Syntaksi:

```js
result = confirm(question);
```

Funktio `confirm` näyttää modaali-ikkunan, jossa on kysymys `question` ja kaksi painiketta: OK ja Peru.

Tulos on `true`, jos painetaan OK, ja muuten `false`.

Esimerkiksi:

```js run
let isBoss = confirm("Oletko sinä pomo?");

alert( isBoss ); // true, jos painetaan OK
```

## Yhteenveto

Kävimme läpi kolme selainkohtaista funktiota, joilla voi olla vuorovaikutuksessa vierailijoiden kanssa:

`alert`
: näyttää viestin.

`prompt`
: näyttää viestin, joka pyytää käyttäjää syöttämään tekstiä. Se palauttaa tekstin, tai `null`, jos painetaan Peru tai `key:Esc`.

`confirm`
: näyttää viestin ja odottaa, että käyttäjä painaa "OK" tai "Peru". Se palauttaa `true`, jos painetaan OK, ja `false`, jos painetaan Peru tai `key:Esc`.

Kaikki nämä metodit avaavat modaali-ikkunan: ne keskeyttävät skriptin suorituksen eivätkä anna vierailijan käyttää muuta sivua ennen kuin ikkuna on suljettu.

Kaikilla yllä olevilla metodeilla on kaksi yhteistä rajoitusta:

1. Selain päättää modaali-ikkunan tarkan sijainnin. Yleensä se on keskellä.
2. Myös ikkunan tarkka ulkoasu riippuu selaimesta. Emme voi muuttaa sitä.

Se on yksinkertaisuuden hinta. On muitakin tapoja näyttää hienompia ikkunoita ja monipuolisempaa vuorovaikutusta vierailijan kanssa, mutta jos kaikenlaisilla kilkkeillä ei ole paljon väliä, nämä metodit toimivat aivan hyvin.
