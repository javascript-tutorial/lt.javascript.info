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

1. **Getting the first truthy value from a list of variables or expressions.**

    Imagine we have a list of variables which can either contain data or be `null/undefined`. How can we find the first one with data?

    We can use OR `||`:

    ```js run
    let currentUser = null;
    let defaultUser = "John";

    *!*
    let name = currentUser || defaultUser || "unnamed";
    */!*

    alert( name ); // selects "John" – the first truthy value
    ```

    If both `currentUser` and `defaultUser` were falsy, `"unnamed"` would be the result.
2. **Short-circuit evaluation.**

    Operands can be not only values, but arbitrary expressions. OR evaluates and tests them from left to right. The evaluation stops when a truthy value is reached, and the value is returned. This process is called "a short-circuit evaluation" because it goes as short as possible from left to right.

    This is clearly seen when the expression given as the second argument has a side effect like a variable assignment.

    In the example below, `x` does not get assigned:

    ```js run no-beautify
    let x;

    *!*true*/!* || (x = 1);

    alert(x); // undefined, because (x = 1) not evaluated
    ```

    If, instead, the first argument is `false`, `||` evaluates the second one, thus running the assignment:

    ```js run no-beautify
    let x;

    *!*false*/!* || (x = 1);

    alert(x); // 1
    ```

    An assignment is a simple case. There may be side effects, that won't show up if the evaluation doesn't reach them.

    As we can see, such a use case is a "shorter way of doing `if`". The first operand is converted to boolean. If it's false, the second one is evaluated.

    Most of time, it's better to use a "regular" `if` to keep the code easy to understand, but sometimes this can be handy.

## && (AND)

The AND operator is represented with two ampersands `&&`:

```js
result = a && b;
```

In classical programming, AND returns `true` if both operands are truthy and `false` otherwise:

```js run
alert( true && true );   // true
alert( false && true );  // false
alert( true && false );  // false
alert( false && false ); // false
```

An example with `if`:

```js run
let hour = 12;
let minute = 30;

if (hour == 12 && minute == 30) {
  alert( 'The time is 12:30' );
}
```

Just as with OR, any value is allowed as an operand of AND:

```js run
if (1 && 0) { // evaluated as true && false
  alert( "won't work, because the result is falsy" );
}
```


## AND "&&" finds the first falsy value

Given multiple AND'ed values:

```js
result = value1 && value2 && value3;
```

The AND `&&` operator does the following:

- Evaluates operands from left to right.
- For each operand, converts it to a boolean. If the result is `false`, stops and returns the original value of that operand.
- If all operands have been evaluated (i.e. all were truthy), returns the last operand.

In other words, AND returns the first falsy value or the last value if none were found.

The rules above are similar to OR. The difference is that AND returns the first *falsy* value while OR returns the first *truthy* one.

Examples:

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
