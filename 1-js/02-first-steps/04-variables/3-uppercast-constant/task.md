importance: 4

---

# Isokirjaiminen const?

Tutki seuraavaa koodia:

```js
const birthday = '18.04.1982';

const age = someCode(birthday);
```

<<<<<<< HEAD
Meillä on vakiomuuttuja `birthday` päivämäärä ja `age` lasketaan muuttujan `birthday` avulla jonkin koodin avulla (sitä ei ole tässä näkyvillä, koska yksityiskohdilla ei ole tässä kohtaa merkitystä).
=======
Here we have a constant `birthday` for the date, and also the `age` constant.

The `age` is calculated from `birthday` using `someCode()`, which means a function call that we didn't explain yet (we will soon!), but the details don't matter here, the point is that `age` is calculated somehow based on the `birthday`.
>>>>>>> 9e3fa1351f80cfd6353a778a55b2c86bca9e895f

Käyttäisitkö isoja kirjaimia muuttujalle `birthday`? Entä `age`? Tai jopa molemmissa?

```js
<<<<<<< HEAD
const BIRTHDAY = '18.04.1982'; // käytä isoja kirjaimia?

const AGE = someCode(BIRTHDAY); // käytä isoja kirjaimia?
=======
const BIRTHDAY = '18.04.1982'; // make birthday uppercase?

const AGE = someCode(BIRTHDAY); // make age uppercase?
>>>>>>> 9e3fa1351f80cfd6353a778a55b2c86bca9e895f
```
