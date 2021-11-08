# Hei maailma!

Tämä osa tutoriaalista keskittyy JavaScriptin ytimeen eli kieleen itseensä.

Tarvitsemme kuitenkin ympäristön, jossa voimme suorittaa skriptimme ja, koska tämä kirja on netissä, selain on hyvä valinta. Pidämme selainkohtaisten komentojen (kuten `alert`) määrän minimissä, jottei sinun tarvitse käyttää niiden oppimiseen aikaan, jos suunnittelet keskittyväsi johonkin muuhun ympäristöön (kuten Node.js) Keskitymme selaimen JavaScriptiin tämän tutoriaalin [seuraavassa osassa](/ui).

Katsotaan ensin, miten saamme liitettyä skriptin nettisivuun. Palvelinpuolen ympäristöissä (kuten Node.js) voimme suorittaa skriptin esimerkiksi komennolla`"node my.js"`.


## "script" tunniste

JavaScript -ohjelmia voi sijoittaa lähes minne tahansa HTML-dokumenttiin käyttämällä `<script>` tunnistetta.

Esimerkiksi:

```html run height=100
<!DOCTYPE HTML>
<html>

<body>

  <p>Ennen skriptiä...</p>

*!*
  <script>
    alert( 'Hei maailma!' );
  </script>
*/!*

  <p>...Skriptin jälkeen.</p>

</body>

</html>
```

```online
Voit suorittaa esimerkin skriptin painamalla "Play" painiketta yllä olevan laatikon oikeassa yläkulmassa.
```

`<script>` tunniste sisältää JavaScript-koodin, joka suoritetaan automaattisesti, kun selain prosessoi tunnisteen.


## Moderni merkintätapa

`<script>` tunnisteeseen liittyy muutamia attribuutteja, joita käytetään nykyään harvoin. Niitä näkyy kuitenkin vanhassa koodissa:

`type` (suom. tyyppi) attribuutti: <code>&lt;script <u>type</u>=...&gt;</code>
: Vanha HTML standardi, HTML4, edellytti `type` attribuutin käyttöä. Useimmiten attribuutti sai arvon `type="text/javascript"`, mutta sen käyttöä ei enää edellytetä. Nykyinen HTML standardi on myös täysin muuttanut attribuutin tarkoituksen. Nyt sitä voidaan käyttää JavaScript-moduulien yhteydessä. Se on kuitenkin edistynyt aihe, josta puhumme myöhemmin tässä tutoriaalissa.

`language` (suom. kieli) attribuutti: <code>&lt;script <u>language</u>=...&gt;</code>
: Tätä attribuuttia oli tarkoitus käyttää skriptin kielen osoittamiseen. Attribuutti ei kuitenkaan käy enää järkeen, koska JavaScript on oletuskieli. Näin ollen sitä ei tarvitse käyttää.

Kommenttit ennen skriptejä ja niiden jälkeen.
: Ikivanhoissa kirjoissa tai oppaissa saattaa näkyä kommentteja `<script>` tunnisteen sisällä tähän tapaan:

    ```html no-beautify
    <script type="text/javascript"><!--
        ...
    //--></script>
    ```

    Tätä temppua ei enää käytetä. Sen tarkoituksena oli piilottaa JavaScript koodi vanhoilta selaimilta, jotka eivät ymmärtäneet miten `<script>` tunnisteita prosessoidaan. Koska tämä ongelma ei koske yhtäkään viimeisen 15 vuoden aikana julkaistua selainta, tällaisen kommentin perusteella voi tunnistaa erittäin vanhaa koodia.


## Ulkoiset skriptit

Jos kirjoitamme paljon JavaScript koodia, voimme kirjoittaa sen erilliseen tiedostoon.

Skriptitiedostot liitetään HTML:ään `src` (suom. lähde) attribuutilla:

```html
<script src="/polku/tiedostoon/script.js"></script>
```

<<<<<<< HEAD
Yllä, `/polku/tiedostoon/script.js` tarkoittaa absoluuttista tiedostopolkua skriptiin sivuston juuresta (root). Polun voi kirjoittaa myös nykyisen sivun suhteen. Esimerkiksi `src="script.js"` tarkoittaisi tiedostoa nimeltä `"script.js"` nykyisessä kansiossa.
=======
Here, `/path/to/script.js` is an absolute path to the script from the site root. One can also provide a relative path from the current page. For instance, `src="script.js"`, just like `src="./script.js"`, would mean a file `"script.js"` in the current folder.
>>>>>>> 4541b7af7584014a676da731f6e8774da5e059f6

Voimme kirjoittaa myös koko URL-osoitteen. Esimerkiksi:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/lodash.js/4.17.11/lodash.js"></script>
```

Voit käyttäää useampaa tunnistetta liittääksesi useamman skriptin:

```html
<script src="/js/script1.js"></script>
<script src="/js/script2.js"></script>
…
```

```smart
Perussääntönä voidaan pitää, että vain erittäin yksinkertaisia skriptejä kirjoitetaan HTML:ään. Muut skriptit kirjoitetaan erillisiin tiedostoihin.

Erillisen tiedoston hyötynä on, että selain lataa ja tallentaa sen [välimuistiin](https://fi.wikipedia.org/wiki/V%C3%A4limuisti).

Jatkossa kaikki sivut, joihin on liitetty sama skripti, voivat lukea sen suoraan välimuistista lataamisen sijaan ja tiedosto itseasiassa ladataan vain kerran.

Tämä vähentää liikennettä ja tekee sivuista nopeampia.
```

````warn header="Jos `src` on määritelty, tunnisteiden välistä koodia ei oteta huomioon."
Yksittäinen `<script>` tunniste ei voi samaan aikaan käyttää `src` attribuuttia ja koodia tunnisteiden välissä.

Tämä ei toimi:

```html
<script *!*src*/!*="file.js">
  alert(1); // sisältöä ei huomioida, koska src on määritelty
</script>
```

Aina on valittava ulkoinen `<script src="…">` tai tavallinen `<script>`, jonka sisällä on koodia.

Yllä oleva esimerkki saadaan toimimaan käyttämällä kahta tunnistetta:

```html
<script src="file.js"></script>
<script>
  alert(1);
</script>
```
````

## Yhteenveto

- Voimme käyttää `<script>` tunnistetta lisääksemme JavaScript koodia sivulle.
- `type` ja `language` attribuutteja ei tarvita.
- Erillisessä tiedostossa olevaan skriptiin voidaan viitata näin: `<script src="polku/tiedostoon/script.js"></script>`.


Skripteissä ja niiden vuorovaikutuksessa nettisivun kanssa riittää opittavaa. Pidetään kuitenkin mielessä, että tämä osa tutoriaalista on omistettu JavaScript ohjelmointikielelle, joten meidän ei pidä keskittyä selainkohtaisiin asioihin. Käytämme kuitenkin selainta JavaScriptin suorittamiseen, mikä on erittäin kätevää tässä yhteydessä, mutta silti vain yksi mahdollisista tavoista.
