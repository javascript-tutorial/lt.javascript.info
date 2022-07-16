Taip yra todėl, kad `prompt` grąžina naudotojo įvestį kaip eilutę.

Taigi kintamieji atitinkamai turi vertes `"1"` ir `"2"`.

```js run
let a = "1"; // prompt("Pirmasis skaičius?", 1);
let b = "2"; // prompt("Antrasis skaičius?", 2);

alert(a + b); // 12
```

Prieš `+` turėtume konvertuoti eilutes į skaičius. Pavyzdžiui, naudodami `Number()` arba prieš tai pridėdami `+` prie jų.

Pavyzdžiui, prieš pat `prompt`:

```js run
let a = +prompt("Pirmasis skaičius?", 1);
let b = +prompt("Antrasis skaičius?", 2);

alert(a + b); // 3
```

Arba viduje `alert`:

```js run
let a = prompt("Pirmasis skaičius?", 1);
let b = prompt("Antrasis skaičius?", 2);

alert(+a + +b); // 3
```

Pastarajame variante naudojamas ir unarinis, ir binarinis `+`. Atrodo linksmai, ar ne?
