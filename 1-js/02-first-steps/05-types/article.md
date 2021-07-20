# Duomenų tipai

Kintamasis JavaScript gali savyje laikyti bet kokius duomenis. Kintamasis gali vienu momentu būti eilutė, o kitu numeris:

```js
// no error
let message = "labas";
message = 123456;
```

Programinės kalbos, kurios tai leidžia yra vadinamos "dinamiškai tipizuotomis" (ang. "dynamically typed"), tai reiškia, kad duomenų tipai yra, tačiau kintamieji nėra prie jų pririšti.

JavaScript turi septynis pagrindinius duomenų tipus. Čia mes juos peržvelgsime bendrai, o tolesniuose skyriuose apie kiekvieną pakalbėsime detaliau.

## Skaičius

```js
let n = 123;
n = 12.345;
```

*Skaičiaus* tipas atstovauja sveikus skaičius (ang. integer) ir slankiojo kablelio skaičius (ang. floating point numbers).

Netrūksta veiksmų skaičiams, kaip pavyzdžiui daugyba `*`, dalyba `/`, sudėtis `+`, atimtis `-`, ir taip toliau.

Kartu su įprastiniais skaičiais, yra taip vadinamos "specialios skaitinės reikšmės", kurios taip pat priklauso šiam duomenų tipui: `Infinity`, `-Infinity` ir `NaN`.

- `Infinity` atstovauja matematinę [Begalybę](https://en.wikipedia.org/wiki/Infinity) ∞. Tai speciali reikšmė, kuri yra didesnė nei bet koks skaičius. 

    Ją gauname kaip rezultatą kai daliname iš nulio:

    ```js run
    alert( 1 / 0 ); // Infinity
    ```

    Arba kai tiesiogiai nurodome:

    ```js run
    alert( Infinity ); // Infinity
    ```
- `NaN` atstovauja skaičiavimo klaidą. Tai yra neteisingo ar neapibrėžto (ang. undefined) mateminio veiksmo rezultatas, pavyzdžiui:

    ```js run
    alert( "ne skaičius" / 2 ); // NaN, tokia dalyba yra klaidinga
    ```

    `NaN` yra kabus. Bet kokie tolesni veiksmai su `NaN` grąžins `NaN`:

    ```js run
    alert( "ne skaičius" / 2 + 5 ); // NaN
    ```

    Taigi, jeigu kažkur matematinėje formulėje yra `NaN` jis persiduoda į visus tolesnius rezultatus.

```smart header="Matematiniai veiksmai yra saugūs"
Užsiimti matematika JavaScript yra "saugu". Galime daryti viską: dalinti iš nulio, elgtis su neskaitinėmis eilutėmis kaip su skaičiais ir t.t.

Skriptas niekada nesustos dėl lemtingos klaidos ("mirs"). Blogiausia kas gali būti, mes gausime `NaN` kaip rezultatą.
```

Specialios skaitinės reikšmės priklauso "skaičių" tipui. Žinoma, jie nėra skaičiai įprastine šio žodžio reikšme.

Daugiau apie darbą su skaičiais bus skyriuje <info:number>.

## Eilutė

Eilutė JavaScript turi būti apsupta kabutėmis.

```js
let str = "Labas";
let str2 = 'Viengubos kabutės taip pat tinka';
let phrase = `galima įterpti ${str}`;
```

JavaScript turi 3-ų tipų kabutes.

1. Dvigubos kabutės: `"Hello"`.
2. Viengubos kabutės: `'Hello'`.
3. Atvirkštinės kabutės: <code>&#96;Labas&#96;</code>.

Dvigubos ir viengubos kabutės yra "paprastosios" kabutės. Tarp jų nėra jokio skirtumo JavaScript.

Atvirkštinės kabutės yra kabutės su "išplėstu funkcionalumu". Jos leidžia mums įterpti kintamuosius ir išraiškas į pačią eilutę kai apsupame juos tokiais ženklais `${…}`, pavyzdžiui:

```js run
let name = "John";

// įterpti kintamąjį
alert( `Labas, *!*${name}*/!*!` ); // Labas, John!

// įterpti išraišką
alert( `rezultas yra *!*${1 + 2}*/!*` ); // rezultatas yra 3
```

Išraiška viduje `${…}` yra įvertinama ir rezultatas tampa eilutės dalimi. Mes galime įdėti bet ką: tokį kintamąjį kaip `name` arba aritmetinę išraišką kaip `1 + 2` arba ką nors dar sudėtingesnio.

Atkreipkite dėmesį, kad tai galima padaryti tik su atvirkštinėmis kabutėmis. Kitos kabutės neturi tokio įterpimo funkcionalumo!
```js run
alert( "rezultatas yra ${1 + 2}" ); // rezultatas yra ${1 + 2} (dvigubos kabutės nieko nepadaro)
```

Mes kalbėsime daugiau apie eilutes skyriuje <info:string>.

```smart header="Nėra tokio tipo kaip *ženklas*."
Kai kuriose kalbose yra specialus "ženklo" (ang. character) tipas skirtas vienetiniam ženklui. Pavyzdžiui tokiose kalbose kaip C arba Java toks ženklas yra vadinamas `char`.

JavaScript tokio tipo nėra. Yra tik vienas tipas: `string`(eilutė). Eilutė gali būti sudaryta iš vieno ženklo arba iš daug ženklų.
```

## Loginis tipas

Loginis tipas (ang. boolean) turi tik dvi reikšmes: `true` (tiesa) ir `false`(netiesa).

Šis tipas dažniausiai naudojamas, kad išsaugotų taip/ne vertes: `true` reiškia "taip, teisingai", o `false` reiškia "ne, netesingai".

Pavyzdžiui:

```js
let nameFieldChecked = true; // taip, vardo laukelis pažymėtas
let ageFieldChecked = false; // ne, amžiaus laukelis nepažymėtas
```

Loginės vertės taip pat yra palyginimų rezultatas:

```js run
let isGreater = 4 > 1;

alert( isGreater ); // tiesa (palyginimo rezultatas yra "taip")
```

Mes daugiau kalbėsime apie loginį tipą skyriuje <info:logical-operators>.

## "null" vertė

Ypatingoji `null` (negaliojanti) vertė nepriklauso jokiam anksčiau minėtam tipui.

Jis formuoja atskirą savo tipą, kuriame yra tik `null` vertė:

```js
let age = null;
```

JavaScript `null` nėra "nuoroda į neegzistuojantį objektą" arba į "nulinę užuomeną" (ang. "null pointer") kaip kai kurios kitos kalbos.

Tai tik speciali vertė, kuri atstovauja "nieką", "tuštumą" arba "vertė nežinoma".

Kodas viršuje reiškia, kad `age` nėra žinomas arba tuščias dėl neaiškios priežasties.

## The "undefined" value

The special value `undefined` also stands apart. It makes a type of its own, just like `null`.

The meaning of `undefined` is "value is not assigned".

If a variable is declared, but not assigned, then its value is `undefined`:

```js run
let x;

alert(x); // shows "undefined"
```

Technically, it is possible to assign `undefined` to any variable:

```js run
let x = 123;

x = undefined;

alert(x); // "undefined"
```

...But we don't recommend doing that. Normally, we use `null` to assign an "empty" or "unknown" value to a variable, and we use `undefined` for checks like seeing if a variable has been assigned.

## Objects and Symbols

The `object` type is special.

All other types are called "primitive" because their values can contain only a single thing (be it a string or a number or whatever). In contrast, objects are used to store collections of data and more complex entities. We'll deal with them later in the chapter <info:object> after we learn more about primitives.

The `symbol` type is used to create unique identifiers for objects. We mention it here for completeness, but we'll study it after objects.

## The typeof operator [#type-typeof]

The `typeof` operator returns the type of the argument. It's useful when we want to process values of different types differently or just want to do a quick check.

It supports two forms of syntax:

1. As an operator: `typeof x`.
2. As a function: `typeof(x)`.

In other words, it works with parentheses or without them. The result is the same.

The call to `typeof x` returns a string with the type name:

```js
typeof undefined // "undefined"

typeof 0 // "number"

typeof true // "boolean"

typeof "foo" // "string"

typeof Symbol("id") // "symbol"

*!*
typeof Math // "object"  (1)
*/!*

*!*
typeof null // "object"  (2)
*/!*

*!*
typeof alert // "function"  (3)
*/!*
```

The last three lines may need additional explanation:

1. `Math` is a built-in object that provides mathematical operations. We will learn it in the chapter <info:number>. Here, it serves just as an example of an object.
2. The result of `typeof null` is `"object"`. That's wrong. It is an officially recognized error in `typeof`, kept for compatibility. Of course, `null` is not an object. It is a special value with a separate type of its own. So, again, this is an error in the language.
3. The result of `typeof alert` is `"function"`, because `alert` is a function. We'll study functions in the next chapters where we'll also see that there's no special "function" type in JavaScript. Functions belong to the object type. But `typeof` treats them differently, returning `"function"`. That's not quite correct, but very convenient in practice.


## Summary

There are 7 basic data types in JavaScript.

- `number` for numbers of any kind: integer or floating-point.
- `string` for strings. A string may have one or more characters, there's no separate single-character type.
- `boolean` for `true`/`false`.
- `null` for unknown values -- a standalone type that has a single value `null`.
- `undefined` for unassigned values -- a standalone type that has a single value `undefined`.
- `object` for more complex data structures.
- `symbol` for unique identifiers.

The `typeof` operator allows us to see which type is stored in a variable.

- Two forms: `typeof x` or `typeof(x)`.
- Returns a string with the name of the type, like `"string"`.
- For `null` returns `"object"` -- this is an error in the language, it's not actually an object.

In the next chapters, we'll concentrate on primitive values and once we're familiar with them, we'll move on to objects.
