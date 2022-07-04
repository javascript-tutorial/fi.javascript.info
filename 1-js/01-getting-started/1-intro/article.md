# Johdanto JavaScriptiin

Katsotaan, mikä JavaScriptissä on niin erityistä, mitä voimme saada sen avulla aikaan ja mitkä muut teknologiat toimivat hyvin sen kanssa.

## Mikä JavaScript on?

*JavaScript* luotiin alunperin "tekemään nettisivuista eläviä".

Tällä kielellä kirjoitettuja ohjelmia kutsutaan *skripteiksi*. Ne voidaan kirjoittaa suoraan nettisivun HTML:ään ja ne suoritetaan automaattisesti, kun sivu latautuu.

Skriptit välitetään ja suoritetaan tavallisena tekstinä. Niiden suorittamiseen ei tarvita erityistä valmistelua tai kääntämistä.

Tässä suhteessa JavaScript poikkeaa selkeästi toisesta kielestä nimeltä [Java](https://fi.wikipedia.org/wiki/Java).

```smart header="Miksi sen nimi on <u>Java</u>Script?"
Kun JavaScript luotiin, sillä oli toinen nimi: "LiveScript". Java oli kuitenkin siihen aikaan erittäin suosittu kieli, joten päätettiin, että uuden kielen sijoittamisesta Javan "nuoremmaksi veljeksi" olisi apua.

Kehittyessään JavaScriptistä tuli kuitenkin täysin itsenäinen, jolla on oma määrittelynsä nimeltä [ECMAScript](http://en.wikipedia.org/wiki/ECMAScript), eikä sillä enää ole yhteyttä Javaan.
```

Nykyisin JavaScriptiä voidaan suorittaa selaimen lisäksi palvelimella tai oikeastaan millä tahansa laitteella, jossa on erityinen ohjelma nimeltä [JavaScript-moottori](https://en.wikipedia.org/wiki/JavaScript_engine).

Selaimeen on upotettu moottori, jota kutsutaan joskus "JavaScript-virtuaalikoneeksi".

Eri moottoreilla on omia kutsumanimiä. Esimerkiksi:

- [V8](https://fi.wikipedia.org/wiki/V8_(JavaScript-moottori)) -- Chromessa, Operassa ja Edgessä.
- [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey) -- Firefoxissa.
- ...Lisäksi on muitakin kutsumanimiä kuten "Chakra" IE:lle, "JavaScriptCore", "Nitro" ja "SquirrelFish" Safarille, jne.

Yllä luetellut termit on hyvä muistaa, koska niitä käytetään internetin sovelluskehitykseen liittyvissä artikkeleissa. Me tulemme myös käyttämään niitä. Jos esimerkiksi "V8 tukee toimintoa X", se todennäköisesti toimii Chromessa, Operassa ja Edgessä.

```smart header="Miten moottorit toimivat?"

Moottorit ovat monimutkaisia, mutta perusteet ovat helpot.

1. Moottori (upotettu, jos kyseessä on selain) lukee ("jäsentää") skriptin.
2. Sitten se muuttaa ("kääntää") skriptin konekielelle.
3. Ja sitten konekieli suoritetaan, melko nopeasti.

Moottori käyttää optimointeja prosessin jokaisessa vaiheessa. Se jopa katsoo käännettyä skriptiä sen suorituksen aikana, analysoi sen läpi kulkevaa dataa ja edelleen optimoi sen perusteella konekieltä lisää.
```

## Mitä JavaScript voi tehdä selaimessa?

Nykyaikainen JavaScript on "turvallinen" ohjelmointikieli. Se ei salli matalan tason pääsyä muistiin tai suorittimeen, koska se alunperin suunniteltiin selaimiin, jotka eivät vaadi sitä.

JavaScriptin kyvyt riippuvat suuresti ympäristöstä, jossa sitä ajetaan. Esimerkiksi [Node.js](https://wikipedia.org/wiki/Node.js) tukee funktioita, joiden avulla JavaScript voi lukea/kirjoittaa mielivaltaisia tiedostoja, suorittaa verkkopyyntöjä, jne.

Selaimessa JavaScript voi tehdä kaikkea nettisivun manipuloinnista vuorovaikutukseen käyttäjän ja web-palvelimen kanssa.

Selaimessa JavaScript voi esimerkiksi:

- Lisätä uutta HTML:ää sivulle, muuttaa olemassaolevaa sisältöä tai muokata tyylejä.
- Reagoida käyttäjän toimintaan, hiiren klikkauksiin, kursorin liikkeisiin ja painikkeiden painalluksiin.
- Lähettää pyyntöjä verkon yli etäpalvelimille, ladata tai lähettää tiedostoja (niin sanotut [AJAX](https://fi.wikipedia.org/wiki/Ajax_(ohjelmointi)) ja [COMET](https://en.wikipedia.org/wiki/Comet_(programming)) teknologiat).
- Lukea ja asettaa evästeitä, kysyä kysymyksiä vierailijalta, näyttää viestejä.
- Muistaa tietoja asiakaspuolella ("local storage", suom. "paikallinen varasto").

## Mitä JavaScript EI VOI tehdä selaimessa?

JavaScriptin kykyjä selaimessa on rajoitettu käyttäjän turvallisuuden vuoksi. Tavoitteena on estää pahaa nettisivua pääsemästä käsiksi yksityisiin tietoihin tai vahingoittamasta käyttäjän tietoja.

Esimerkkejä tällaisista rajoituksista ovat:

- Nettisivun JavaScript ei voi lukea, kirjoittaa tai kopioida mielivaltaisia tiedostoja kovalevyllä tai suorittaa ohjelmia. Sillä ei ole suoraa pääsyä käyttöjärjestelmän funktioihin.

    Modernit selaimet voivat sallia sen olla tekemisissä tiedostojen kanssa, mutta pääsy on rajoitettu ja sallittu vain, jos käyttäjä toimii tietyllä tavalla, kuten "pudottaa" tiedoston selaimeen tai valitsee sen `<input>` tunnisteen kautta.

    Kameran tai mikrofonin ja muiden laitteiden kanssa voi olla vuorovaikutuksessa, mutta ne edellyttävät käyttäjän nimenomaista lupaa. Eli sivusto, jossa JavaScript on käytössä, ei voi salaa käyttää webkameraa, tarkkailla ympäristöä ja lähettää tietoja [SUPO](https://fi.wikipedia.org/wiki/Suojelupoliisi):lle.
- Välilehdet tai ikkunat eivät lähtökohtaisesti tiedä toisistaan. Joskus ne tietävät, esimerkiksi yhden ikkunan käyttäessä JavaScriptiä toisen ikkunan avaamiseen, mutta tässäkään tapauksessa yhden sivun JavaScript ei pääse käsiksi toiseen sivuun, jos ne ovat peräisin eri sivustoilta (eri verkkotunnus, protokolla tai portti).

    Tätä kutsutaan nimellä "Same Origin Policy" ("saman alkuperän käytäntö"). Tämän kiertämiseksi *molempien sivujen* on sovittava tietojenvaihdosta ja niiden pitää sisältää erityistä JavaScript-koodia, joka käsittelee sitä. Käsittelemme tätä tässä tutoriaalissa.

    Tämäkin rajoitus on tehty käyttäjän turvaksi. Käyttäjän avaama sivu osoitteessa `http://jokusivu.fi` ei saa päästä käsiksi tai varastaa tietoa toiselle välilehdelle avatulta sivulta, jonka osoite on `http://gmail.com`.
- JavaScript voi helposti kommunikoida verkon yli sen palvelimen kanssa, jolta nykyinen sivu on peräisin, mutta sen kyky vastaanottaa tietoja toisilta sivustoilta tai verkkotunnuksilta on hankalaa. Vaikka se onkin mahdollista, se vaatii nimenomaista suostumusta (HTTP-otsikkojen muodossa) toiselta osapuolelta. Tämä on jälleen yksi turvarajoitus.

![](limitations.svg)

Samat rajoitukset eivät koske JavaScriptiä selaimen ulkopuolella, esimerkiksi palvelimella. Nykyaikaisiin selaimiin on myös saatavilla lisäosia tai laajennuksia, joilla on laajemmat käyttöoikeudet.

## Mikä tekee JavaScriptistä uniikin?

JavaScriptissä on ainakin *kolme* hienoa puolta:

```compare
+ Sillä on täysi integraatio HTML:n ja CSS:n kanssa.
+ Siinä tehdään yksinkertaiset asiat yksinkertaisella tavalla.
+ Sillä on kaikkien tärkeiden selainten tuki, ja se on oletuksena käytössä.
```
JavaScript on ainoa selainten teknologia, johon kaikki kolme kohtaa pätevät.

Tämä tekee JavaScriptistä uniikin. Tämän takia se on laajimmalle levinnyt selainten käyttöliittymien luontityökalu.

Tämän ohella JavaScriptillä voidaan tehdä myös palvelimia, mobiilisovelluksia, jne.

## JavaScriptin päälle luotuja kieliä

JavaScriptin syntaksi ei sovi kaikkien tarpeisiin. Eri ihmiset haluavat eri toimintoja.

Tämä on oletettavaa, koska kaikki projektit ja niiden vaatimukset ovat erilaisia.

Näin ollen viime aikoina on ilmestynyt monia kieliä, jotka muunnetaan JavaScriptiksi ennen niiden suorittamista selaimessa.

Nykyaikaisten työkalujen avulla muuntaminen on todella nopeaa ja läpinäkyvää ja niiden avulla sovelluskehittäjät voivat kirjoittaa koodia toisella kielellä, joka muunnetaan "kulissien takana" automaattisesti.

Esimerkkejä tällaisista kielistä:

<<<<<<< HEAD
- [CoffeeScript](http://coffeescript.org/) on niin sanottua syntaksisokeria JavaScriptille. Se mahdollistaa lyhyemmän syntaksin, jonka avulla voidaan kirjoittaa selkeämpää ja tarkempaa koodia. Ruby-devaajat yleensä pitävät siitä.
- [TypeScript](http://www.typescriptlang.org/) keskittyy "vahvaan tyypitykseen" yksinkertaistaakseen sovelluskehitystä ja tukeakseen monimutkaisia systeemejä. Sen on kehittänyt Microsoft.
- [Flow](http://flow.org/) tuo mukanaan vahvan tyypityksen, mutta eri tavalla. Sen on kehittänyt Facebook.
- [Dart](https://www.dartlang.org/) on oma kielensä, jolla on oma moottori, joka suorittaa koodia selaimen ulkopuolella (esimerkiksi mobiilisovelluksissa), mutta sekin on muunnettavissa JavaScriptiksi. Sen on kehittänyt Google.
- [Brython](https://brython.info/) muuntaa Pythonia JavaScriptiksi ja sallii sovellusten kirjoittamisen puhtaasti Pythonilla ilman JavaScriptiä.
- [Kotlin](https://kotlinlang.org/docs/reference/js-overview.html) on moderni, tiivis ja turvallinen ohjelmointikieli, joka toimii selaimessa tai Nodessa.
=======
- [CoffeeScript](https://coffeescript.org/) is a "syntactic sugar" for JavaScript. It introduces shorter syntax, allowing us to write clearer and more precise code. Usually, Ruby devs like it.
- [TypeScript](https://www.typescriptlang.org/) is concentrated on adding "strict data typing" to simplify the development and support of complex systems. It is developed by Microsoft.
- [Flow](https://flow.org/) also adds data typing, but in a different way. Developed by Facebook.
- [Dart](https://www.dartlang.org/) is a standalone language that has its own engine that runs in non-browser environments (like mobile apps), but also can be transpiled to JavaScript. Developed by Google.
- [Brython](https://brython.info/) is a Python transpiler to JavaScript that enables the writing of applications in pure Python without JavaScript.
- [Kotlin](https://kotlinlang.org/docs/reference/js-overview.html) is a modern, concise and safe programming language that can target the browser or Node.
>>>>>>> fe1c4a241f12a0939d1e0977cec6504ccd67201f

Lisääkin esimerkkejä löytyy. Silti, vaikka käytämme jotain muunnettavaa kieltä, meidän on tunnettava JavaScriptiä ymmärtääksemme, mitä todella olemme tekemässä.

## Yhteenveto

- JavaScript suunniteltiin alunperin vain selaimessa käytettäväksi kieleksi, mutta sitä käytetään nykyisin myös monissa muissa ympäristöissä.
- JavaScriptillä on nykyisin uniikki asema laajimmin käytettynä selainkielenä, joka integroituu täysin HTML:ään ja CSS:ään.
- Monet JavaScriptiksi "muunnettavat" kielet tuovat mukanaan tiettyjä toimintoja. On suositeltavaa tutustua niihin, ainakin lyhyesti, kun JavaScript on hallussa.
