importance: 4

---

# Isokirjaiminen const?

Tutki seuraavaa koodia:

```js
const birthday = '18.04.1982';

const age = someCode(birthday);
```

Meillä on vakiomuuttuja `birthday` päivämäärä ja `age` lasketaan muuttujan `birthday` avulla jonkin koodin avulla (sitä ei ole tässä näkyvillä, koska yksityiskohdilla ei ole tässä kohtaa merkitystä).

Käyttäisitkö isoja kirjaimia muuttujalle `birthday`? Entä `age`? Tai jopa molemmissa?

```js
const BIRTHDAY = '18.04.1982'; // käytä isoja kirjaimia?

const AGE = someCode(BIRTHDAY); // käytä isoja kirjaimia?
```

