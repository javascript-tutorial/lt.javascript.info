<<<<<<< HEAD:1-js/02-first-steps/07-operators/article.md
# Operatoriai
=======
# Basic operators, maths
>>>>>>> 193319c963b9ba86ac7d9590f7261a36ecdcc4d2:1-js/02-first-steps/08-operators/article.md

Mes žinome daug operatorių iš mokyklos. Tokie kaip sudėtis `+`, daugyba `*`, atimtis `-` ir taip toliau.

<<<<<<< HEAD:1-js/02-first-steps/07-operators/article.md
Šiame skyriuje, susikoncentruosime prie tokio operatorių aspekto, kuris nėra aptariamas mokykloje.
=======
In this chapter, we’ll start with simple operators, then concentrate on JavaScript-specific aspects, not covered by school arithmetic.
>>>>>>> 193319c963b9ba86ac7d9590f7261a36ecdcc4d2:1-js/02-first-steps/08-operators/article.md

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

    Formaliai aukščiau esančiame pavyzdyje mes turime du skirtingus operatorius, kurie dalinasi tuo pačiu simboliu: neigimo operatoriumi, t.y. unariniu operatoriumi, kuris pakeičia simbolį, ir atimties operatoriumi, t.y. binarinu operatoriumi, kuris atima vieną skaičių iš kito. 

<<<<<<< HEAD:1-js/02-first-steps/07-operators/article.md
## Eilutės sujungimas, binarinis +

Dabar susipažinkime su ypatingomis JavaScript savybėmis, kurios pranoksta mokyklos aritmetiką.
=======
## Maths

The following math operations are supported:

- Addition `+`,
- Subtraction `-`,
- Multiplication `*`,
- Division `/`,
- Remainder `%`,
- Exponentiation `**`.

The first four are straightforward, while `%` and `**` need a few words about them.

### Remainder %

The remainder operator `%`, despite its appearance, is not related to percents.

The result of `a % b` is the [remainder](https://en.wikipedia.org/wiki/Remainder) of the integer division of `a` by `b`.

For instance:

```js run
alert( 5 % 2 ); // 1, a remainder of 5 divided by 2
alert( 8 % 3 ); // 2, a remainder of 8 divided by 3
```

### Exponentiation **

The exponentiation operator `a ** b` raises `a` to the power of `b`.

In school maths, we write that as a<sup>b</sup>.

For instance:

```js run
alert( 2 ** 2 ); // 2² = 4
alert( 2 ** 3 ); // 2³ = 8
alert( 2 ** 4 ); // 2⁴ = 16
```

Just like in maths, the exponentiation operator is defined for non-integer numbers as well. 

For example, a square root is an exponentiation by ½:

```js run
alert( 4 ** (1/2) ); // 2 (power of 1/2 is the same as a square root)
alert( 8 ** (1/3) ); // 2 (power of 1/3 is the same as a cubic root)
```


## String concatenation with binary +

Let's meet features of JavaScript operators that are beyond school arithmetics.
>>>>>>> 193319c963b9ba86ac7d9590f7261a36ecdcc4d2:1-js/02-first-steps/08-operators/article.md

Dažniausiai operatorius pliusas `+` sumuoja skaičius.

Bet jeigu binarinis `+` pritaikomas eilutėms, pliusas jas sulieja (sujungia):

```js
let s = "my" + "string";
alert(s); // mystring
```

<<<<<<< HEAD:1-js/02-first-steps/07-operators/article.md
Atkreipkite dėmesį, jeigu vienas iš operandų yra eilutė, tai kitas taip pat paverčiamas eilute.
=======
Note that if any of the operands is a string, then the other one is converted to a string too.
>>>>>>> 193319c963b9ba86ac7d9590f7261a36ecdcc4d2:1-js/02-first-steps/08-operators/article.md

Pavyzdžiui:

```js run
alert( '1' + 2 ); // "12"
alert( 2 + '1' ); // "21"
```

<<<<<<< HEAD:1-js/02-first-steps/07-operators/article.md
Kaip matote nėra svarbu ar pirmasis operandas ar antrasis yra eilutė. Taisyklė paprasta: jeigu bent vienas operandas yra eilutė, kitas taip pat paverčiamas eilute.

Tačiau pastebėkite, kad operacijos vyksta iš kairės į dešinę. Jeigu pirmiau yra du numeriai, kuriuos seka eilutė, numeriai bus susumuoti ir tik tada paversti į eilutę:
=======
See, it doesn't matter whether the first operand is a string or the second one.
>>>>>>> 193319c963b9ba86ac7d9590f7261a36ecdcc4d2:1-js/02-first-steps/08-operators/article.md

Here's a more complex example:

```js run
alert(2 + 2 + '1' ); // "41" bet ne "221"
```

<<<<<<< HEAD:1-js/02-first-steps/07-operators/article.md
Eilutės sujungimas ir konversija yra ypatinga binarinio pliuso savybė `+`. Kiti aritmetiniai operatoriai veikia tik su skaičiais ir visada konvertuoja savo operandus į skaičius.

Pavyzdžiui, atimtis ir dalyba:
=======
Here, operators work one after another. The first `+` sums two numbers, so it returns `4`, then the next `+` adds the string `1` to it, so it's like `4 + '1' = '41'`.

```js run
alert('1' + 2 + 2); // "122" and not "14"
```
Here, the first operand is a string, the compiler treats the other two operands as strings too. The `2` gets concatenated to `'1'`, so it's like `'1' + 2 = "12"` and `"12" + 2 = "122"`.

The binary `+` is the only operator that supports strings in such a way. Other arithmetic operators work only with numbers and always convert their operands to numbers.

Here's the demo for subtraction and division:
>>>>>>> 193319c963b9ba86ac7d9590f7261a36ecdcc4d2:1-js/02-first-steps/08-operators/article.md

```js run
alert( 6 - '2' ); // 4, converts '2' to a number
alert( '6' / '2' ); // 3, converts both operands to numbers
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

Jeigu išraiška turi daugiau operatorių nei vieną, jų vykdymo tvarka yra nustatoma pagal jų *pirmenybę*, arba kitaip sakant, iš ankto numatytąjį operatorių prioritetą. 

Dar mokykloje sužinojome, kad daugyba tokioje išraiškoje `1 + 2 * 2` turėtų būti suskaičiuojama prieš sudėtį. Tai ir yra pirmenybė. Yra tariama, kad daugyba turi *aukštesnį prioritetą* negu sudėtis.

Skliausteliai perrašo bet kokią pirmenybę, tad jeigu mums netinka numatyta tvarka, mes galime juos panaudoti, kad tai pakeistume. Pavyzdžiui rašydami `(1 + 2) * 2`.

JavaScript turi daug operatorių. Kiekvienas operatorius turi atitinkamą pirmenybės numerį. Tas kas turi aukštenį numerį įvykdomas pirmiau. Jeigu prioritetas vienodas, įvykdymo eilė yra iš kairės į dešinę. 

<<<<<<< HEAD:1-js/02-first-steps/07-operators/article.md
Štai ištrauka iš [pirmenybės lentelės](https://developer.mozilla.org/en/JavaScript/Reference/operators/operator_precedence) (jums nereikia šito prisiminti, bet žinokite, kad unariniai operatoriai yra aukščiau už atitinkamus binarinius operatorius):
=======
Here's an extract from the [precedence table](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence) (you don't need to remember this, but note that unary operators are higher than corresponding binary ones):
>>>>>>> 193319c963b9ba86ac7d9590f7261a36ecdcc4d2:1-js/02-first-steps/08-operators/article.md

| Pirmenybė | Pavadinimas | Ženklas |
|------------|------|------|
| ... | ... | ... |
<<<<<<< HEAD:1-js/02-first-steps/07-operators/article.md
| 16 | unarinis pliusas | `+` |
| 16 | unarinis minusas | `-` |
| 14 | daugyba | `*` |
| 14 | dalyba | `/` |
| 13 | sudėtis | `+` |
| 13 | atimtis | `-` |
=======
| 17 | unary plus | `+` |
| 17 | unary negation | `-` |
| 16 | exponentiation | `**` |
| 15 | multiplication | `*` |
| 15 | division | `/` |
| 13 | addition | `+` |
| 13 | subtraction | `-` |
>>>>>>> 193319c963b9ba86ac7d9590f7261a36ecdcc4d2:1-js/02-first-steps/08-operators/article.md
| ... | ... | ... |
| 3 | asignavimas | `=` |
| ... | ... | ... |

<<<<<<< HEAD:1-js/02-first-steps/07-operators/article.md
Kaip matome, "unarinis pliusas" turi pirmenybę `16`, kuri yra didesnė nei "sudėties" `13` (binarinis pliusas). Dėl tos priežasties, išraiškoje `"+apples + +oranges"`, unariniai pliusai suveikia pirmiau už sudėtį.
=======
As we can see, the "unary plus" has a priority of `17` which is higher than the `13` of "addition" (binary plus). That's why, in the expression `"+apples + +oranges"`, unary pluses work before the addition.
>>>>>>> 193319c963b9ba86ac7d9590f7261a36ecdcc4d2:1-js/02-first-steps/08-operators/article.md

## Asignavimas

Atkreipkite dėmesį, kad asignavimas (kitaip užduoties operatorius) `=` taip pat yra operatorius. Lentelėje jis įrašytas kaip turintis labai žemą pirmenybę `3`.

Dėl tos priežasties kai mes priskiriame kintamąjį, kaip `x = 2 * 2 + 1`, visų pirma suskaičiuojama vertė ir tik tada `=` yra įvertinamas bei rezultatas patalpinamas į `x`.

```js
let x = 2 * 2 + 1;

alert( x ); // 5
```

<<<<<<< HEAD:1-js/02-first-steps/07-operators/article.md
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
Operatorius visada grąžina vertę. Tai yra akivaizdu tokiems atvejams kaip sudėtis `+` arba daugyba `*`. Bet asignavimas taip pat seka šita taisykle.
=======
### Assignment = returns a value

The fact of `=` being an operator, not a "magical" language construct has an interesting implication.

All operators in JavaScript return a value. That's obvious for `+` and `-`, but also true for `=`.
>>>>>>> 193319c963b9ba86ac7d9590f7261a36ecdcc4d2:1-js/02-first-steps/08-operators/article.md

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

<<<<<<< HEAD:1-js/02-first-steps/07-operators/article.md
Koks juokingas kodas, juk taip? Turėtume suprasti kaip jis veikia, nes kartais tokius dalykus randame JavaScript bibliotekose, bet patys tokių geriau nerašykite. Tokie triukai tikrai nepaverčia kodo aiškesniu ir įskaitomesniu.
````

## Liekana %

Liekanos operatorius `%`, nepaisant jo išvaizdos, nėra susijęs su procentais.

Šios išraiškos `a % b` rezultatas yra liekana po sveikų skaičių dalybos `a` iš `b`.

Pavyzdžiui:

```js run
alert( 5 % 2 ); // 1 yra liekana kai 5 padalinami iš 2
alert( 8 % 3 ); // 2 yra liekana kai 8 padalinami iš 3
alert( 6 % 3 ); // 0 yra liekana kai 6 padalinami iš 3
=======
Funny code, isn't it? We should understand how it works, because sometimes we see it in JavaScript libraries.

Although, please don't write the code like that. Such tricks definitely don't make code clearer or readable.

### Chaining assignments

Another interesting feature is the ability to chain assignments:

```js run
let a, b, c;

*!*
a = b = c = 2 + 2;
*/!*

alert( a ); // 4
alert( b ); // 4
alert( c ); // 4
```

Chained assignments evaluate from right to left. First, the rightmost expression `2 + 2` is evaluated and then assigned to the variables on the left: `c`, `b` and `a`. At the end, all the variables share a single value.

Once again, for the purposes of readability it's better to split such code into few lines:

```js
c = 2 + 2;
b = c;
a = c;
>>>>>>> 193319c963b9ba86ac7d9590f7261a36ecdcc4d2:1-js/02-first-steps/08-operators/article.md
```
That's easier to read, especially when eye-scanning the code fast.

<<<<<<< HEAD:1-js/02-first-steps/07-operators/article.md
## Kėlimas laipsniu **

Kėlimo laipsniu (ang. exponentiation) operatorius `**` yra naujas kalbos priedas.

Natūraliajam skaičiui `b`, kai `a ** b` rezultatas yra `a` padaugintas iš savęs `b` kartus.

Pavyzdžiui:
=======
## Modify-in-place

We often need to apply an operator to a variable and store the new result in that same variable.

For example:

```js
let n = 2;
n = n + 5;
n = n * 2;
```

This notation can be shortened using the operators `+=` and `*=`:
>>>>>>> 193319c963b9ba86ac7d9590f7261a36ecdcc4d2:1-js/02-first-steps/08-operators/article.md

```js run
let n = 2;
n += 5; // now n = 7 (same as n = n + 5)
n *= 2; // now n = 14 (same as n = n * 2)

alert( n ); // 14
```

<<<<<<< HEAD:1-js/02-first-steps/07-operators/article.md
Operatorius veikia ir su trupmenomis.

Pavyzdžiui:

```js run
alert( 4 ** (1/2) ); // 2 (laipsnis 1/2 yra taip pat kaip traukti iš šaknies, tai paprasta matematika)
alert( 8 ** (1/3) ); // 2 (laipsnis 1/3 taip pats kaip kubinė šaknis)
=======
Short "modify-and-assign" operators exist for all arithmetical and bitwise operators: `/=`, `-=`, etc.

Such operators have the same precedence as a normal assignment, so they run after most other calculations:

```js run
let n = 2;

n *= 3 + 5;

alert( n ); // 16  (right part evaluated first, same as n *= 8)
>>>>>>> 193319c963b9ba86ac7d9590f7261a36ecdcc4d2:1-js/02-first-steps/08-operators/article.md
```

## Padidėjimas/sumažėjimas

<!-- Can't use -- in title, because the built-in parser turns it into a 'long dash' – -->

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

Abu šie teiginiai daro tą patį: padidina `counter` vienu `1`.

Ar yra koks nors skirtumas? Taip, bet jį galime pamatyti tik naudodami grąžintą vertę iš `++/--`.

Pasiaiškinkime. Kaip žinoma, visi operatoriai grąžina vertę. Padidinimas/sumažinimas ne išimtis. Priešdėlio forma grąžina naują vertę kai tuo tarpu priedėlio forma grąžina senąją formą (prieš padidinimą/sumažinimą). 

Tam kad pamatytume skirtumą, pavyzdys:

```js run
let counter = 1;
let a = ++counter; // (*)

alert(a); // *!*2*/!*
```

Eilėje `(*)`, *priešdėlio* forma `++counter` padidina `counter` ir grąžina vertę `2`. Tad `alert` parodo `2`.

Dabar patikrinkime priedėlio formą:

```js run
let counter = 1;
let a = counter++; // (*) pakeitėme ++counter į counter++

alert(a); // *!*1*/!*
```

Eilutėje `(*)`, *priedėlio* forma `counter++` taip pat padidina `counter`, bet grąžina *senąją* vertę (dar prieš padidinimą. Tad `alert` parodo `1`.

Apibendrintai:

- Jeigu padidinimo/sumažinimo rezultatas nėra naudojamas, nėra jokio skirtumo kokią formą naudoti:

    ```js run
    let counter = 0;
    counter++;
    ++counter;
    alert( counter ); // 2, abi eilės viršuje padarė tą patį
    ```
- Jeigu norime padidinti vertę *ir* iš karto panaudoti operatoriaus rezultatą, mums reikia priešdėlio formos:

    ```js run
    let counter = 0;
    alert( ++counter ); // 1
    ```
- Jeigu norime padidinti vertę, bet naudoti jos senąją formą, mums reikia priedėlio formos:

    ```js run
    let counter = 0;
    alert( counter++ ); // 0
    ```

````smart header="Padidinimas/sumažinimas tarp kitų operatorių"
Operatoriai `++/--` gali būti naudojami su išraiškomis. Pirmumas yra aukštesnis už didelę dalį kitų aritmetinių veiksmų.

Pavyzdžiui:

```js run
let counter = 1;
alert( 2 * ++counter ); // 4
```

Palyginkite tai su:

```js run
let counter = 1;
alert( 2 * counter++ ); // 2, nes counter++ grąžina *senąją* vertę
```

Nors techniškai viskas yra gerai, bet tokie žymėjimai dažniausiai padaro kodą sunkiau įskaitomu. Viena eilutė atlieka daug veiksmų -- negerai.

Skaitant kodą, greitas "vertikalus" skanavimas akimis gali praleisti tokį užrašą kaip `counter++` ir nebus pilnai aišku, kad kintamasis padidėjo.

Mes patariame naudoti "viena eilutė -- vienas veiksmas" stilių:

```js run
let counter = 1;
alert( 2 * counter );
counter++;
```
````

## Bitų operatoriai

Bitų (ang. bitwise) operatoriai su argumentais elgiasi kaip su 32-bit sveikaisiais skaičias ir dirba jų binarinio pateikimo lygyje.

Tokie operatoriai nėra specifiniai vien JavaScript kalbai. Jie yra palaikomi didžiojoje dalyje programinių kalbų.

Operatorių sąrašas:

- AND ( `&` )
- OR ( `|` )
- XOR ( `^` )
- NOT ( `~` )
- LEFT SHIFT ( `<<` )
- RIGHT SHIFT ( `>>` )
- ZERO-FILL RIGHT SHIFT ( `>>>` )

<<<<<<< HEAD:1-js/02-first-steps/07-operators/article.md
Šie operatoriai naudojami labai retai. Kad juos suprastume, mums reikia pasinerti į žemo-lygio skaičių taikimą ir tai daryti šiuo metu nebūtų optimalu, juolabiau, kad mums jų greitu laiku neprireiks. Jeigu jums įdomu, galite daugiau paskaityti apie [Bitwise Operators](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Operators/Bitwise_Operators) MDN straipsnyje. Daug praktiškiau tai padaryti kai iškils tikras poreikis. 

## Keitimas vietoje (ang. Modify-in-place)

Mums dažnai tenka kintamajam pritaikyti operatorių ir tuo pačiu patalpinti naują rezultatą į tą patį kintamajį.

Pavyzdžiui:

```js
let n = 2;
n = n + 5;
n = n * 2;
```

Šis užrašas gali būti sutrumpintas naudojant operatorius `+=` ir `*=`:

```js run
let n = 2;
n += 5; // dabar n = 7 (tas pats kaip n = n + 5)
n *= 2; // dabar n = 14 (tas pats kaip n = n * 2)

alert( n ); // 14
```

Trumpieji "keitimo-ir-priskyrimo" operatoriai egzistuoja visiems aritmetiniams ir bitų operatoriams: `/=`, `-=` ir t.t.

Tokie operatoriai turi tokį patį pirmumą kaip ir įprastiniai asignavimai, tad jie dažniausiai vykdomi po didžiosios dalies kitų skaičiavimų:

```js run
let n = 2;

n *= 3 + 5;

alert( n ); // 16  (pirma įvykdoma dešinė pusė, tas pats kaip būtų n *= 8)
```
=======
These operators are used very rarely, when we need to fiddle with numbers on the very lowest (bitwise) level. We won't need these operators any time soon, as web development has little use of them, but in some special areas, such as cryptography, they are useful. You can read the [Bitwise Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#Bitwise) chapter on MDN when a need arises.
>>>>>>> 193319c963b9ba86ac7d9590f7261a36ecdcc4d2:1-js/02-first-steps/08-operators/article.md

## Kablelis

Kablelio operatorius `,` yra vienas iš rečiausių ir neįprasčiausių operatorių. Kartais jis naudojamas, kad sutrumpintume kodą, tad turime apie jį žinoti, kad suprastume kas vyksta.

Kablelio operatorius leidžia įvertinti kelias išraiškas, atskirdamas jas kableliu `,`. Kiekviena jų įvykdoma, tačiau grąžinamas tik rezultatas iš paskutinės išraiškos. 

Pavyzdžiui:

```js run
*!*
let a = (1 + 2, 3 + 4);
*/!*

alert( a ); // 7 (3 + 4 rezultatas)
```

šiuo atveju išraiška `1 + 2`  yra įvertinama, bet jos rezultatas išmetamas. Tada įvertinama `3 + 4` ir grąžinamas jos rezultatas.

```smart header="Kablelis turi labai žemą prioritetą"
Atkreipkite dėmesį, kad kablelio operatorius turi labai žemą prioritetą, žemesnį nei `=`, dėl to skliausteliai yra labai svarbūs kaip pavyzdyje aukščiau.

Be jų: `a = 1 + 2, 3 + 4` pirma įvertina `+` susumuodamas visus skaičius į `a = 3, 7`, o tada užduoties operatorius `=` priskiria `a = 3`, o visa kita yra ignoruojama. Panašiai lyg tai būtų `(a = 1 + 2), 3 + 4`.
```

Kam mums reikalingas operatorius, kuris išmeta viską išskyrus paskutinę išraišką? 

Kartais žmonės jį naudoja sudėtingesniuose konstruktuose, kad sudėtų kelis veiksmus į vieną eilę. 

Pavyzdžiui:

```js
// trys operacijos vienoje eilutėje
for (*!*a = 1, b = 3, c = a * b*/!*; a < 10; a++) {
 ...
}
```

Tokie triukai dažnai naudojami JavaScript struktūrose (ang. frameworks). Dėl to juos ir paminėjome. Bet dažniausiai jie nepalengvina kodo skaitymo tad turėtume gerai pagalvoti prieš juos naudodami.
