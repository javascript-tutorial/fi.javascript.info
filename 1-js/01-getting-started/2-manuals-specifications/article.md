
# Oppaat ja määrittelyt

Tämä kirja on *tutoriaali*. Sen tavoitteena on auttaa sinua oppimaan kielen asteittain. Kun tunnet perusteet, tarvitset kuitenkin muita lähteitä. 

## Määrittely

[ECMA-262 määrittely](https://www.ecma-international.org/publications/standards/Ecma-262.htm) sisältää kaikkein tarkinta, yksityiskohtaisinta ja virallisinta tietoa JavaScriptistä. Se määrittelee kielen.

Koska tieto on niin virallista, se on aluksi vaikeaa ymmärtää. Jos siis tarvitset kaikkein luotettavinta tietoa kielen yksityiskohdista, määrittely on sille oikea paikka. Se ei kuitenkaan ole jokapäiväiseen käyttöön.

Uusi määrittely julkaistaan joka vuosi. Julkaisujen välillä uusimman määrittelyn luonnos löytyy osoitteesta <https://tc39.es/ecma262/>.

Lukeaksesi kaikkein uusimmista toiminnoista, mukaan lukien niistä, jotka ovat "melkein standardisoitu" (niin sanottu "taso 3"), katso "proposals" (suom. ehdotukset) osoitteessa <https://github.com/tc39/proposals>.

Jos kehität selainsovelluksia, tämän tutoriaalin [toisessa osassa](info:browser-environment) on mainittu muitakin määrittelyjä.

## Oppaat

- **MDN (Mozilla) JavaScript Reference** on tärkein opas, joka sisältää esimerkkejä ja muuta tietoa. Se on hyvä tarkemman tiedon lähde yksittäisille funktioille, metodeille, jne.

    Opas löytyy osoitteesta <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference>.

Toisaalta usein on parasta käyttää internethakuja. Käytä vain muotoa "MDN [termi]" hakusanassa, esim. <https://google.fi/search?q=MDN+parseInt> etsiessäsi tietoa `parseInt` funktiosta.

## Yhteensopivuustaulukot

JavaScript on kehittyvä kieli ja uusia toimintoja lisätään säännöllisesti.

Nähdäksesi niiden yhteensopivuuden eri selainpohjaisissa ja muissa moottoreissa, katso:

<<<<<<< HEAD
- <http://caniuse.com> - toimintokohtaiset yhteensopivuustaulukot, esim. nähdäksesi, mitkä moottorit ovat yhteensopivia nykyaikaisten salausfunktioiden kanssa: <http://caniuse.com/#feat=cryptography>.
- <https://kangax.github.io/compat-table> - kielen toimintoja ja niiden kanssa yhteensopivia moottoreita sisältävä taulukko
=======
- <https://caniuse.com> - per-feature tables of support, e.g. to see which engines support modern cryptography functions: <http://caniuse.com/#feat=cryptography>.
- <https://kangax.github.io/compat-table> - a table with language features and engines that support those or don't support.
>>>>>>> fe1c4a241f12a0939d1e0977cec6504ccd67201f

Kaikki nämä tietolähteet ovat hyödyllisiä todellisen elämän sovelluskehityksessä, koska ne sisältävät arvokasta tietoa kielen yksityiskohdista, niiden yhteensopivuudesta, jne.

Ne (tai tämä sivu) kannattaa muistaa, kun tarvitset tarkempaa tietoa tietystä toiminnosta.
