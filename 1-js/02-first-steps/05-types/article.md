# Duomenų tipai

<<<<<<< HEAD
Kintamasis JavaScript gali savyje laikyti bet kokius duomenis. Kintamasis gali vienu momentu būti eilutė, o kitu numeris:
=======
A value in JavaScript is always of a certain type. For example, a string or a number.

There are eight basic data types in JavaScript. Here, we'll cover them in general and in the next chapters we'll talk about each of them in detail.

We can put any type in a variable. For example, a variable can at one moment be a string and then store a number:
>>>>>>> b09e38c5573346c401a9f9f7410b4ff9be5f4115

```js
// no error
let message = "labas";
message = 123456;
```

<<<<<<< HEAD
Programinės kalbos, kurios tai leidžia yra vadinamos "dinamiškai tipizuotomis" (ang. "dynamically typed"), tai reiškia, kad duomenų tipai yra, tačiau kintamieji nėra prie jų pririšti.

JavaScript turi septynis pagrindinius duomenų tipus. Čia mes juos peržvelgsime bendrai, o tolesniuose skyriuose apie kiekvieną pakalbėsime detaliau.

## Skaičius
=======
Programming languages that allow such things, such as JavaScript, are called "dynamically typed", meaning that there exist data types, but variables are not bound to any of them.

## Number
>>>>>>> b09e38c5573346c401a9f9f7410b4ff9be5f4115

```js
let n = 123;
n = 12.345;
```

*Skaičiaus* tipas atstovauja sveikus skaičius (ang. integer) ir slankiojo kablelio skaičius (ang. floating point numbers).

Netrūksta veiksmų skaičiams, kaip pavyzdžiui daugyba `*`, dalyba `/`, sudėtis `+`, atimtis `-`, ir taip toliau.

Kartu su įprastiniais skaičiais, yra taip vadinamos "specialios skaitinės reikšmės", kurios taip pat priklauso šiam duomenų tipui: `Infinity`, `-Infinity` ir `NaN`.

- `Infinity` atstovauja matematinę [begalybę](https://en.wikipedia.org/wiki/Infinity) ∞. Tai speciali reikšmė, kuri yra didesnė nei bet koks skaičius. 

    Ją gauname kaip rezultatą kai daliname iš nulio:

    ```js run
    alert( 1 / 0 ); // Infinity
    ```

    Arba kai tiesiogiai nurodome:

    ```js run
    alert( Infinity ); // Infinity
    ```
- `NaN` atstovauja skaičiavimo klaidą. Tai yra neteisingo ar neapibrėžto (ang. undefined) matematinio veiksmo rezultatas, pavyzdžiui:

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

<<<<<<< HEAD
## Eilutė
=======
## BigInt [#bigint-type]

In JavaScript, the "number" type cannot represent integer values larger than <code>(2<sup>53</sup>-1)</code> (that's `9007199254740991`), or less than <code>-(2<sup>53</sup>-1)</code> for negatives. It's a technical limitation caused by their internal representation.

For most purposes that's quite enough, but sometimes we need really big numbers, e.g. for cryptography or microsecond-precision timestamps.

`BigInt` type was recently added to the language to represent integers of arbitrary length.

A `BigInt` value is created by appending `n` to the end of an integer:

```js
// the "n" at the end means it's a BigInt
const bigInt = 1234567890123456789012345678901234567890n;
```

As `BigInt` numbers are rarely needed, we don't cover them here, but devoted them a separate chapter <info:bigint>. Read it when you need such big numbers.


```smart header="Compatibility issues"
Right now, `BigInt` is supported in Firefox/Chrome/Edge/Safari, but not in IE.
```

You can check [*MDN* BigInt compatibility table](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/BigInt#Browser_compatibility) to know which versions of a browser are supported.

## String
>>>>>>> b09e38c5573346c401a9f9f7410b4ff9be5f4115

Eilutė JavaScript turi būti apsupta kabutėmis.

```js
<<<<<<< HEAD
let str = "Labas";
let str2 = 'Viengubos kabutės taip pat tinka';
let phrase = `galima įterpti ${str}`;
=======
let str = "Hello";
let str2 = 'Single quotes are ok too';
let phrase = `can embed another ${str}`;
>>>>>>> b09e38c5573346c401a9f9f7410b4ff9be5f4115
```

JavaScript turi 3-ų tipų kabutes.

1. Dvigubos kabutės: `"Hello"`.
2. Viengubos kabutės: `'Hello'`.
3. Atvirkštinės kabutės: <code>&#96;Labas&#96;</code>.

<<<<<<< HEAD
Dvigubos ir viengubos kabutės yra "paprastosios" kabutės. Tarp jų nėra jokio skirtumo JavaScript.
=======
Double and single quotes are "simple" quotes. There's practically no difference between them in JavaScript.
>>>>>>> b09e38c5573346c401a9f9f7410b4ff9be5f4115

Atvirkštinės kabutės yra kabutės su "išplėstu funkcionalumu". Jos leidžia mums įterpti kintamuosius ir išraiškas į pačią eilutę kai apsupame juos tokiais ženklais `${…}`, pavyzdžiui:

```js run
let name = "John";

// įterpti kintamąjį
alert( `Labas, *!*${name}*/!*!` ); // Labas, John!

// įterpti išraišką
alert( `rezultas yra *!*${1 + 2}*/!*` ); // rezultatas yra 3
```

Išraiška viduje `${…}` yra įvertinama ir rezultatas tampa eilutės dalimi. Mes galime įterpti bet ką: tokį kintamąjį kaip `name` arba aritmetinę išraišką kaip `1 + 2` arba ką nors dar sudėtingesnio.

Atkreipkite dėmesį, kad tai galima padaryti tik su atvirkštinėmis kabutėmis. Kitos kabutės neturi tokio įterpimo funkcionalumo!
```js run
alert( "rezultatas yra ${1 + 2}" ); // rezultatas yra ${1 + 2} (dvigubos kabutės nieko nepadaro)
```

Mes kalbėsime daugiau apie eilutes skyriuje <info:string>.

<<<<<<< HEAD
```smart header="Nėra tokio tipo kaip *ženklas*."
Kai kuriose kalbose yra specialus "ženklo" (ang. character) tipas skirtas vienetiniam ženklui. Pavyzdžiui tokiose kalbose kaip C arba Java toks ženklas yra vadinamas `char`.

JavaScript tokio tipo nėra. Yra tik vienas tipas: `string`(eilutė). Eilutė gali būti sudaryta iš vieno ženklo arba iš daug ženklų.
```

## Loginis tipas
=======
```smart header="There is no *character* type."
In some languages, there is a special "character" type for a single character. For example, in the C language and in Java it is called "char".

In JavaScript, there is no such type. There's only one type: `string`. A string may consist of zero characters (be empty), one character or many of them.
```

## Boolean (logical type)
>>>>>>> b09e38c5573346c401a9f9f7410b4ff9be5f4115

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

JavaScript `null` nėra "nuoroda į neegzistuojantį objektą" arba į "nulinę užuomeną" (ang. "null pointer") kaip kai kuriose kitose kalbose.

Tai tik speciali vertė, kuri atstovauja "nieką", "tuštumą" arba "vertė nežinoma".

<<<<<<< HEAD
Kodas viršuje reiškia, kad `age` nėra žinomas arba tuščias dėl neaiškios priežasties.
=======
The code above states that `age` is unknown.
>>>>>>> b09e38c5573346c401a9f9f7410b4ff9be5f4115

## Vertė "undefined"

Ypatingoji vertė `undefined` (neapibrėžtas) taip pat yra išskirtinė, nes turi savo pačios tipą kaip ir `null`.

`undefined` reškia, kad "vertė nėra priskirta".

Jeigu kintamasis deklaruotas, bet nepriskirtas, tada jo vertė yra `undefined`:

```js run
let age;

<<<<<<< HEAD
alert(x); // parodo "undefined"
```

Techniškai yra įmanoma priskirti `undefined` vertę bet kuriam kintamajam:
=======
alert(age); // shows "undefined"
```

Technically, it is possible to explicitly assign `undefined` to a variable:
>>>>>>> b09e38c5573346c401a9f9f7410b4ff9be5f4115

```js run
let age = 100;

// change the value to undefined
age = undefined;

alert(age); // "undefined"
```

<<<<<<< HEAD
...Bet mes nerekomenduojame to daryti. Dažniausiai tam, kad priskirtume "tuščią" ar "nežinomą" vertę kintamajam, mes naudojame `null`, o `undefined` naudojame patikrinimams ar kintamajam buvo priskirta vertė.
=======
...But we don't recommend doing that. Normally, one uses `null` to assign an "empty" or "unknown" value to a variable, while `undefined` is reserved as a default initial value for unassigned things.
>>>>>>> b09e38c5573346c401a9f9f7410b4ff9be5f4115

## Objektai ir Simboliai

Objekto `object` tipas yra ypatingas.

<<<<<<< HEAD
Visi kiti tipai vadinami "primityviais", nes jų vertė gali turėti tik vieną dalyką (nesvarbu ar tai eilutė, numeris ar kita). Tuo tarpu objektai naudojami saugoti duomenų kolekcijas ir daug sudėtingesnius darinius. Apie juos kalbėsime vėliau skyriuje <info:object> kai sužinosime daugiau apie primityvius tipus. 

Simbolio `symbol` tipas yra skirtas sukurti unikalius identifikatorius skirtus objektams. Paminėjome juos tik dėl užbaigtumo, bet labiau juos studijuosime po objektų. 
=======
All other types are called "primitive" because their values can contain only a single thing (be it a string or a number or whatever). In contrast, objects are used to store collections of data and more complex entities.

Being that important, objects deserve a special treatment. We'll deal with them later in the chapter <info:object>, after we learn more about primitives.

The `symbol` type is used to create unique identifiers for objects. We have to mention it here for the sake of completeness, but also postpone the details till we know objects.
>>>>>>> b09e38c5573346c401a9f9f7410b4ff9be5f4115

## Operatorius typeof [#type-typeof]

Operatorius `typeof` grąžina argumento tipą. Jis naudingas kai mes norime išskirtinai apdoroti skirtingų tipų vertes arba norime greitai patikrinti tipą. 

Jis palaiko dviejų formų sintaksę:

1. Kaip operatorius: `typeof x`.
2. Kaip funkcija: `typeof(x)`.

Kitais žodžiais, jis veikia su skliausteliais ar be jų. Rezultatas toks pats.

Šaukimas `typeof x` grąžina eilutę su tipo pavadinimu:

```js
typeof undefined // "undefined"

typeof 0 // "number"

typeof 10n // "bigint"

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

Paskutinės trys eilės gali reikalauti papildomo paaiškinimo:

<<<<<<< HEAD
1. `Math` yra įrašyta (ang. built-in) matematinė operacija. Apie ją sužinosime skyriuje <info:number>. Čia ji yra tik kaip objekto pavyzdys.
2. Rezultatas iš `typeof null` yra `"object"`. Tai nėra tiesa. Tai yra oficialiai pripažinta `typeof` klaida, palikta dėl suderinamumo. Žinoma, kad `null` nėra objektas. Tai yra ypatinga vertė su atskiru tipu. Tad dar kartą, tai yra kalbos klaida.
3. Rezultatas iš `typeof alert` yra `"function"`, nes `alert` ir yra funkcija. Funkcijas studijuosime sekančiuose skyriuose kur sužinosime, kad JavaScript neturi atskiro ypatingo "funkcijos" tipo. Funkcijos priklauso prie objekto tipo. Bet `typeof` jas vertina kitaip, grąžindamas `"function"`. Tai nėra visiškai teisinga, bet praktiškai labai patogu.

=======
1. `Math` is a built-in object that provides mathematical operations. We will learn it in the chapter <info:number>. Here, it serves just as an example of an object.
2. The result of `typeof null` is `"object"`. That's an officially recognized error in `typeof` behavior, coming from the early days of JavaScript and kept for compatibility. Definitely, `null` is not an object. It is a special value with a separate type of its own.
3. The result of `typeof alert` is `"function"`, because `alert` is a function. We'll study functions in the next chapters where we'll also see that there's no special "function" type in JavaScript. Functions belong to the object type. But `typeof` treats them differently, returning `"function"`. That also comes from the early days of JavaScript. Technically, such behavior isn't correct, but can be convenient in practice.
>>>>>>> b09e38c5573346c401a9f9f7410b4ff9be5f4115

## Santrauka

<<<<<<< HEAD
JavaScript turi 7 pagrindinius duomenų tipus.

- `number` skirta bet kokio tipo skaičiams: sveikiems ir slankiojančio kablelio skaičiams.
- `string` skirta eilutėms. Eilutė gali turėti vieną ar daugiau ženklų, nėra atskiro vieno-ženklo tipo.
- `boolean` skirta `true`/`false`.
- `null` skirta nežinomoms vertėms -- atskiras tipas turintis tik vieną vertę `null`.
- `undefined` nepriskirtoms vertėms -- atskiras tipas turintis vieną vertę `undefined`.
- `object` skirta sudėtingesnėms duomenų struktūroms.
- `symbol` skirta unikaliems identifikatoriams.
=======
There are 8 basic data types in JavaScript.

- `number` for numbers of any kind: integer or floating-point, integers are limited by <code>±(2<sup>53</sup>-1)</code>.
- `bigint` is for integer numbers of arbitrary length.
- `string` for strings. A string may have zero or more characters, there's no separate single-character type.
- `boolean` for `true`/`false`.
- `null` for unknown values -- a standalone type that has a single value `null`.
- `undefined` for unassigned values -- a standalone type that has a single value `undefined`.
- `object` for more complex data structures.
- `symbol` for unique identifiers.
>>>>>>> b09e38c5573346c401a9f9f7410b4ff9be5f4115

Operatorius `typeof` leidžia matyti, kuris tipas yra saugomas kintamajame. 

- Dvi formos: `typeof x` arba `typeof(x)`.
- Grąžina eilutę su tipo pavadinimu, kaip pavyzdžiui `"string"`.
- Kai yra `null` grąžina `"object"` -- klaida kalboje, nes tai iš tikrųjų nėra objektas.

Kituose skyriuose susikoncentruosime prie primityvių verčių, o kai su jomis būsime pažįstami, pereisime prie objektų.
