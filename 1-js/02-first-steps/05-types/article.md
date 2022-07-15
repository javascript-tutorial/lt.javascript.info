# Duomenų tipai

JavaScript vertė visada yra tam tikro tipo. Pavyzdžiui, eilutė arba skaičius.

JavaScript yra aštuoni pagrindiniai duomenų tipai. Čia apžvelgsime juos apskritai, o kituose skyriuose apie kiekvieną iš jų kalbėsime išsamiau.

Į kintamąjį galime įrašyti bet kokį tipą. Pavyzdžiui, vienu metu kintamasis gali būti eilutė, o paskui jame gali būti įrašytas skaičius:

```js
// nėra klaidos
let message = "labas";
message = 123456;
```

Programavimo kalbos, kurios leidžia tokius dalykus, kaip JavaScript, vadinamos "dinamiškai tipizuotomis", tai reiškia, kad egzistuoja duomenų tipai, tačiau kintamieji nėra susieti su jokiais iš jų.

## Number

```js
let n = 123;
n = 12.345;
```

Tipas *number* atstovauja ir sveikuosius, ir slankiojo kablelio skaičius.

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
- `NaN` atstovauja skaičiavimo klaidą. Tai yra neteisingo ar neapibrėžto (ang. *“undefined”*) matematinio veiksmo rezultatas, pavyzdžiui:

    ```js run
    alert( "ne skaičius" / 2 ); // NaN, tokia dalyba yra klaidinga
    ```

    `NaN` yra kabus. Bet kokie tolesni veiksmai su `NaN` grąžins `NaN`:

    ```js run
    alert( NaN + 1 ); // NaN
    alert( 3 * NaN ); // NaN
    alert( "ne skaičius" / 2 - 1 ); // NaN
    ```

    Taigi, jei matematinėje išraiškoje kur nors yra `NaN`, ji persiduoda visam rezultatui (yra tik viena išimtis: `NaN ** 0` yra `1`)

```smart header="Matematiniai veiksmai yra saugūs"
Užsiimti matematika JavaScript yra "saugu". Galime daryti viską: dalinti iš nulio, elgtis su neskaitinėmis eilutėmis kaip su skaičiais ir t.t.

Skriptas niekada nesustos dėl lemtingos klaidos ("mirs"). Blogiausia kas gali būti, mes gausime `NaN` kaip rezultatą.
```

Specialios skaitinės reikšmės priklauso "skaičių" tipui. Žinoma, jie nėra skaičiai įprastine šio žodžio reikšme.

Daugiau apie darbą su skaičiais bus skyriuje <info:number>.

## BigInt [#bigint-type]

JavaScript tipo “number” sudėtyje negali būti skaičių, didesnių už <code>(2<sup>53</sup>-1)</code> (t. y. `9007199254740991`), arba mažesnių nei <code>-(2<sup>53</sup>-1)</code> neigiamiems skaičiams. Šį techninį apribojimą lemia jų vidinė išvaizda.

Tačiau kartais mums reikia tikrai milžiniškų skaičių, pavyzdžiui, kriptografijoje arba naudojant laiko žymą (“timestamp”) su mikrosekundėmis.

Neseniai į kalbą buvo pridėtas `BigInt` tipas, kuriuo galima išreikšti bet kokio ilgio sveikuosius skaičius. 

Norint sukurti `BigInt` vertę, prie skaičiaus pabaigos turite pridėti `n`:

```js
// pabaigoje esanti raidė "n" reiškia, kad tai yra BigInt
const bigInt = 1234567890123456789012345678901234567890n;
```

Kadangi `BigInt` skaičiai reikalingi retai, čia jų neaprašysime, bet skirsime jiems atskirą skyrių <info:bigint>. Jį skaitykite, kai prireiks tokių didelių skaičių.

```smart header="Suderinamumo problemos"
Šiuo metu `BigInt` yra palaikomas Firefox/Chrome/Edge/Safari, bet ne IE.
```

Jūs galite patikrinti [*MDN* BigInt suderinamumo lentelė](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/BigInt#Browser_compatibility) norėdami sužinoti, kurios naršyklės versijos yra palaikomos.

## String

Eilutė (ang. *“String”*) JavaScript turi būti apsupta kabutėmis.

```js
let str = "Labas";
let str2 = 'Viengubos kabutės taip pat tinka';
let phrase = `galima įterpti ${str}`;
```

JavaScript turi 3-ų tipų kabutes.

1. Dvigubos kabutės: `"Labas"`.
2. Viengubos kabutės: `'Labas'`.
3. Atvirkštinės kabutės: <code>&#96;Labas&#96;</code>.

Dvigubos ir viengubos kabutės yra “paprastosios” kabutės. Tarp jų nėra jokio skirtumo JavaScript.

Atvirkštinės kabutės yra kabutės su “išplėstu funkcionalumu”. Jos leidžia mums įterpti kintamuosius ir išraiškas į pačią eilutę kai apsupame juos tokiais ženklais `${…}`, pavyzdžiui:

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
Kai kuriose kalbose yra specialus "ženklo" (ang. *“character”*) tipas skirtas vienetiniam ženklui. Pavyzdžiui, tokiose kalbose kaip C arba Java toks ženklas yra vadinamas `char`.

JavaScript tokio tipo nėra. Yra tik vienas tipas: `string`. Eilutė gali būti sudaryta iš vieno ženklo arba iš daug ženklų.
```

## Boolean (loginis tipas)

`Boolean` tipas turi tik dvi reikšmes: `true` (tiesa) ir `false`(netiesa).

Šis tipas dažniausiai naudojamas, kad išsaugotų taip/ne vertes: `true` reiškia “taip, teisingai”, o `false` reiškia “ne, netesingai”.

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

## “null” vertė

Ypatingoji `null` (negaliojanti) vertė nepriklauso jokiam anksčiau minėtam tipui.

Jis formuoja atskirą savo tipą, kuriame yra tik `null` vertė:

```js
let age = null;
```

JavaScript `null` nėra “nuoroda į neegzistuojantį objektą” arba į “nulinę užuomeną” (ang. *“null pointer”*), kaip kai kuriose kitose kalbose.

Tai tik speciali vertė, kuri atstovauja "nieką", "tuštumą" arba "vertė nežinoma".

Pirmiau pateiktame kode teigiama, kad `age` yra nežinomas.

## Vertė "undefined"

Ypatingoji vertė `undefined` (neapibrėžtas) taip pat yra išskirtinė, nes turi savo pačios tipą kaip ir `null`.

`undefined` reškia, kad “vertė nėra priskirta”.

Jeigu kintamasis deklaruotas, bet nepriskirtas, tada jo vertė yra `undefined`:

```js run
let age;

alert(x); // parodo "undefined"
```

Techniškai yra įmanoma priskirti `undefined` vertę bet kuriam kintamajam:

```js run
let age = 100;

// pakeičia vertę į undefined
age = undefined;

alert(age); // "undefined"
```

...Bet mes nerekomenduojame to daryti. Dažniausiai kintamajam priskirti “tuščią” arba “nežinomą” vertę naudojamas `null`, o `undefined` yra rezervuotas kaip numatytoji pradinė vertė nepriskirtiems dalykams.

## Objektai ir Simboliai

Objekto `object` tipas yra ypatingas.

Visi kiti tipai vadinami "primityviais", nes jų vertės gali turėti tik vieną dalyką (eilutę, skaičių ar kt.). Priešingai, objektai naudojami duomenų rinkiniams ir sudėtingesnėms struktūroms saugoti.

Kadangi objektai yra tokie svarbūs, jie nusipelno ypatingo elgesio. Juos aptarsime vėliau, skyriuje <info:object>, kai daugiau sužinosime apie primityvus.

Tipas `symbol` yra naudojamas unikaliems objektų identifikatoriams sukurti. Turime jį paminėti čia dėl išsamumo, bet taip pat turime atidėti detales, kol susipažinsime su objektais.

## Operatorius typeof [#type-typeof]

Operatorius `typeof` grąžina argumento tipą. Jis naudingas kai mes norime išskirtinai apdoroti skirtingų tipų vertes arba norime greitai patikrinti tipą. 

Iškvietimas `typeof x` grąžina eilutę su tipo pavadinimu:

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

1. `Math` yra integruotas (ang. *“built-in”*) objektas, skirtas matematinėms operacijoms atlikti. Su juo susipažinsime skyriuje <info:number>. Čia jis pasitarnaus tik kaip objekto pavyzdys.
2. `typeof null` rezultatas yra `"object"`. Tai oficialiai pripažinta `typeof` klaida, atsiradusi labai ankstyvaisiais "JavaScript" laikais ir išsaugota dėl suderinamumo. Neabejotinai `null` nėra objektas. Tai speciali reikšmė, turinti atskirą savo tipą. Šiuo atveju `typeof` elgsena yra neteisinga.
3. Rezultatas `typeof alert` yra `"function"`, nes `alert` yra funkcija. Funkcijas nagrinėsime kituose skyriuose, kur taip pat pamatysime, kad JavaScript nėra jokio specialaus `"function"` tipo. Funkcijos priklauso objektų tipui. Tačiau `typeof` su jomis elgiasi kitaip, grąžindamas `"function"`. Tai taip pat atkeliavo iš ankstyvųjų JavaScript laikų. Techniškai toks elgesys nėra teisingas, tačiau praktiškai gali būti patogus.

```smart header="`typeof(x)` sintaksė"
Jūs taip pat galite susidurti su kita sintakse: `typeof(x)`. Ji tokia pati kaip `typeof x`.

Aiškiau tariant, `typeof` yra operatorius, o ne funkcija. Čia esantys skliaustai nėra `typeof` dalis. Tai tokie skliaustai, kurie naudojami matematiniam grupavimui.

Paprastai tokiuose skliausteliuose būna matematinė išraiška, pavyzdžiui, `(2 + 2)`, tačiau čia jie turi tik vieną argumentą `(x)`. Sintaksiškai jie leidžia išvengti tarpo tarp operatoriaus `typeof` ir jo argumento, ir kai kuriems žmonėms tai patinka.

Kai kurie žmonės mėgsta `typeof(x)`, nors `typeof x` sintaksė yra daug dažnesnė.
```

## Santrauka

JavaScript turi 8 pagrindinius duomenų tipus.

- `number` skirtas bet kokio tipo skaičiams: sveikiems ir slankiojančio kablelio skaičiams.
- `bigint` skirtas bet kokio ilgio sveikiesiems skaičiams.
- `string` skirtas eilutėms. Eilutė gali turėti vieną ar daugiau ženklų, nėra atskiro vieno-ženklo tipo.
- `boolean` skirtas `true`/`false`.
- `null` skirtas nežinomoms vertėms -- atskiras tipas turintis tik vieną vertę `null`.
- `undefined` nepriskirtoms vertėms -- atskiras tipas turintis vieną vertę `undefined`.
- `object` skirtas sudėtingesnėms duomenų struktūroms.
- `symbol` skirtas unikaliems identifikatoriams.

Operatorius `typeof` leidžia matyti, kuris tipas yra saugomas kintamajame. 

- Yra dvi formos: `typeof x` ir `typeof(x)`.
- Grąžina eilutę su tipo pavadinimu, kaip pavyzdžiui `"string"`.
- Kai yra `null` grąžina `"object"` -- klaida kalboje, nes tai iš tikrųjų nėra objektas.

Kituose skyriuose susikoncentruosime prie primityvių verčių, o kai su jomis būsime pažįstami, pereisime prie objektų.
