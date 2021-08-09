# Ciklai: while ir for

Mes dažnai turime pakartoti veiksmus. 

Pavyzdžiui, įvairių dalykų išvedimas vienas paskui kitą iš sąrašo, arba paprasčiausiai to paties kodo paliedimas kiekvienam numeriui nuo 1 iki 10.

*Cilkai* (ang. *Loops*) yra būdas pakartoti daug kartų tą patį kodą.

## Ciklas "while"

Ciklas `while` turi sekančią sintaksę:

```js
while (condition) {
  // kodas
  // taip vadinamas "ciklo korpusas" (ang. "loop body")
}
```

Kol `sąlyga` yra truthy, `kodas` iš ciklo rinkinio yra įvykdomas.

Pavyzdžiui, ciklas žemiau atiduoda `i` kol `i < 3`:

```js run
let i = 0;
while (i < 3) { // parodo 0, tada 1, tada 2
  alert( i );
  i++;
}
```

Vienas ciklo rinkinio įvykdymas vadinamas *iteracija* (ang. *an iteration*). Ciklas pavyzdyje aukščiau padaro tris iteracijas.

Jeigu kodo pavyzdyje viršuje nebūtų `i++`, ciklas (teoriškai) kartotųsi amžinai. Praktiškai, naršyklė suteikia būdų sustabdyti tokį ciklą ir procesas gali būti užbaigtas serverio pusės JavaScript. 

Bet kokia išraiška arba kintamasis gali būti ciklo sąlyga, ne tik palyginimas: sąlyga yra įvertinama ir `while` paverčiama į loginį sprendimą. 

Pavyzdžiui, trumpesnis būdas parašyti `while (i != 0)` yra `while (i)`:

```js run
let i = 3;
*!*
while (i) { // kai i pavirsta 0, sąlyga tampa falsy ir ciklas sustoja
*/!*
  alert( i );
  i--;
}
```

````smart header="Riestiniai skliaustai nėra reikalingi vienos eilės korpusui"
Jeigu ciklo kopusas turi tik vieną teiginį, galime nenaudoti riestinių skliaustų `{…}`:

```js run
let i = 3;
*!*
while (i) alert(i--);
*/!*
```
````

## Ciklas "do..while"

Sąlygos patikrinimas gali būtų perkeltas *žemiau* ciklo korpuso naudojant sintaksę `do..while`:

```js
do {
  // ciklo korpusas
} while (sąlyga);
```

Ciklas visų pirma įvykdys korpusą, tada patikrins sąlygą ir kol ji yra truthy, įvykdys vėl ir vėl.

Pavyzdžiui:

```js run
let i = 0;
do {
  alert( i );
  i++;
} while (i < 3);
```

Tokia sintaksė turėtų būti naudojama kai norite, kad ciklo korpusas būtų įvykdytas **bent vieną kartą** nepaisant to ar jo sąlyga yra truthy. Dažniausiai vis dėlto naudojama kita forma: `while(…) {…}`.

## Ciklas "for"

Ciklas `for` yra kiek sudėtingesnis, bet jis taip pat yra dažniausiai naudojamas ciklas.

Jis atrodo taip:

```js
for (begin; condition; step) { // pradžia; sąlyga; žingsnis
  // ... ciklo korpusas ...
}
```

Išmokime šių dalių reikšmę su pavyzdžiais. Ciklas žemiau paleidžia `alert(i)` dėl `i` nuo `0` iki (bet neįskaitant) `3`:

```js run
for (let i = 0; i < 3; i++) { // parodo 0, tada 1, tada 2
  alert(i);
}
```

Ištirkime teiginį `for` dalis po dalies:

| dalis |          |                                                                            |
|-------|----------|----------------------------------------------------------------------------|
| pradžia | `i = 0`    | Įvykdomas vieną kartą pradedant ciklą.                                 |
| salyga | `i < 3`| Patikrinama prieš kiekvieną ciklo iteraciją. Jeigu netiesa, ciklas sustoja. |
| korpusas | `alert(i)`| Įvykdomas vėl ir vėl kol sąlyga yra truthy.                         |
| žingsnis | `i++`     | Įvykdomas po korpuso per kiekvieną iteraciją.     |

Įprastinio ciklo algoritmas veikia taip:

```
Pradedamas vykdymas
→ (jeigu sąlyga → paleisti korpusą ir paleisti žingsnį)
→ (jeigu sąlyga → paleisti korpusą ir paleisti žingsnį)
→ (jeigu sąlyga → paleisti korpusą ir paleisti žingsnį)
→ ...
```

Tai yra, `begin` įvykdomas vieną kartą ir tada jis kartojasi (ang. iterates): po kiekvieno `sąlygos` testo, įvykdomi `korpusas` ir `žingsnis`.

Jeigu ciklai jums naujiena, juos geriau suprasti padėtų , jeigu sugrįžtumėte prie pavyzdžio ir žingsnis po žingsnio atkurtumėte kaip jis veikia ant popieriaus lapo.

Štai kas konkrečiai vyksta mūsų atveju:

```js
// for (let i = 0; i < 3; i++) alert(i)

// pradedamas vykdymas
let i = 0
// jeigu sąlyga → paleisti korpusą ir paleisti žingsnį
if (i < 3) { alert(i); i++ }
// jeigu sąlyga → paleisti korpusą ir paleisti žingsnį
if (i < 3) { alert(i); i++ }
// jeigu sąlyga → paleisti korpusą ir paleisti žingsnį
if (i < 3) { alert(i); i++ }
// ...pabaiga, nes dabar i == 3
```

````smart header="Įterptojo kintamojo deklaracija"
Čia "skaičiuojantis" (ang. "counter") kintamasis `i` yra deklaruotas tiesiai cikle. Tai vadinama "įterptojo" (ang. "inline") kintamojo deklaracija. Toks kintamasis yra matomas tik ciklo viduje.

```js run
for (*!*let*/!* i = 0; i < 3; i++) {
  alert(i); // 0, 1, 2
}
alert(i); // klaida, tokio kintamojo nėra
```

Vietoje to, kad apibrėžtume kintamąjį, galime naudoti jau egzituojantį:

```js run
let i = 0;

for (i = 0; i < 3; i++) { // naudojamas jau egzituojantis kintamasis
  alert(i); // 0, 1, 2
}

alert(i); // 3, matomas, nes deklaruotas už ciklo ribų
```

````


### Dalių praleidimas

Bet kuri `for` dalis gali būti praleista.

Pavyzdžiui, mes galime neįtraukti `begin`, jeigu mums nieko nereikia daryti ciklo pradžioje.

Kaip šiame pavyzdyje:

```js run
let i = 0; // jau turime deklaravę ir priskyrę i

for (; i < 3; i++) { // nereikia "pradžios"
  alert( i ); // 0, 1, 2
}
```

Taip pat galime nenaudoti `žingsnio` dalies:

```js run
let i = 0;

for (; i < 3;) {
  alert( i++ );
}
```

Tai padaro ciklą identišku `while (i < 3)`.

Mes netgi galime viską panaikinti, sukurdami begalinį ciklą:

```js
for (;;) {
  // kartojasi be ribų
}
```

Atkreipkite dėmesį, kad du `for` kabliataškiai `;` myra privalomi. Kitu atveju bus sintaksės klaida.

## Ciklo nutraukimas

Dažniausiai, ciklas egzituoja kol jo sąlyga tampa falsy.

Bet mes galime priverstinai išeiti naudodami ypatingają `break` direktyvą.

Pavyzdžiui, ciklas žemiau klausia naudotojo numerių serijos, "nutraukdamas" kai nėra įvedamas skaičius:

```js run
let sum = 0;

while (true) {

  let value = +prompt("Įveskite skaičių", '');

*!*
  if (!value) break; // (*)
*/!*

  sum += value;

}
alert( 'Suma: ' + sum );
```

Direktyva `break` yra aktyvuojama eilutėje `(*)`, jeigu lankytojas pateikia tuščią rezultatą arba atšaukia įvedimą. Tai iš karto sustabdo ciklą, perduodant kontrolę pirmai eilei po ciklo. Šiuo atveju `alert`.

Kombinacija "bagalinis ciklas + `break` kai reikia" yra gerai tokiose situacijose kai ciklo sąlyga turi būti patikrinama ne pačioje pradžio ar pabaigoje ciklo, bet viduryje arba netgi keliose jo korpuso vietose. 

## Tęsinys kitoje iteracijoje [#continue]

Direktyva `continue` (tęsti) yra "lengvesnė versija" direktyvos `break`. Ji nesustobado viso ciklo. Vietoje to, ji sustabdo esamą iteraciją ir priverčią ciklą pradėti naują iteraciją (jeigu sąlyga tai leidžia).

Galime tai naudoti kai baihiame su esama iteracija ir esame pasiruošę pereiti prie sekančios.

Ciklas žemiau naudoja `continue`, kad atiduotų tik nelygines vertes:

```js run no-beautify
for (let i = 0; i < 10; i++) {

  // jeigu tiesa, praleisti likusią korpuso dalį
  *!*if (i % 2 == 0) continue;*/!*

  alert(i); // 1, then 3, 5, 7, 9
}
```

Lyginėms `i` vertėms, direktyva `continue` nustoja vykdyti korpusą ir perleidžia kontrolę sekančiai `for` iteracijai (su sekančiu skaičiumi). Tad `alert` yra iškviečiamas tik nelyginėms vertėms.

````smart header="The `continue` directive helps decrease nesting"
A loop that shows odd values could look like this:

```js
for (let i = 0; i < 10; i++) {

  if (i % 2) {
    alert( i );
  }

}
```

From a technical point of view, this is identical to the example above. Surely, we can just wrap the code in an `if` block instead of using `continue`.

But as a side-effect, this created one more level of nesting (the `alert` call inside the curly braces). If the code inside of`if` is longer than a few lines, that may decrease the overall readability.
````

````warn header="No `break/continue` to the right side of '?'"
Please note that syntax constructs that are not expressions cannot be used with the ternary operator `?`. In particular, directives such as `break/continue` aren't allowed there.

For example, if we take this code:

```js
if (i > 5) {
  alert(i);
} else {
  continue;
}
```

...and rewrite it using a question mark:


```js no-beautify
(i > 5) ? alert(i) : *!*continue*/!*; // continue isn't allowed here
```

...it stops working: there's a syntax error.

This is just another reason not to use the question mark operator `?` instead of `if`.
````

## Labels for break/continue

Sometimes we need to break out from multiple nested loops at once.

For example, in the code below we loop over `i` and `j`, prompting for the coordinates `(i, j)` from `(0,0)` to `(2,2)`:

```js run no-beautify
for (let i = 0; i < 3; i++) {

  for (let j = 0; j < 3; j++) {

    let input = prompt(`Value at coords (${i},${j})`, '');

    // what if we want to exit from here to Done (below)?
  }
}

alert('Done!');
```

We need a way to stop the process if the user cancels the input.

The ordinary `break` after `input` would only break the inner loop. That's not sufficient--labels, come to the rescue!

A *label* is an identifier with a colon before a loop:
```js
labelName: for (...) {
  ...
}
```

The `break <labelName>` statement in the loop below breaks out to the label:

```js run no-beautify
*!*outer:*/!* for (let i = 0; i < 3; i++) {

  for (let j = 0; j < 3; j++) {

    let input = prompt(`Value at coords (${i},${j})`, '');

    // if an empty string or canceled, then break out of both loops
    if (!input) *!*break outer*/!*; // (*)

    // do something with the value...
  }
}
alert('Done!');
```

In the code above, `break outer` looks upwards for the label named `outer` and breaks out of that loop.

So the control goes straight from `(*)` to `alert('Done!')`.

We can also move the label onto a separate line:

```js no-beautify
outer:
for (let i = 0; i < 3; i++) { ... }
```

The `continue` directive can also be used with a label. In this case, code execution jumps to the next iteration of the labeled loop.

````warn header="Labels do not allow to \"jump\" anywhere"
Labels do not allow us to jump into an arbitrary place in the code.

For example, it is impossible to do this:
```js
break label; // doesn't jumps to the label below

label: for (...)
```

A call to `break/continue` is only possible from inside a loop and the label must be somewhere above the directive.
````

## Summary

We covered 3 types of loops:

- `while` -- The condition is checked before each iteration.
- `do..while` -- The condition is checked after each iteration.
- `for (;;)` -- The condition is checked before each iteration, additional settings available.

To make an "infinite" loop, usually the `while(true)` construct is used. Such a loop, just like any other, can be stopped with the `break` directive.

If we don't want to do anything in the current iteration and would like to forward to the next one, we can use the `continue` directive.

`break/continue` support labels before the loop. A label is the only way for `break/continue` to escape a nested loop to go to an outer one.
