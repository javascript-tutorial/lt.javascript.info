# Loginiai operatoriai

JavaScript yra trys loginiai operatoriai: `||` (OR - arba), `&&` (AND - ir), `!` (NOT - ne).

Nors jie vadinami "loginiais", juos galima naudoti su bet kokio tipo vertėmis, ne vien loginėmis. Jų rezultatas taip pat gali būti bet kokio tipo.

Pažiūrėkime detaliau.

## || (OR)

Dvi vertikalios linijos atstoja "ARBA" operatorių:

```js
result = a || b;
```

Klasikiniame programavime, loginis ARBA yra skirtas manipuliuoti tik logines vertes. Jeigu bent vienas jo argumentas yra `true`, tai ir jis grąžina `true`, kitu atveju grąžina `false`.

JavaScript operatorius yra šiek tiek sudėtingesnis ir galingesnis. Bet visų pirma pažvelkime kas nutinka su loginėmis vertėmis.

Yra keturios įmanomos loginės kombinacijos:

```js run
alert( true || true );   // true
alert( false || true );  // true
alert( true || false );  // true
alert( false || false ); // false
```

Kaip matome, rezultatas yra visada `true` išskyrus kai abu operandai yra `false`.

Jeigu operandas nėra loginis, tai jis paverčiamas logine vertė, kad būtų įvertintas.

Pavyzdžiui, skaičius `1` laikomas `true`, skaičius `0` laikomas `false`:

```js run
if (1 || 0) { // veikia taip pat kaip ( true || false )
  alert( 'truthy!' );
}
```

Dažniausiai ARBA `||` yra naudojamas `if` teiginiuose, kad pratestuotų ar *kuri nors* iš duotų sąlygų yra `true`.

Pavyzdžiui:

```js run
let hour = 9;

*!*
if (hour < 10 || hour > 18) {
*/!*
  alert( 'Ofisas uždarytas.' );
}
```

Galime praleisti ir daugiau sąlygų:

```js run
let hour = 12;
let isWeekend = true;

if (hour < 10 || hour > 18 || isWeekend) {
  alert( 'Ofisas uždarytas.' ); // nes savaitgalis
}
```

## ARBA "||" suranda pirmąją truthy vertę

Aukščiau apibūdinta logika yra klasikinė. Dabar pridėkime "ekstra" JavaScript savybių.

Štai kaip veikia išplėstas algoritmas.

Turint daugybines ARBA vertes:

```js
result = value1 || value2 || value3;
```

ARBA `||` operatorius atlieka sekančius veiksmus:

- Įvertina operandus iš kairės į dešinę.
- Kiekvieną operandą paverčia į loginę vertę. Jeigu rezultatas yra `true`, sustoja ir grąžina orginalią operando vertę.
- Jeigu visi operandai įvertinti (pvz. visi buvo `false`), grąžinamas paskutinis operandas.

Vertė grąžinama savo originalioje formoje be konversijos.

Kitaip sakant ARBA `"||"` grandinė grąžina pirmąją truthy vertę arba pačią paskutinę vertę, jeigu teisinga vertė nebuvo rasta.

Pavyzdžiui:

```js run
alert( 1 || 0 ); // 1 (1 yra truthy)
alert( true || 'nesvarbu kas' ); // (true yra truthy)

alert( null || 1 ); // 1 (1 yra pirmoji truthy vertė)
alert( null || 0 || 1 ); // 1 (pirmoji truthy vertė)
alert( undefined || null || 0 ); // 0 (visos falsy, grąžinama paskutinė vertė)
```

Tai veda prie labai įdomių panaudojimo būdų, lyginant su "grynu, klasikiniu, loginiu ARBA".

1. **Gaunant pirmą truthy vertę iš kintamųjų ar išraiškų sąrašo.**

    Įsivaizduokite, kad turime sąrašą kintamųjų, kuriuose arba yra duomenys arba `null/undefined`. Kaip mums surasti pirmąjį su duomenimis?

    Galime naudoti ARBA `||`:

    ```js run
    let currentUser = null;
    let defaultUser = "John";

    *!*
    let name = currentUser || defaultUser || "bevardis";
    */!*

    alert( name ); // pasirenka "John" – pirmąją truthy vertę
    ```

    Jeigu abu `currentUser` ir `defaultUser` būtų falsy, rezultatas būtų `"bevardis"`.
2. **Supaprastintas įvertinimas.**

    Operandai gali būti ne tik vertės, bet ir sutartinės išraiškos. ARBA juos įvertina ir testuoja iš kairės į dešinę. Įvertinimas sustoja kai pasiekiama truthy vertė ir ta vertė sugrąžinama. Toks procesas yra vadinamas "supaprastintu įvertinimu" (ang. "a short-circuit evaluation"), nes jis vyksta taip trumpai iš kairės į dešinę kaip tik įmanoma.

    Tai labai akivaizdu kai išraiška, duota kaip antras argumentas, turi tokį šalutinį efektą kaip kintamojo priskyrimą.

    Pavyzdyje žemiau `x` nėra priskiriamas:

    ```js run no-beautify
    let x;

    *!*true*/!* || (x = 1);

    alert(x); // undefined, nes (x = 1) nėra įvertinamas
    ```

    Tačiau jeigu pirmas argumentas yra `false`, `||` įvertina antrąjį, tada įvykdomas priskyrimas:

    ```js run no-beautify
    let x;

    *!*false*/!* || (x = 1);

    alert(x); // 1
    ```

    Asignavimas yra paprastas atvejis. Tam gali būti šalutinių efektų, kurie nepasirodys, jeigu įvertinimas jų nepasieks.

    Kaip matote toks naudojimo atvejis yra "trumpesnis būdas" su `if`". Pirmasis operandas paverčiamas logine verte, antrasis įvertinamas.

    Dažniausiai, geriau naudoti "įprastinį" `if`, kad kodas būtų lengviau įskaitomas, bet kartais toks būdas gali būti naudingas.

## && (IR)

IR operatorių atstovauja du ampersandai `&&`:

```js
result = a && b;
```

Klasikiniame programavime, IR grąžina `true` tik tokiu atveju kai abu operandai yra arba truthy, arba `false`:

```js run
alert( true && true );   // true
alert( false && true );  // false
alert( true && false );  // false
alert( false && false ); // false
```

Pavyzdys su `if`:

```js run
let hour = 12;
let minute = 30;

if (hour == 12 && minute == 30) {
  alert( 'Dabar yra 12:30' );
}
```

Taip kaip ir su ARBA, bet kokia vertė gali būti IR operandu:

```js run
if (1 && 0) { // įvertintas kaip true && false
  alert( "neveiks, nes rezultatas yra falsy" );
}
```


## IR "&&" suranda pirmą falsy vertę

Turint daug AND verčių:

```js
result = value1 && value2 && value3;
```

Operatorius IR `&&` veikia sekančiai:

- Įvertina operandus iš kairės į dešinę.
- Kiekvieną operandą paverčia į loginę vertę. Jeigu rezultatas yra `false`, sustoja ir grąžina originalią operando vertę.
- Jeigu visi operandai buvo įvertinti (pvz. visi buvo truthy), grąžina paskutinį operandą.

Kitais žodžiais IR grąžina pirmą falsy vertę arba jeigu tokių nerado, pačią paskutinę vertę.

Taisklės aukščiau yra panašios į ARBA. Skirtumas toks, kad IR grąžina pirmą *falsy* vertę kai tuo tarpu ARBA grąžina pirmą *truthy* vertę.

Pavyzdžiai:

```js run
// if the first operand is truthy,
// AND returns the second operand:
alert( 1 && 0 ); // 0
alert( 1 && 5 ); // 5

// if the first operand is falsy,
// AND returns it. The second operand is ignored
alert( null && 5 ); // null
alert( 0 && "no matter what" ); // 0
```

We can also pass several values in a row. See how the first falsy one is returned:

```js run
alert( 1 && 2 && null && 3 ); // null
```

When all values are truthy, the last value is returned:

```js run
alert( 1 && 2 && 3 ); // 3, the last one
```

````smart header="Precedence of AND `&&` is higher than OR `||`"
The precedence of AND `&&` operator is higher than OR `||`.

So the code `a && b || c && d` is essentially the same as if the `&&` expressions were in parentheses: `(a && b) || (c && d)`.
````

Just like OR, the AND `&&` operator can sometimes replace `if`.

For instance:

```js run
let x = 1;

(x > 0) && alert( 'Greater than zero!' );
```

The action in the right part of `&&` would execute only if the evaluation reaches it. That is, only if `(x > 0)` is true.

So we basically have an analogue for:

```js run
let x = 1;

if (x > 0) {
  alert( 'Greater than zero!' );
}
```

The variant with `&&` appears shorter. But `if` is more obvious and tends to be a little bit more readable.

So we recommend using every construct for its purpose: use `if` if we want if and use `&&` if we want AND.

## ! (NOT)

The boolean NOT operator is represented with an exclamation sign `!`.

The syntax is pretty simple:

```js
result = !value;
```

The operator accepts a single argument and does the following:

1. Converts the operand to boolean type: `true/false`.
2. Returns the inverse value.

For instance:

```js run
alert( !true ); // false
alert( !0 ); // true
```

A double NOT `!!` is sometimes used for converting a value to boolean type:

```js run
alert( !!"non-empty string" ); // true
alert( !!null ); // false
```

That is, the first NOT converts the value to boolean and returns the inverse, and the second NOT inverses it again. In the end, we have a plain value-to-boolean conversion.

There's a little more verbose way to do the same thing -- a built-in `Boolean` function:

```js run
alert( Boolean("non-empty string") ); // true
alert( Boolean(null) ); // false
```

The precedence of NOT `!` is the highest of all logical operators, so it always executes first, before `&&` or `||`.
