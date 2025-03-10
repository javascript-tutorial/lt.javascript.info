# Rodyklių funkcijos, pagrindai

Yra dar viena labai paprasta ir glausta funkcijų kūrimo sintaksė, kuri dažnai yra geresnė už Function Expressions.

Ji vadinama “rodyklių funkcijomis” (ang. *“arrow functions”*), nes atrodo taip:

```js
let func = (arg1, arg2, ..., argN) => expression;
```

Čia sukuriama funkcija `func`, kuri priima argumentus `arg1..argN`, tada įvertina dešinėje pusėje esantį `expression` su jų panaudojimu ir grąžina rezultatą.

Kitaip tariant, tai yra trumpesnė versija:

```js
let func = function(arg1, arg2, ..., argN) {
  return expression;
};
```

Išnagrinėkime konkretų pavyzdį:

```js run
let sum = (a, b) => a + b;

/* Ši rodyklės funkcija yra trumpesnė forma:

let sum = function(a, b) {
  return a + b;
};
*/

alert( sum(1, 2) ); // 3
```

Kaip jūs matote, `(a, b) => a + b` reiškia funkciją, kuri priima du argumentus, pavadintus `a` ir `b`. Vykdymo metu ji įvertina išraišką `a + b` ir grąžina rezultatą.

- Jeigu mes turime tik vieną argumentą, skliaustelius aplink parametrus galima praleisti ir taip dar labiau sutrumpinti užrašą

    Pavyzdžiui:

    ```js run
    *!*
    let double = n => n * 2;
    // maždaug tas pats kaip: let double = function(n) { return n * 2 }
    */!*

    alert( double(3) ); // 6
    ```

<<<<<<< HEAD
- Jeigu argumentų nėra, skliaustai bus tušti (tačiau jie turėtų būti):
=======
- If there are no arguments, parentheses are empty, but they must be present:
>>>>>>> 1dce5b72b16288dad31b7b3febed4f38b7a5cd8a

    ```js run
    let sayHi = () => alert("Labas!");

    sayHi();
    ```

Rodyklės funkcijas galima naudoti taip pat, kaip ir Function Expressions.

Pavyzdžiui, norėdami dinamiškai sukurti funkciją:

```js run
let age = prompt("Koks jūsų amžius?", 18);

let welcome = (age < 18) ?
<<<<<<< HEAD
  () => alert('Labas!') :
  () => alert("Laba diena!");
=======
  () => alert('Hello!') :
  () => alert("Greetings!");
>>>>>>> 1dce5b72b16288dad31b7b3febed4f38b7a5cd8a

welcome();
```

Iš pradžių rodyklių funkcijos gali atrodyti nepažįstamos ir nelabai skaitomos, tačiau tai greitai pasikeičia, kai akys pripranta prie struktūros.

Jie labai patogūs atliekant paprastus vienos eilutės veiksmus, kai tiesiog tingime rašyti daug žodžių.

## Kelių eilučių rodyklių funkcijos

<<<<<<< HEAD
Aukščiau pateiktuose pavyzdžiuose buvo paimti argumentai iš `=>` kairės pusės ir su jais įvertinta dešiniosios pusės išraiška.

Kartais mums reikia šiek tiek sudėtingesnių dalykų, pavyzdžiui, kelių išraiškų ar teiginių. Tai taip pat įmanoma, tačiau jas turėtume uždaryti figūriniais skliaustais. Tada juose reikia naudoti įprastą `return`.
=======
The arrow functions that we've seen so far were very simple. They took arguments from the left of `=>`, evaluated and returned the right-side expression with them.

Sometimes we need a more complex function, with multiple expressions and statements. In that case, we can enclose them in curly braces. The major difference is that curly braces require a `return` within them to return a value (just like a regular function does).
>>>>>>> 1dce5b72b16288dad31b7b3febed4f38b7a5cd8a

Štai taip:

```js run
let sum = (a, b) => {  // figūrinis skliaustelis atveria kelių eilučių funkciją
  let result = a + b;
*!*
  return result; // jei naudojame figūrinius skliaustus, reikia aiškiai nurodyti "return".
*/!*
};

alert( sum(1, 2) ); // 3
```

```smart header="Toliau mes išmoksime daugiau"
Čia mes pateikėme pagrindinę rodyklių funkcijų paskirtį -- trumpumas. Bet tai dar ne viskas!

Rodyklių funkcijos turi ir kitų įdomių savybių.

Norėdami jas nuodugniai išnagrinėti, pirmiausia turime susipažinti su kitais JavaScript aspektais, todėl prie rodyklių funkcijų grįšime vėliau, skyriuje <info:arrow-functions>.

O dabar mes jau galime naudoti rodyklių funkcijas vienos eilutės veiksmams ir callback'ams.
```

## Santrauka

<<<<<<< HEAD
Rodyklių funkcijos yra patogios, kai reikia parašyti vieną eilutę. Jos būna dviejų rūšių:

1. Be figūrinių skliaustų: `(...args) => expression` -- dešinioji išraiškos pusė: funkcija ją apskaičiuoja ir grąžina rezultatą. Skliaustelius galima praleisti, jei yra tik vienas argumentas: `n => n * 2`.
2. Su figūriniais skliaustais: `(...args) => { body }` -- figūriniai skliaustai leidžia įrašyti kelis teiginius funkcijos viduje, tačiau mums reikia aiškaus `return`, kad ką nors grąžintume.
=======
Arrow functions are handy for simple actions, especially for one-liners. They come in two flavors:

1. Without curly braces: `(...args) => expression` -- the right side is an expression: the function evaluates it and returns the result. Parentheses can be omitted, if there's only a single argument, e.g. `n => n*2`.
2. With curly braces: `(...args) => { body }` -- brackets allow us to write multiple statements inside the function, but we need an explicit `return` to return something.
>>>>>>> 1dce5b72b16288dad31b7b3febed4f38b7a5cd8a
