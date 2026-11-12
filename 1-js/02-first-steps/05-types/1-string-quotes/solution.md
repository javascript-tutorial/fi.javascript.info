
Takahipsut upottavat merkkijonoon merkintöjen `${...}` sisällä olevan lausekkeen.

```js run
let name = "Ilya";

// lauseke on luku 1
alert( `hei ${1}` ); // hei 1

// lauseke on merkkijono "name"
alert( `hei ${"name"}` ); // hei name

// lauseke on muuttuja, upotetaan se
alert( `hei ${name}` ); // hei Ilya
```