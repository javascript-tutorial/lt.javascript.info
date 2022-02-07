# Ciklai: while ir for

Mes dažnai turime pakartoti veiksmus. 

Pavyzdžiui, įvairių prekių išbraukimas viena paskui kitą iš sąrašo, arba paprasčiausiai to paties kodo paleidimas kiekvienam numeriui nuo 1 iki 10.

*Ciklai* (ang. *Loops*) yra būdas pakartoti daug kartų tą patį kodą.

## Ciklas "while"

Ciklas `while` turi sekančią sintaksę:

```js
while (sąlyga) {
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

Jeigu kodo pavyzdyje viršuje nebūtų `i++`, ciklas (teoriškai) kartotųsi amžinai. Praktikoje naršyklė suteikia būdų sustabdyti tokį ciklą ir procesas gali būti užbaigtas JavaScript serverio pusėje. 

Bet kokia išraiška arba kintamasis gali būti ciklo sąlyga, ne tik palyginimas: sąlyga yra įvertinama ir `while` ciklo paverčiama į loginį sprendimą. 

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

Ciklas `for` yra kiek sudėtingesnis, bet jis tuo pačiu yra dažniausiai naudojamas ciklas.

Jis atrodo taip:

```js
for (begin; condition; step) { // pradžia; sąlyga; žingsnis
  // ... ciklo korpusas ...
}
```

Išmokime šių dalių reikšmę su pavyzdžiais. Ciklas žemiau paleidžia `alert(i)` kol `i` yra nuo `0` iki (bet neįskaitant) `3`:

```js run
for (let i = 0; i < 3; i++) { // parodo 0, tada 1, tada 2
  alert(i);
}
```

Ištirkime teiginį `for` dalis po dalies:

| dalis |          |                                                                            |
|-------|----------|----------------------------------------------------------------------------|
<<<<<<< HEAD:1-js/02-first-steps/12-while-for/article.md
| pradžia | `i = 0`    | Įvykdomas vieną kartą pradedant ciklą.                                 |
| salyga | `i < 3`| Patikrinama prieš kiekvieną ciklo iteraciją. Jeigu netiesa, ciklas sustoja. |
| korpusas | `alert(i)`| Įvykdomas vėl ir vėl kol sąlyga yra truthy.                         |
| žingsnis | `i++`     | Įvykdomas po korpuso per kiekvieną iteraciją.     |
=======
| begin | `let i = 0`    | Executes once upon entering the loop.                                      |
| condition | `i < 3`| Checked before every loop iteration. If false, the loop stops.              |
| body | `alert(i)`| Runs again and again while the condition is truthy.                         |
| step| `i++`      | Executes after the body on each iteration. |
>>>>>>> 71da17e5960f1c76aad0d04d21f10bc65318d3f6:1-js/02-first-steps/13-while-for/article.md

Įprastinio ciklo algoritmas veikia taip:

```
Pradedamas vykdymas
→ (jeigu sąlyga → paleisti korpusą ir paleisti žingsnį)
→ (jeigu sąlyga → paleisti korpusą ir paleisti žingsnį)
→ (jeigu sąlyga → paleisti korpusą ir paleisti žingsnį)
→ ...
```

Tai yra, `begin` įvykdomas vieną kartą ir tada jis kartojasi (ang. iterates): po kiekvieno `sąlygos` testo įvykdomi `korpusas` ir `žingsnis`.

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

````smart header="Vidinio kintamojo deklaracija"
Čia "skaičiuojantis" (ang. "counter") kintamasis `i` yra deklaruotas tiesiai cikle. Tai vadinama "vidinio" (ang. "inline") kintamojo deklaracija. Toks kintamasis yra matomas tik ciklo viduje.

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

alert(i); // 3, matomas, nes buvo deklaruotas už ciklo ribų
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

Atkreipkite dėmesį, kad du `for` kabliataškiai `;` yra privalomi. Kitu atveju bus sintaksės klaida.

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

Galime tai naudoti kai baigiame su esama iteracija ir esame pasiruošę pereiti prie sekančios.

Ciklas žemiau naudoja `continue`, kad atiduotų tik nelygines vertes:

```js run no-beautify
for (let i = 0; i < 10; i++) {

  // jeigu tiesa, praleisti likusią korpuso dalį
  *!*if (i % 2 == 0) continue;*/!*

  alert(i); // 1, tada 3, 5, 7, 9
}
```

Lyginėms `i` vertėms, direktyva `continue` nustoja vykdyti korpusą ir perleidžia kontrolę sekančiai `for` iteracijai (su sekančiu skaičiumi). Tad `alert` yra iškviečiamas tik nelyginėms vertėms.

````smart header="Direktyva `continue` sumažina matrioškinį kodą (ang. nesting)"
Ciklas, kuris parodo nelygines vertes gali atrodyti ir taip:

```js run
for (let i = 0; i < 10; i++) {

  if (i % 2) {
    alert( i );
  }

}
```

Iš techninės perspektyvos tai yra visiškai identiškas kodas aukščiau esančiam pavyzdžiui. Žinoma, mes galime tiesiog apgobti `if` rinkinį vietoje to, kad naudotume `continue`.

<<<<<<< HEAD:1-js/02-first-steps/12-while-for/article.md
Bet to pašalinis efektas yra papildomas matrioškinis lygis (šaukimas `alert` viduje riestinių skliaustų). O jeigu kodas `if` viduje yra ilgesnis nei kelios eilės, tai apsunkina skaitomumą. 
=======
But as a side-effect, this created one more level of nesting (the `alert` call inside the curly braces). If the code inside of `if` is longer than a few lines, that may decrease the overall readability.
>>>>>>> 71da17e5960f1c76aad0d04d21f10bc65318d3f6:1-js/02-first-steps/13-while-for/article.md
````

````warn header="Jokių `break/continue` dešinėje '?' pusėje"
Atkreipkite dėmesį, kad sintaksiniai konstruktai, kurie nėra išraiškos, negalimi su ternariniu operatoriumi `?`. Ypatingai tokios direktyvos kaip `break/continue` yra neleidžiamos.

Pavyzdžiui, jeigu paimtume tokį kodą:

```js
if (i > 5) {
  alert(i);
} else {
  continue;
}
```

...ir perrašytume jį naudodami klaustuką:


```js no-beautify
(i > 5) ? alert(i) : *!*continue*/!*; // continue nėra leidžiamas
```

...jis nustoja veikti: tai yra sintaksės klaida.

Tai tik dar viena priežastis nenaudoti klaustuko operatoriaus `?` vietoje`if`.
````

## Etiketės break/continue

Kartais mums reikia ištrūkti iš daugybinių matrioškinių ciklų tuo pačiu metu.

Pavyzdžiui, kode žemiau mes paleidžiame ciklą per `i` ir `j`, klausdami koordinačių `(i, j)` nuo `(0,0)` iki `(2,2)`:

```js run no-beautify
for (let i = 0; i < 3; i++) {

  for (let j = 0; j < 3; j++) {

    let input = prompt(`Vertė koordinatėse (${i},${j})`, '');

    // kas nutinka jeigu norime išeiti šiuo momentu iki Baigta (žemiau)?
  }
}

alert('Baigta!');
```

Mums reikia tokio būdo, kuris sustabdytų procesą, jeigu lankytojas atšaukia įvedimą.

<<<<<<< HEAD:1-js/02-first-steps/12-while-for/article.md
Įprastinis `break` sekantis po `input` sustabdytų tik vidinį ciklą. To neužtenka--į pagalba ateina etiketės!
=======
The ordinary `break` after `input` would only break the inner loop. That's not sufficient -- labels, come to the rescue!
>>>>>>> 71da17e5960f1c76aad0d04d21f10bc65318d3f6:1-js/02-first-steps/13-while-for/article.md

*Etikėtė* tai toks identifikatorius su dvitaškiu prieš ciklą:
```js
etiketėsPavadinimas: for (...) {
  ...
}
```

Teiginys `break <etiketėsPavadinimas>` cikle žemiau nutraukia procesą iki etiketės:

```js run no-beautify
*!*išorinis:*/!* for (let i = 0; i < 3; i++) {

  for (let j = 0; j < 3; j++) {

    let input = prompt(`Vertė koordinatėse (${i},${j})`, '');

    // jeigu eilutė tuščia arba buvo atšaukta, nutraukti procesą iš abiejų ciklų
    if (!input) *!*break išorinis*/!*; // (*)

    // darykite kažką su verte...
  }
}
alert('Baigta!');
```

Kodas viršuje `break išorinis` suranda viršuje etiketę su pavadinimu `išorinis` ir nutraukia tą ciklą.

Tad kontrolė pereina tiesiai nuo `(*)` iki `alert('Baigta!')`.

Mes taip pat galime perkelti etiketę į atskirą eilę:

```js no-beautify
išorinis:
for (let i = 0; i < 3; i++) { ... }
```

Direktyva `continue` taip pat gali būti naudojama su etiketėmis. Šiuo atveju kodo įvykdymas peršoka prie sekančios ciklo su etikete iteracijos.

````warn header="Etiketės neleidžia \"peršokti\" bet kur"
Etiketės negali leisti peršokti į bet kurią arbitrišką kodo vietą.

Pavyzdžiui tai nėra įmanoma:
```js
<<<<<<< HEAD:1-js/02-first-steps/12-while-for/article.md
break etiketė; // neperšoka į etiketę žemiau
=======
break label; // jump to the label below (doesn't work)
>>>>>>> 71da17e5960f1c76aad0d04d21f10bc65318d3f6:1-js/02-first-steps/13-while-for/article.md

etiketė: for (...)
```

<<<<<<< HEAD:1-js/02-first-steps/12-while-for/article.md
Šaukimas `break/continue` įmanoma tik iš ciklo vidaus ir etiketė turi būti kažkur virš direktyvos.
=======
A `break` directive must be inside a code block. Technically, any labelled code block will do, e.g.:
```js
label: {
  // ...
  break label; // works
  // ...
}
```

...Although, 99.9% of the time `break` is used inside loops, as we've seen in the examples above.

A `continue` is only possible from inside a loop.
>>>>>>> 71da17e5960f1c76aad0d04d21f10bc65318d3f6:1-js/02-first-steps/13-while-for/article.md
````

## Santrauka

Mes aptarėme 3 ciklų tipus:

- `while` -- Sąlyga patikrinima prieš kiekvieną iteraciją.
- `do..while` -- Sąlyga patikrinama po kiekvienos iteracijos.
- `for (;;)` -- Sąlyga patikrinama prieš kiekvieną iteraciją, įmanomi papildomi nustatymai.

Kad padarytume "begalinį" ciklą, naudojamas konstruktas `while(true)`. Toks ciklas, kaip ir bet kuris kitas, gali būti sustabdytas naudojant direktyvą `break`.

Jeigu nenorime nieko daryti esamoje iteracijoje, bet norime pereiti prie sekančios, galime naudoti `continue` direktyvą.

`break/continue` palaiko etiketes prieš ciklą. Etiketė yra vienintelis kelias tam, kad `break/continue` išeitų iš matrioškinio vidinio ciklo į išorinį.
