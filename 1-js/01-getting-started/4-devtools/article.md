# Kehityskonsoli

Koodi on altis virheille. Tulet todennäköisesti tekemään virheitä... Tai siis, mitä höpisen? Tulet *takuuvarmasti* tekemään virheitä ainakin, jos olet ihminen etkä [robotti](https://en.wikipedia.org/wiki/Bender_(Futurama)).

Selaimessa virheitä ei kuitenkaan oletuksena näe. Jos jokin skriptissä menee pieleen, emme näe mikä on rikki emmekä voi korjata sitä.

Nähdäksemme virheet ja paljon muuta hyödyllistä skripteihin liittyvää, selaimiin on upotettu "kehitystyökaluja".

Useimmat sovelluskehittäjät käyttävät Chromea tai Firefoxia, koska niissä on parhaat kehitystyökalut. Muissakin selaimissa on kehitystyökaluja, mutta ne seuraavat yleensä Chromen ja Firefoxin esimerkkiä. Useimmilla kehittäjillä onkin yksi "lempiselain" ja he käyttävät muita, jos ongelma on selainkohtainen.

Kehitystyökalut ovat tehokkaita; niissä on monia toimintoja. Aluksi opimme, miten työkalut saa näkyviin, katsomme virheitä ja ajamme JavaScript-komentoja.

## Google Chrome

Avaa tämä sivu: [bug.html](bug.html).

Sivun JavaScript-koodissa on virhe. Se on piilossa tavallisille vierailijoille, joten avataanpa kehitystyökalut, niin näemme sen.

Paina `key:F12` tai, jos käytät Macciä, paina `key:Cmd+Opt+J`.

Kehitystyökalut avautuvat oletuksena konsoliin (Console).

Sen pitäisi näyttää suurin piirtein tältä:

![chrome](chrome.png)

Työkalujen tarkka ulkoasu riippuu Chromen versiosta. Tarkka ulkoasu muuttuu silloin tällöin, mutta sen pitäisi näyttää samankaltaiselta.

- Täällä näemme punaisen virhetekstin. Tässä tapauksessa skripti sisältää tuntemattoman komennon "lalala".
- Oikealla on klikattava linkki lähteeseen `bug.html:12`, jossa näkyy sen rivin numero, jolta virhe löytyy.

Virhetekstin alla näkyy sininen `>` symboli. Se osoittaa "komentoriviä", johon voimme kirjoittaa JavaScript-komentoja. Paina `key:Enter` suorittaaksesi niitä.

Näemme nyt virheet, ja se riittää alkuun. Palaamme kehitystyökaluihin myöhemmin ja käsittelemme virheenkorjausta tarkemmin kappaleessa <info:debugging-chrome>.

```smart header="Monirivinen syöttö"
Kun syötämme rivin koodia konsoliin ja painamme `key:Enter`, koodi suoritetaan.

Voimme painaa `key:Shift+Enter` syöttääksemme useamman rivin. Näin voimme syöttää pidempiä JavaScript-koodipätkiä.
```

## Firefox, Edge ja muut

Suurimmassa osassa selaimista kehittäjätyökalut saa avattua painamalla `key:F12`.

Niiden ulkoasu ja tuntuma on melko samanlainen. Kun opit käyttämään yhden selaimen työkaluja (voit aloittaa Chromella), toiseen selaimeen vaihtaminen on helppoa.

## Safari

Safari (Macin selain, jota Windows/Linux eivät tue) on vähän erityinen. Meidän täytyy ensin ottaa "Develop menu" (suom. "kehitysvalikko") käyttöön.

Avaa "Preferences" (suom. "Asetukset") ja mene kohtaan "Advanced" (suom. "Lisäasetukset"). Alaosasta löytyy valinta:

![safari](safari.png)

Nyt näppäinyhdistelmällä `key:Cmd+Opt+C` saa avattua konsolin. Huomaa myös, että yläpalkkiin on ilmestynyt uusi valinta "Develop" (suom. "Kehitä"). Sieltä löytyy monia komentoja ja valintoja.

## Yhteenveto

- Kehitystyökalujen avulla voimme nähdä virheet, suorittaa komentoja, tutkia muuttujia ja paljon muuta.
- Työkalut saa suurimmassa osassa Windows-selaimista auki painamalla `key:F12`. Chrome Macillä vaatii näppäinyhdistelmää `key:Cmd+Opt+J`, Safari `key:Cmd+Opt+C` (kun työkalut on ensin otettu käyttöön).

Nyt meillä on kehitysympäristö valmiina. Seuraavassa osiossa paneudumme JavaScriptiin.
