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

Išraiška viduje `${…}` yra įvertinama ir rezultatas tampa eilutės dalimi. Mes galime įterpti bet ką: tokį kintamąjį kaip `name` arba aritmetinę išraišką kaip `1 + 2` arba ką nors dar sudėtingesnio.

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

JavaScript `null` nėra "nuoroda į neegzistuojantį objektą" arba į "nulinę užuomeną" (ang. "null pointer") kaip kai kuriose kitose kalbose.

Tai tik speciali vertė, kuri atstovauja "nieką", "tuštumą" arba "vertė nežinoma".

Kodas viršuje reiškia, kad `age` nėra žinomas arba tuščias dėl neaiškios priežasties.

## Vertė "undefined"

Ypatingoji vertė `undefined` (neapibrėžtas) taip pat yra išskirtinė, nes turi savo pačios tipą kaip ir `null`.

`undefined` reškia, kad "vertė nėra priskirta".

Jeigu kintamasis deklaruotas, bet nepriskirtas, tada jo vertė yra `undefined`:

```js run
let x;

alert(x); // parodo "undefined"
```

Techniškai yra įmanoma priskirti `undefined` vertę bet kuriam kintamajam:

```js run
let x = 123;

x = undefined;

alert(x); // "undefined"
```

...Bet mes nerekomenduojame to daryti. Dažniausiai tam, kad priskirtume "tuščią" ar "nežinomą" vertę kintamajam, mes naudojame `null`, o `undefined` naudojame patikrinimams ar kintamajam buvo priskirta vertė.

## Objektai ir Simboliai

Objekto `object` tipas yra ypatingas.

Visi kiti tipai vadinami "primityviais", nes jų vertė gali turėti tik vieną dalyką (nesvarbu ar tai eilutė, numeris ar kita). Tuo tarpu objektai naudojami saugoti duomenų kolekcijas ir daug sudėtingesnius darinius. Apie juos kalbėsime vėliau skyriuje <info:object> kai sužinosime daugiau apie primityvius tipus. 

Simbolio `symbol` tipas yra skirtas sukurti unikalius identifikatorius skirtus objektams. Paminėjome juos tik dėl užbaigtumo, bet labiau juos studijuosime po objektų. 

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

1. `Math` yra įrašyta (ang. built-in) matematinė operacija. Apie ją sužinosime skyriuje <info:number>. Čia ji yra tik kaip objekto pavyzdys.
2. Rezultatas iš `typeof null` yra `"object"`. Tai nėra tiesa. Tai yra oficialiai pripažinta `typeof` klaida, palikta dėl suderinamumo. Žinoma, kad `null` nėra objektas. Tai yra ypatinga vertė su atskiru tipu. Tad dar kartą, tai yra kalbos klaida.
3. Rezultatas iš `typeof alert` yra `"function"`, nes `alert` ir yra funkcija. Funkcijas studijuosime sekančiuose skyriuose kur sužinosime, kad JavaScript neturi atskiro ypatingo "funkcijos" tipo. Funkcijos priklauso prie objekto tipo. Bet `typeof` jas vertina kitaip, grąžindamas `"function"`. Tai nėra visiškai teisinga, bet praktiškai labai patogu.


## Santrauka

JavaScript turi 7 pagrindinius duomenų tipus.

- `number` skirta bet kokio tipo skaičiams: sveikiems ir slankiojančio kablelio skaičiams.
- `string` skirta eilutėms. Eilutė gali turėti vieną ar daugiau ženklų, nėra atskiro vieno-ženklo tipo.
- `boolean` skirta `true`/`false`.
- `null` skirta nežinomoms vertėms -- atskiras tipas turintis tik vieną vertę `null`.
- `undefined` nepriskirtoms vertėms -- atskiras tipas turintis vieną vertę `undefined`.
- `object` skirta sudėtingesnėms duomenų struktūroms.
- `symbol` skirta unikaliems identifikatoriams.

Operatorius `typeof` leidžia matyti, kuris tipas yra saugomas kintamajame. 

- Dvi formos: `typeof x` arba `typeof(x)`.
- Grąžina eilutę su tipo pavadinimu, kaip pavyzdžiui `"string"`.
- Kai yra `null` grąžina `"object"` -- klaida kalboje, nes tai iš tikrųjų nėra objektas.

Kituose skyriuose susikoncentruosime prie primityvių verčių, o kai su jomis būsime pažįstami, pereisime prie objektų.
