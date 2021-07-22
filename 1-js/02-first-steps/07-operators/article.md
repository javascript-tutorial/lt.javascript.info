# Operatoriai

Mes žinome daug operatorių iš mokyklos. Tokie kaip sudėtis `+`, daugyba `*`, atimtis `-` ir taip toliau.

Šiame skyriuje, susikoncentruosime prie tokio operatorių aspekto, kuris nėra aptariamas mokykloje.

## Terminai: "unary", "binary", "operand"

Prieš tęsiant, išsiaiškinkime įprastinę terminologiją.

- *An operand* -- operandas yra tai kam operatoriai yra naudojami. Pavyzdžiui šioje daugyboje `5 * 2` yra du operandai: kairysis operandas yra `5`, o dešinysis yra `2`. Kartais žmonės juos vadina argumentais, o ne operandais.
- Operatorius yra *unarinis* (ang. *unary*), jeigu turi vieną operandą. Pavyzdžiui unarinis neiginys (ang. negation) `-` paverčia skaičių neigiamu:

    ```js run
    let x = 1;

    *!*
    x = -x;
    */!*
    alert( x ); // -1, pritaikytas unarinis neiginys
    ```
- Operatorius yra *binarinis* (ang. *binary*) kai turi du operandus. Tas pats minusas egzistuoja ir binarinėse formose:

    ```js run no-beautify
    let x = 1, y = 3;
    alert( y - x ); // 2, binarinis minusas atima vertes
    ```

    Formaliai aukščiau esančiame pavyzdyje mes turime du skirtingus operatorius, kurie dalinasi tuo pačiu simboliu: neigimo operatorių, t.y. unarinį operatorių, kuris pakeičia simbolį, ir atimties operatorių, t.y. binarinį operatorių, kuris atima vieną skaičių iš kito. 

## Eilutės sujungimas, binarinis +

Dabar susipažinkime su ypatingomis JavaScript savybėmis, kurios pranoksta mokyklos aritmetiką.

Dažniausiai operatorius pliusas `+` sumuoja skaičius.

Bet jeigu binarinis `+` pritaikomas eilutėms, pliusas jas sulieja (sujungia):

```js
let s = "my" + "string";
alert(s); // mystring
```

Atkreipkite dėmesį, jeigu vienas iš operandų yra eilutė, tai kitas taip pat paverčiamas eilute.

Pavyzdžiui:

```js run
alert( '1' + 2 ); // "12"
alert( 2 + '1' ); // "21"
```

Kaip matote nėra svarbu ar pirmasis operandas ar antrasis yra eilutė. Taisyklė paprasta: jeigu bent vienas operandas yra eilutė, kitas taip pat paverčiamas eilute.

Tačiau pastebėkite, kad operacijos vyksta iš kairės į dešinę. Jeigu pirmiau yra du numeriai, kuriuos seka eilutė, numeriai bus susumuoti ir tik tada paversti į eilutę:


```js run
alert(2 + 2 + '1' ); // "41" and not "221"
```

Eilutės sujungimas ir konversija yra ypatinga binarinio pliuso savybė `+`. Kiti aritmetiniai operatoriai veikia tik su skaičiais ir visada konvertuoja savo operandus į skaičius.

Pavyzdžiui, atimtis ir dalyba:

```js run
alert( 2 - '1' ); // 1
alert( '6' / '2' ); // 3
```

## Skaitinė konversija, unarinis +

Pliusas `+` egzistuoja dviejose formose: binarinėje formoje, kurią matėme aukščiau ir unarinėje formoje.

Unarinis pliusas arba kitaip sumos operatorius `+`, pritaikytas vienetinei vertei, nieko nedaro skaičiams. Bet jeigu operandas nėra skaičius, unarinis pliusas paverčia jį skaičiumi. 

Pavyzdžiui:

```js run
// Jokio efekto skaičiams
let x = 1;
alert( +x ); // 1

let y = -2;
alert( +y ); // -2

*!*
// Paverčia ne skaičius į skaičius
alert( +true ); // 1
alert( +"" );   // 0
*/!*
```

Tiesą sakant jis daro tą patį kaip `Number(...)`, bet daug trumpesne versija.

Poreikis eilutes pakeisti skaičiais pasitaiko labai dažnai. Pavyzdžiui kai gauname vertes iš HTML formų laukelių, jie dažniausiai yra eilutės. Kas jeigu mums reikia jas susumuoti? 

Binarinis pliusas juos sujungtų į eilutę:

```js run
let apples = "2";
let oranges = "3";

alert( apples + oranges ); // "23", binarinis pliusas eilutes sujungia
```

Jeigu mes norime skaičių, pirma turime juos konvertuoti ir tik tada galime susumuoti:

```js run
let apples = "2";
let oranges = "3";

*!*
// abi vertės iš anksto konvertuojamos į skaičius prieš binarinį pliusą
alert( +apples + +oranges ); // 5
*/!*

// ilgesnis variantas
// alert( Number(apples) + Number(oranges) ); // 5
```

Iš matematiko perspektyvos gausybė pliusų gali atrodyti keistai. Bet iš programuotojo pozicijos, tai nėra nieko ypatingo: unariniai pliusai pritaikomi pirmi, jie pakeičia eilutes į skaičius, o tada binarinis pliusas juos susumuoja.

Kodėl unariniai pliusai pritaikomi vertėms pirmiau nei binarinis? Kaip pamatysime vėliau, taip nutinka dėl jų *aukštesnio prioriteto* (ang. *higher precedence*).

## Operatorių pirmenybė

Jeigu išraiška turi daugiau operatorių nei vieną, jų vykdymo tvarką yra nustatoma pagal jų *pirmenybę*, arba kitaip sakant, iš ankto numatytąjį operatorių prioritetą. 

Dar mokykloje sužinojome, kad daugyba tokioje išraiškoje `1 + 2 * 2` turėtų būti suskaičiuojama prieš sudėtį. Tai ir yra pirmenybė. Yra tariama, kad daugyba turi *aukštesnį prioritetą* negu sudėtis.

Skliausteliai perrašo bet kokią pirmenybę, tad jeigu mums netinka numatyta tvarka, mes galime juos panaudoti, kad tai pakeistume. Pavyzdžiui rašydami `(1 + 2) * 2`.

JavaScript turi daug operatorių. Kiekvienas operatorius turi atitinkamą pirmenybės numerį. Tas kas turi aukštenį numerį įvykdomas pirmiau. Jeigu prioritetas vienodas, įvykdymo eilė yra iš kairės į dešinę. 

Štai ištrauka iš [pirmenybės lenteltės](https://developer.mozilla.org/en/JavaScript/Reference/operators/operator_precedence) (jums nereikia šito prisiminti, bet žinokite, kad unariniai operatoriai yra aukščiau už atitinkamus binarinius operatorius):

| Pirmenybė | Pavadinimas | Ženklas |
|------------|------|------|
| ... | ... | ... |
| 16 | unarinis pliusas | `+` |
| 16 | unarinis minusas | `-` |
| 14 | daugyba | `*` |
| 14 | dalyba | `/` |
| 13 | sudėtis | `+` |
| 13 | atimtis | `-` |
| ... | ... | ... |
| 3 | asignavimas | `=` |
| ... | ... | ... |

Kaip matome, "unarinis pliusas" turi `16` pirmenybę, kuri yra didesnė nei "sudėties" `13` (binarinis pliusas). Dėl tos priežasties, išraiškoje `"+apples + +oranges"`, unariniai pliusai suveikia pirmiau už sudėtį.

## Asignavimas

Atkreipkite dėmesį, kad asignavimas (kitaip užduoties operatorius) `=` taip pat yra operatorius. Lentelėje jis įrašytas kaip turintis labai žemą pirmenybę `3`.

Dėl tos priežasties kai mes priskiriame kintamąjį, kaip `x = 2 * 2 + 1`, visų pirma suskaičiuojama vertė ir tik tada `=` yra įvertinamas bei rezultatas patalpinamas į `x`.

```js
let x = 2 * 2 + 1;

alert( x ); // 5
```

Asignavimus įmanoma sujungti į grandinę:

```js run
let a, b, c;

*!*
a = b = c = 2 + 2;
*/!*

alert( a ); // 4
alert( b ); // 4
alert( c ); // 4
```

Sujungti į grandinę asignavimai įvertinami iš dešinės į kairę. Visų pirmą įvykdoma dešiniausiai esanti išraiška `2 + 2` ir priskiriama kintamiesiems esantiems dešinėje: `c`, `b` ir `a`. Galų gale visi kintamieji dalinasi viena verte.

````smart header="Užduoties operatorius `\"=\"` grąžina vertę"
Operatorius visada grąžina vertę. Tai yra akivaizdu tokiems kaip sudėtis `+` arba daugyba `*`. Bet asignavimas taip pat seka šita taisykle.

Šaukimas `x = value` įrašo `value` į `x` *ir tada ją grąžina*.

Štai pavyzdys su asignavimu sudėtingesnėje išraiškoje:

```js run
let a = 1;
let b = 2;

*!*
let c = 3 - (a = b + 1);
*/!*

alert( a ); // 3
alert( c ); // 0
```

Pavyzdyje aukščiau, išraiškos `(a = b + 1)` rezultatas yra vertė, kuri buvo priskirta `a` (tai yra `3`). Vėliau ji naudojama tolesniuose vertinimuose.

Kodas yra juokingas, juk taip? Turėtume suprasti kaip jis veikia, nes kartais tokius dalykus randame JavaScript bibliotekose, bet patys tokių geriau nerašykite. Tokie triukai tikrai nepaverčia kodo aiškesniu ir įskaitomesniu.
````

## Liekana %

Liekanos operatorius `%`, nepaisant jo išvaizdos, jis nėra susijęs su procentais.

Šios išraiškos `a % b` rezultatas yra liekana po sveikų skaičių dalybos `a` iš `b`.

Pavyzdžiui:

```js run
alert( 5 % 2 ); // 1 yra liekana kai 5 padalinami iš 2
alert( 8 % 3 ); // 2 yra liekana kai 8 padalinami iš 3
alert( 6 % 3 ); // 0 yra liekana kai 6 padalinami iš 3
```

## Kėlimas laipsniu **

Kėlimo laipsniu (ang. exponentiation) operatorius `**` yra naujas kalbos priedas.

Natūraliajam skaičiui `b`, kai `a ** b` rezultatas yra `a` padaugintas iš savęs `b` kartus.

Pavyzdžiui:

```js run
alert( 2 ** 2 ); // 4  (2 * 2)
alert( 2 ** 3 ); // 8  (2 * 2 * 2)
alert( 2 ** 4 ); // 16 (2 * 2 * 2 * 2)
```

Operatorius veikia ir su trupmenomis.

Pavyzdžiui:

```js run
alert( 4 ** (1/2) ); // 2 (laipsnis 1/2 yra taip pat kaip traukti iš šaknies, tai matematika)
alert( 8 ** (1/3) ); // 2 (laipsnis 1/3 taip pats kaip kubinė šaknis)
```

## Padidėjimas/sumažėjimas

<!-- Can't use -- in title, because built-in parse turns it into – -->

Skaičiaus padidinimas arba sumažinimas vienetu yra viena dažniausiai naudojamų įprastinių skaičių operacijų. 

Tad tam netgi yra specialūs operatoriai:

- **Padidinimas** `++` (ang. increment) kintamąjį padidina 1-u:

    ```js run no-beautify
    let counter = 2;
    counter++;        // veikia taip pat kaip counter = counter + 1, bet yra trumpesnis
    alert( counter ); // 3
    ```
- **Sumažinimas** `--` (ang. decrement) sumažina kintamajį 1-u:

    ```js run no-beautify
    let counter = 2;
    counter--;        // veikia taip kaip counter = counter - 1, bet yra trumpesnis
    alert( counter ); // 1
    ```

```warn
Padidinimas/sumažinimas gali būti taikomas tik kintamiesiems. Bandymas jį naudoti vertei kaip pavyzdžiui `5++` sukels klaidą.
```

Operatoriai `++` ir `--` gali būti dedami tiek prieš, tiek ir po kintamojo.

- Kai operatorius eina po kintamojo, jis yra "priedėlio formoje" (ang. "postfix form"): `counter++`.
- "Priešdėlio forma" (ang. "prefix form") yra tada kai operatorius eina prieš kintamąjį: `++counter`.

Both of these statements do the same thing: increase `counter` by `1`.

Is there any difference? Yes, but we can only see it if we use the returned value of `++/--`.

Let's clarify. As we know, all operators return a value. Increment/decrement is no exception. The prefix form returns the new value while the postfix form returns the old value (prior to increment/decrement).

To see the difference, here's an example:

```js run
let counter = 1;
let a = ++counter; // (*)

alert(a); // *!*2*/!*
```

In the line `(*)`, the *prefix* form `++counter` increments `counter` and returns the new value, `2`. So, the `alert` shows `2`.

Now, let's use the postfix form:

```js run
let counter = 1;
let a = counter++; // (*) changed ++counter to counter++

alert(a); // *!*1*/!*
```

In the line `(*)`, the *postfix* form `counter++` also increments `counter` but returns the *old* value (prior to increment). So, the `alert` shows `1`.

To summarize:

- If the result of increment/decrement is not used, there is no difference in which form to use:

    ```js run
    let counter = 0;
    counter++;
    ++counter;
    alert( counter ); // 2, the lines above did the same
    ```
- If we'd like to increase a value *and* immediately use the result of the operator, we need the prefix form:

    ```js run
    let counter = 0;
    alert( ++counter ); // 1
    ```
- If we'd like to increment a value but use its previous value, we need the postfix form:

    ```js run
    let counter = 0;
    alert( counter++ ); // 0
    ```

````smart header="Increment/decrement among other operators"
The operators `++/--` can be used inside expressions as well. Their precedence is higher than most other arithmetical operations.

For instance:

```js run
let counter = 1;
alert( 2 * ++counter ); // 4
```

Compare with:

```js run
let counter = 1;
alert( 2 * counter++ ); // 2, because counter++ returns the "old" value
```

Though technically okay, such notation usually makes code less readable. One line does multiple things -- not good.

While reading code, a fast "vertical" eye-scan can easily miss something like `counter++` and it won't be obvious that the variable increased.

We advise a style of "one line -- one action":

```js run
let counter = 1;
alert( 2 * counter );
counter++;
```
````

## Bitwise operators

Bitwise operators treat arguments as 32-bit integer numbers and work on the level of their binary representation.

These operators are not JavaScript-specific. They are supported in most programming languages.

The list of operators:

- AND ( `&` )
- OR ( `|` )
- XOR ( `^` )
- NOT ( `~` )
- LEFT SHIFT ( `<<` )
- RIGHT SHIFT ( `>>` )
- ZERO-FILL RIGHT SHIFT ( `>>>` )

These operators are used very rarely. To understand them, we need to delve into low-level number representation and it would not be optimal to do that right now, especially since we won't need them any time soon. If you're curious, you can read the [Bitwise Operators](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Operators/Bitwise_Operators) article on MDN. It would be more practical to do that when a real need arises.

## Modify-in-place

We often need to apply an operator to a variable and store the new result in that same variable.

For example:

```js
let n = 2;
n = n + 5;
n = n * 2;
```

This notation can be shortened using the operators `+=` and `*=`:

```js run
let n = 2;
n += 5; // now n = 7 (same as n = n + 5)
n *= 2; // now n = 14 (same as n = n * 2)

alert( n ); // 14
```

Short "modify-and-assign" operators exist for all arithmetical and bitwise operators: `/=`, `-=`, etc.

Such operators have the same precedence as a normal assignment, so they run after most other calculations:

```js run
let n = 2;

n *= 3 + 5;

alert( n ); // 16  (right part evaluated first, same as n *= 8)
```

## Comma

The comma operator `,` is one of the rarest and most unusual operators. Sometimes, it's used to write shorter code, so we need to know it in order to understand what's going on.

The comma operator allows us to evaluate several expressions, dividing them with a comma `,`. Each of them is evaluated but only the result of the last one is returned.

For example:

```js run
*!*
let a = (1 + 2, 3 + 4);
*/!*

alert( a ); // 7 (the result of 3 + 4)
```

Here, the first expression `1 + 2` is evaluated and its result is thrown away. Then, `3 + 4` is evaluated and returned as the result.

```smart header="Comma has a very low precedence"
Please note that the comma operator has very low precedence, lower than `=`, so parentheses are important in the example above.

Without them: `a = 1 + 2, 3 + 4` evaluates `+` first, summing the numbers into `a = 3, 7`, then the assignment operator `=` assigns `a = 3`, and the rest is ignored. It's like `(a = 1 + 2), 3 + 4`.
```

Why do we need an operator that throws away everything except the last expression?

Sometimes, people use it in more complex constructs to put several actions in one line.

For example:

```js
// three operations in one line
for (*!*a = 1, b = 3, c = a * b*/!*; a < 10; a++) {
 ...
}
```

Such tricks are used in many JavaScript frameworks. That's why we're mentioning them. But usually they don't improve code readability so we should think well before using them.
