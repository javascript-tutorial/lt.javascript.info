# Palyginimai

Iš matematikos mes žinome daug palyginimo operatorių:

- Daugiau/mažiau negu: <code>a &gt; b</code>, <code>a &lt; b</code>.
- Daugiau/mažiau arba lygu negu: <code>a &gt;= b</code>, <code>a &lt;= b</code>.
- Lygu: `a == b` (atkreipkite dėmesį į dvigubos lygybės ženklą `=`. Vienas ženklas `a = b` reikštų priskyrimą).
- Nelygus. Matematikos toks ženklas yra <code>&ne;</code>, bet JavaScript jis rašomas kaip asigmentas su šauktuku prieš jį: <code>a != b</code>.

## Loginė vertė yra rezultatas

Kaip ir visi kiti operatoriai, palyginimas grąžina vertę. Šiuo atvejuta vertė yra loginė.

- `true` -- reiškia "taip", "teisingai" arba "tiesa".
- `false` -- reiškia "ne", "neteisingai" arba "netiesa".

Pavyzdžiui:

```js run
alert( 2 > 1 );  // true (teisingai)
alert( 2 == 1 ); // false (neteisingai)
alert( 2 != 1 ); // true (teisingai)
```

Palyginimo rezultatas gali būti priskirtas kintamajam, kaip ir bet kuri kita vertė:

```js run
let result = 5 > 4; // priskirti palyginimo rezultato vertę
alert( result ); // true
```

## Eilutės palyginimas

Kad patikrintų ar viena eilutė yra didesnė už kitą, JavaScript naudoja taip vadinamą "žodyno" arba "leksikografinį" eiliškumą

Kitais žodžiais, eilutės yra lyginamos paraidžiui.

Pavyzdžiui:

```js run
alert( 'Z' > 'A' ); // true
alert( 'Glow' > 'Glee' ); // true
alert( 'Bee' > 'Be' ); // true
```

Algoritmas eilučių palyginimui yra labai paprastas:

1. Palyginti abiejų eilučių pirmus ženklus.
2. Jeigu pirmas ženklas iš pirmos eilutės yra didesnis (ar mažesnis) negu kitos eilutės, tada pirma eilutė yra didesnį (ar mažesnė) už antrąją. Pabaiga.
3. Kitu atveju, jeigu abiejų eilučių pirmi ženklai yra vienodi, tada lyginami antri ženklai tuo pačiu principu.
4. Pakartoti iki vienos iš eilučių pabaigos.
5. Jeigu abi eilutės baigiasi tuo pačiu metu, jos yra vienodo. Kitu atveju ilgesnė eilutė yra didesnė.

Pavyzdyje aukščiau, palyginimas `'Z' > 'A'` gauna atsakymą pirmame žingsnyje, kai tuo tarpu `"Glow"` ir `"Glee"` yra lyginami ženklas po ženklo:

1. `G` tas pats kaip `G`.
2. `l` tas pats kaip `l`.
3. `o` yra didesnis nei `e`. Čia sustojame. Pirma eilutė yra didesnė.

```smart header="Ne tikras žodynas, bet Unicode eiliškumas"
Palyginimo algorimtas esantis aukščiau yra maždaug panašus į tokį koks naudojamas žodynuose ir telefonų knygoje, tačiau jis nėra visiškai toks pats.

Pavyzdžiui svarbu ar raidės yra mažosios ar didžiosios. Didžioji raidė `"A"` nėra lygi mažajai raidei `"a"`. Kuri yra didesnė? Mažoji `"a"`. Kodėl? Nes mažosios raidės turi aukštesnį indeksą vidinėje JavaScript kodavimo lentelėje (Unicode). Mes sugrįšime prie specifinių detalių ir pasekmių skyriuje <info:string>.
```

## Skirtingų tipų palyginimai

JavaScript lygindama skirtingų tipų vertes, jas paverčia į skaičius.

Pavyzdžiui:

```js run
alert( '2' > 1 ); // true, eilutė '2' tampa skaičiumi 2
alert( '01' == 1 ); // true, eilutė '01' tampa skaičiumi 1
```

Loginėse vertėse, `true` tampa `1`, o `false` tampa `0`.

Pavyzdžiui:

```js run
alert( true == 1 ); // true
alert( false == 0 ); // true
```

````smart header="Linksmas sutapimas"
Ar įmanoma, kad tuo pačiu metu:

- Dvi vertės yra vienodos.
- Kaip loginė vertė viena iš jų yra `true`, o kita yra `false`.

Pavyzdžiui:

```js run
let a = 0;
alert( Boolean(a) ); // false

let b = "0";
alert( Boolean(b) ); // true

alert(a == b); // true!
```

Iš JavaScript pozicijos, toks rezultatas yra visiškai normalus. Palyginimas paverčia vertes naudodamas skaičių konversijas (tad `"0"` tampa `0`), o tuo tarpu išskirtinė loginė `Boolean` konversija naudoja kitokias taisykles.
````

## Griežta lygybė

Įprastinės lygybės patikrinimas `==` turi problemą. Ji negali atskirti `0` nuo `false`:

```js run
alert( 0 == false ); // true
```

Tas pats nutinka su tuščia eilutė:

```js run
alert( '' == false ); // true
```

Taip nutinka dėl to, kad skirtingų tipų operandai naudojant lygybės operatorių `==` yra paverčiami į skaičius. Tuščia eilutė, taip pat kaip ir `false`, tampa nuliu. 

Ką daryti jeigu mes norime, kad `0` skirtųsi nuo `false`?

**Griežtos lygybės operatorius `===` patikrina lygybę nedarydamas tipo konversijos.**

Kitaip sakant, jeigu `a` ir `b` yra skirtingų tipų, tada `a === b` iš karto grąžina `false` net nebandydama jų konvertuoti.

Pabandykime:

```js run
alert( 0 === false ); // false, nes tipai yra skirtingi
```

Taip pat yra ir "griežtos nelygybės" operatorius `!==` analogiškas `!=`.

Griežtos lygybės operatorius yra ilgesnis, bet jis padeda kodui atrodyti aiškesniu ir palieka mažiau vietos klaidoms. 

## Palyginimai su null ir undefined

There's a non-intuitive behavior when `null` or `undefined` are compared to other values.

For a strict equality check `===`
: These values are different, because each of them is a different type.

    ```js run
    alert( null === undefined ); // false
    ```

For a non-strict check `==`
: There's a special rule. These two are a "sweet couple": they equal each other (in the sense of `==`), but not any other value.

    ```js run
    alert( null == undefined ); // true
    ```

For maths and other comparisons `< > <= >=`
: `null/undefined` are converted to numbers: `null` becomes `0`, while `undefined` becomes `NaN`.

Now let's see some funny things that happen when we apply these rules. And, what's more important, how to not fall into a trap with them.

### Strange result: null vs 0

Let's compare `null` with a zero:

```js run
alert( null > 0 );  // (1) false
alert( null == 0 ); // (2) false
alert( null >= 0 ); // (3) *!*true*/!*
```

Mathematically, that's strange. The last result states that "`null` is greater than or equal to zero", so in one of the comparisons above it must be `true`, but they are both false.

The reason is that an equality check `==` and comparisons `> < >= <=` work differently. Comparisons convert `null` to a number, treating it as `0`. That's why (3) `null >= 0` is true and (1) `null > 0` is false.

On the other hand, the equality check `==` for `undefined` and `null` is defined such that, without any conversions, they equal each other and don't equal anything else. That's why (2) `null == 0` is false.

### An incomparable undefined

The value `undefined` shouldn't be compared to other values:

```js run
alert( undefined > 0 ); // false (1)
alert( undefined < 0 ); // false (2)
alert( undefined == 0 ); // false (3)
```

Why does it dislike zero so much? Always false!

We get these results because:

- Comparisons `(1)` and `(2)` return `false` because `undefined` gets converted to `NaN` and `NaN` is a special numeric value which returns `false` for all comparisons.
- The equality check `(3)` returns `false` because `undefined` only equals `null`, `undefined`, and no other value.

### Evade problems

Why did we go over these examples? Should we remember these peculiarities all the time? Well, not really. Actually, these tricky things will gradually become familiar over time, but there's a solid way to evade problems with them:

Just treat any comparison with `undefined/null` except the strict equality `===` with exceptional care.

Don't use comparisons `>= > < <=` with a variable which may be `null/undefined`, unless you're really sure of what you're doing. If a variable can have these values, check for them separately.

## Summary

- Comparison operators return a boolean value.
- Strings are compared letter-by-letter in the "dictionary" order.
- When values of different types are compared, they get converted to numbers (with the exclusion of a strict equality check).
- The values `null` and `undefined` equal `==` each other and do not equal any other value.
- Be careful when using comparisons like `>` or `<` with variables that can occasionally be `null/undefined`. Checking for `null/undefined` separately is a good idea.
