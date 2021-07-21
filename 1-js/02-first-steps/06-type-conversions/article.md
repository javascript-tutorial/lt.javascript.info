# Tipų konversijos 

Dažniausiai operatoriai ir funkcijos automatiškai pakeičia jiems duotas vertes į teisingą tipą. 

Pavyzdžiui `alert` automatiškai paverčia bet kokią jiems duotą vertę į eilutės tipą, kad galėtų jį parodytų. Matematinės operacijos pakeičia vertes į skaičius.

Yra tokių konkrečių atvejų kai mums reikia vertę pakeisti į atitinkamą tipą.

```smart header="Dar nekalbame apie objektus"
Šiame skyriuje kol kas dar nekalbėsime apie objektus. Vietoje to studijuosime primityvius tipus. Vėliau kai sužinosime daugiau apie objektus, pamatysime kaip objektų keitimai veikia skyriuje <info:object-toprimitive>.
```

## Eilutės konversijos

Eilutės keitimas įvyksta tada kai mums reikia eilutės formos vertės.

Pavyzdžiui, `alert(value)` tai padaro, kad parodytų vertę.

Mes taip pat galime iššaukti `String(value)` funkciją, kad konvertuotume vertę į eilutę:

```js run
let value = true;
alert(typeof value); // boolean (loginis)

*!*
value = String(value); // dabar vertė yra eilutė "true"
alert(typeof value); // string
*/!*
```

Eilutės konversijos dažniausiai yra labai akivaizdžios. `false` tampa `"false"`, `null` tampa `"null"` ir t.t.

## Skaičių konversijos

Skaičių konversijos įvyksta automatiškai matematinėse funkcijose ir formulėse. 

Pavyzdžiui, kai dalyba `/` taikoma ne skaičiams:

```js run
alert( "6" / "2" ); // 3, eilutės paverčiamos skaičiais
```

Mes taip pat galime naudoti `Number(value)` funkciją konkrečiai tam, kad paverstume `value` į skaičių:

```js run
let str = "123";
alert(typeof str); // string

let num = Number(str); // tampa numeriu 123

alert(typeof num); // number
```

Akivaizdžios konversijos dažniausiai reikalingos kai gauname vertę eilutės tipo formatu iš tekstinių šaltinių, bet mums iš tikrųjų reikalingas skaičius. 

Jeigu eilutė nėra tinkamas skaičius, tada tokios konversijos rezultatas bus is `NaN`. Pavyzdžiui:

```js run
let age = Number("arbitriška eilutė vietoje skaičiaus");

alert(age); // NaN, konversija nepavyko
```

Skaičių konversijos taisyklės:

| Vertė |  Tampa... |
|-------|-------------|
|`undefined`|`NaN`|
|`null`|`0`|
|<code>true&nbsp;ir&nbsp;false</code> | `1` ir `0` |
| `string` | Tarpai pradžioje ir pabaigoje panaikinami. Jeigu likusi eilutė yra tuščia, rezultatas yra `0`. Kitu atveju, skaičius "perskaitomas" iš eilutės. Klaida grąžina `NaN`. |

Pavyzdžiai:

```js run
alert( Number("   123   ") ); // 123
alert( Number("123z") );      // NaN (klaida perskaitė skaičiuje "z")
alert( Number(true) );        // 1
alert( Number(false) );       // 0
```

Atkreipkite dėmesį, kad `null` ir `undefined` elgiasi kitaip šiuo atveju: `null` tampa nuliu kai `undefined` tampa `NaN`.

````smart header="Sudėtis '+' sujungia eilutes"
Beveik visos matematinės operacijos paverčia vertes numeriais. A notable exception is addition `+`. If one of the added values is a string, the other one is also converted to a string.

Then, it concatenates (joins) them:

```js run
alert( 1 + '2' ); // '12' (string to the right)
alert( '1' + 2 ); // '12' (string to the left)
```

This only happens when at least one of the arguments is a string. Otherwise, values are converted to numbers.
````

## Boolean Conversion

Boolean conversion is the simplest one.

It happens in logical operations (later we'll meet condition tests and other similar things) but can also be performed explicitly with a call to `Boolean(value)`.

The conversion rule:

- Values that are intuitively "empty", like `0`, an empty string, `null`, `undefined`, and `NaN`, become `false`.
- Other values become `true`.

For instance:

```js run
alert( Boolean(1) ); // true
alert( Boolean(0) ); // false

alert( Boolean("hello") ); // true
alert( Boolean("") ); // false
```

````warn header="Please note: the string with zero `\"0\"` is `true`"
Some languages (namely PHP) treat `"0"` as `false`. But in JavaScript, a non-empty string is always `true`.

```js run
alert( Boolean("0") ); // true
alert( Boolean(" ") ); // spaces, also true (any non-empty string is true)
```
````

## Summary

The three most widely used type conversions are to string, to number, and to boolean.

**`String Conversion`** -- Occurs when we output something. Can be performed with `String(value)`. The conversion to string is usually obvious for primitive values.

**`Numeric Conversion`** -- Occurs in math operations. Can be performed with `Number(value)`.

The conversion follows the rules:

| Value |  Becomes... |
|-------|-------------|
|`undefined`|`NaN`|
|`null`|`0`|
|<code>true&nbsp;/&nbsp;false</code> | `1 / 0` |
| `string` | The string is read "as is", whitespaces from both sides are ignored. An empty string becomes `0`. An error gives `NaN`. |

**`Boolean Conversion`** -- Occurs in logical operations. Can be performed with `Boolean(value)`.

Follows the rules:

| Value |  Becomes... |
|-------|-------------|
|`0`, `null`, `undefined`, `NaN`, `""` |`false`|
|any other value| `true` |


Most of these rules are easy to understand and memorize. The notable exceptions where people usually make mistakes are:

- `undefined` is `NaN` as a number, not `0`.
- `"0"` and space-only strings like `"   "` are true as a boolean.

Objects aren't covered here. We'll return to them later in the chapter <info:object-toprimitive> that is devoted exclusively to objects after we learn more basic things about JavaScript.
