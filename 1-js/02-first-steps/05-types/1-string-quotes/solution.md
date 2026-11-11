
Takahipsut upottavat merkkijonoon merkintöjen `${...}` sisällä olevan lausekkeen.

```js run
let name = "Ilya";

// lauseke on luku 1
alert( `hello ${1}` ); // hello 1

// lauseke on merkkijono "name"
alert( `hello ${"name"}` ); // hello name

// lauseke on muuttuja, upotetaan se
alert( `hello ${name}` ); // hello Ilya
```