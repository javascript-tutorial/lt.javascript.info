# Tipų konversijos 

<<<<<<< HEAD:1-js/02-first-steps/06-type-conversions/article.md
Dažniausiai operatoriai ir funkcijos automatiškai pakeičia jiems duotas vertes į teisingą tipą. 
=======
Most of the time, operators and functions automatically convert the values given to them to the right type.
>>>>>>> eda333d423db8ade41f75d2e2d30ea06c7d997ef:1-js/02-first-steps/07-type-conversions/article.md

Pavyzdžiui `alert` automatiškai paverčia bet kokią jiems duotą vertę į eilutės tipą, kad galėtų jį parodytų. Matematinės operacijos pakeičia vertes į skaičius.

Yra tokių konkrečių atvejų kai mums reikia vertę pakeisti į atitinkamą tipą.

<<<<<<< HEAD:1-js/02-first-steps/06-type-conversions/article.md
```smart header="Dar nekalbame apie objektus"
Šiame skyriuje kol kas dar nekalbėsime apie objektus. Vietoje to studijuosime primityvius tipus. Vėliau kai sužinosime daugiau apie objektus, pamatysime kaip objektų keitimai veikia skyriuje <info:object-toprimitive>.
=======
```smart header="Not talking about objects yet"
In this chapter, we won't cover objects. For now we'll just be talking about primitives.

Later, after we learn about objects, in the chapter <info:object-toprimitive> we'll see how objects fit in.
>>>>>>> eda333d423db8ade41f75d2e2d30ea06c7d997ef:1-js/02-first-steps/07-type-conversions/article.md
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

<<<<<<< HEAD:1-js/02-first-steps/06-type-conversions/article.md
````smart header="Sudėtis '+' sujungia eilutes"
Beveik visos matematinės operacijos paverčia vertes numeriais. Svarbi išimtis yra sudėtis `+`. Jeigu viena iš verčių yra eilutės, kita taip pat paverčiama eilute.

Tada ji sujungia (ang. concatenates) vertes:

```js run
alert( 1 + '2' ); // '12' (eilutė iš dešinės)
alert( '1' + 2 ); // '12' (eilutė iš kairės)
```

Taip įvyksta tik tokiu atveju kai vienas iš argumentų yra eilutė. Kitu atveju vertės konvertuojamos į skaičius.
````
=======
Most mathematical operators also perform such conversion, we'll see that in the next chapter.
>>>>>>> eda333d423db8ade41f75d2e2d30ea06c7d997ef:1-js/02-first-steps/07-type-conversions/article.md

## Loginės konversijos

Loginės konversijos yra pačios paprasčiausios. 

Jos nutinka loginėse operacijose (vėliau dar matysime padėties testus, ang. condition tests, ir panašius atvejus), bet taip pat gali būti atliekamos akivaizdžiam `Boolean(value)` iškvietimui.

Konversijos taisyklės:

- Vertės kurios intuityviai yra tuščios, kaip `0`, tuščia eilutė, `null`, `undefined` ir `NaN`, tampa `false`.
- Kitos vertės tampa `true`.

Pavyzdžiui:

```js run
alert( Boolean(1) ); // true
alert( Boolean(0) ); // false

alert( Boolean("hello") ); // true
alert( Boolean("") ); // false
```

````warn header="Atkreipkite dėmesė: eilutė su nuliu `\"0\"` yra `true`"
Kai kurios kalbos (pavyzdžiui PHP) `"0"` laiko `false`. Bet JavaScript netuščia eilutė visada bus `true`.

```js run
alert( Boolean("0") ); // true
alert( Boolean(" ") ); // tarpai, taip pat tinka (bet kokia netuščia eilutė yra tinkama - true)
```
````

## Santrauka

Trys labiausiai naudojamos tipų konversijos yra į eilutę, skaičių ir loginiai.

**`Eilutės Konversija`** -- Nutinka kai mes kažką gauname. Gali būti atliekama su `String(value)`. Konversija į eilutę su primityviais tipais dažniausiai yra akivaizdi. 

**`Skaičių Konversija`** -- Nutinka matematinėse operacijos. Gali būti atliekama su `Number(value)`.

Konversija laikosi taisyklių:

| Vertė |  Tampa... |
|-------|-------------|
|`undefined`|`NaN`|
|`null`|`0`|
|<code>true&nbsp;/&nbsp;false</code> | `1 / 0` |
| `string` | Eilutė skaitoma taip kaip yra, tarpai iš abiejų pusių ignoruojami. Tuščia eilutė tampa `0`. Klaida grąžina `NaN`. |

**`Loginės Konversijos`** -- Nutinka loginėse operacijose. Gali būti atliekama su `Boolean(value)`.

Laikosi taisyklių:

| Vertė |  Tampa... |
|-------|-------------|
|`0`, `null`, `undefined`, `NaN`, `""` |`false`|
|bet kokia kita vertė| `true` |


Didžiąją dalį šių taisyklių lengva suprasti ir prisiminti. Svarbios išimtys kur žmonės daro klaidas yra:

- `undefined` kaip skaičius yra `NaN` kaip skaičius, ne `0`.
- `"0"` ir eilutė tik su tarpu kaip `"   "` yra tiesa loginėse vertėse.

Objektai čia neaptariami. Prie jų sugrįšime vėliau skyriuje <info:object-toprimitive>, kuris yra skirtas išskirtinai objektams kai tik sužinosime daugiau apie JavaScript.
