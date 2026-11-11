importance: 4

---

# Isokirjaiminen const?

Tutki seuraavaa koodia:

```js
const birthday = '18.04.1982';

const age = someCode(birthday);
```

Tässä meillä on vakiomuuttuja `birthday` päivämäärälle sekä vakiomuuttuja `age`.

`age` lasketaan `birthday`-muuttujasta kutsulla `someCode()`. Se on funktiokutsu, jota emme ole vielä selittäneet (selitämme pian!), mutta yksityiskohdilla ei ole tässä merkitystä. Olennaista on, että `age` lasketaan jotenkin `birthday`-arvon perusteella.

Käyttäisitkö isoja kirjaimia muuttujalle `birthday`? Entä `age`? Tai jopa molemmissa?

```js
const BIRTHDAY = '18.04.1982'; // syntymäpäivä isoilla kirjaimilla?

const AGE = someCode(BIRTHDAY); // ikä isoilla kirjaimilla?
```
