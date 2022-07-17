# JavaScript ypatumai

Šiame skyriuje trumpai apžvelgiamos iki šiol išmoktos JavaScript savybės, ypatingą dėmesį skiriant subtiliems momentams.

## Kodo struktūra

Teiginiai atskiriami kabliataškiu:

```js run no-beautify
alert('Labas'); alert('Pasauli');
```

Paprastai eilutės laužimas taip pat laikomas skiriamuoju ženklu, todėl jis taip pat tiktų:

```js run no-beautify
alert('Hello')
alert('World')
```

Tai vadinama “automatiniu kabliataškio įterpimu”. Kartais tai neveikia, pavyzdžiui:

```js run
alert("Po šio pranešimo pasirodys klaida")

[1, 2].forEach(alert)
```

Dauguma kodų stiliaus vadovų sutinka, kad po kiekvieno teiginio turėtume dėti kabliataškį.

Po kodo blokų `{...}` ir sintaksės konstrukcijų su jais, pvz., ciklų, kabliataškiai nereikalingi:

```js
function f() {
  // po funkcijos deklaravimo nereikia kabliataškio
}

for(;;) {
  // po ciklo nereikia kabliataškio
}
```

...Tačiau net jei kur nors galime įterpti papildomą kabliataškį, tai nėra klaida. Tai bus ignoruojama.

Išsamiau: <info:structure>.

## Griežtas režimas

Kad būtų įjungtos visos šiuolaikinės JavaScript ypatybės, skriptus turėtume pradėti nuo `"use strict"`.

```js
'use strict';

...
```

Ši direktyva turi būti skripto viršuje arba funkcijos kūno pradžioje.

Be `"use strict"` viskas veikia, tačiau kai kurios funkcijos veikia senamadiškai, “suderinamumo” būdu. Apskritai mums labiau tiktų šiuolaikinis elgesys.

Kai kurios šiuolaikinės kalbos savybės (pvz., klasės, kurias nagrinėsime ateityje) įgalina griežtąjį režimą netiesiogiai.

Išsamiau: <info:strict-mode>.

## Kintamieji

Galima deklaruoti naudojant:

- `let`
- `const` (konstanta, negali būti pakeista)
- `var` (pasenęs būdas, daugiau informacijos vėliau)

Kintamojo pavadinimas gali apimti:
- Raidės ir skaitmenys, tačiau pirmasis simbolis negali būti skaitmuo.
- Greta raidžių naudojami simboliai `$` ir `_`.
- Leidžiami ir nelotyniški simboliai bei hieroglifai, tačiau paprastai jie nenaudojami.

Kintamieji yra dinamiškai tipizuojami. Juose galima saugoti bet kokią vertę:

```js
let x = 5;
x = "Jonas";
```

Yra 8 duomenų tipai:

- `number` sveikiesiems ir realiesiems skaičiams,
- `bigint` darbui su savavališkai ilgais sveikaisiais skaičiais,
- `string` eilutėms,
- `boolean` loginėms vertėms: `true/false`,
- `null` -- tipas su vienintele verte `null`, reiškiančia “tuščias” arba “neegzistuoja”,
- `undefined` -- tipas su vienintele verte `undefined`, reiškiančia "nepriskirtas",
- `object` ir `symbol` -- sudėtingoms duomenų struktūroms ir unikaliems identifikatoriams, jų dar nesimokome.

Operatorius `typeof` grąžina vertės tipą, išskyrus dvi išimtis:
```js
typeof null == "object" // kalbos klaida
typeof function(){} == "function" // funkcijos traktuojamos ypatingai
```

Išsamiau: <info:variables> ir <info:types>.

## Interakcija su lankytoju

Kaip darbo aplinką naudojame naršyklę, todėl pagrindinės vartotojo sąsajos funkcijos bus:

[`prompt(question, [default])`](mdn:api/Window/prompt)
: Užduoti klausimą `question` ir grąžinti lankytojo įvestus duomenis arba `null`, jei lankytojas paspaudė “atšaukti”.

[`confirm(question)`](mdn:api/Window/confirm)
: Užduoti klausimą `question` ir pasiūlyti pasirinkti tarp “OK” ir “Atšaukti”. Pasirinkimas grąžinamas kaip `true/false`.

[`alert(message)`](mdn:api/Window/alert)
: Išvesti pranešimą `message`.

Visos šios funkcijos yra *modalinės*, jos sustabdo kodo vykdymą ir neleidžia lankytojui sąveikauti su puslapiu, kol jis neatsakys.

Pavyzdžiui:

```js run
let userName = prompt("Jūsų vardas?", "Alisa");
let isTeaWanted = confirm("Ar norite arbatos?");

alert( "Lankytojas: " + userName ); // Alisa
alert( "Norėjo arbatos: " + isTeaWanted ); // true
```

Išsamiau: <info:alert-prompt-confirm>.

## Operatoriai

JavaScript palaiko šiuos operatorius:

Aritmetikos
: Įprasti: `* + - /`, taip pat `%` skirtas dalybos likučiui gauti ir `**` skirtas pakėlimui laipsniu.

    Binarinis pliusas `+` sujungia eilutes. Jei kuris nors iš operandų yra eilutė, kitas operandas taip pat paverčiamas eilute:

    ```js run
    alert( '1' + 2 ); // '12', eilutė
    alert( 1 + '2' ); // '12', eilutė
    ```

Priskyrimo operatoriai
: Yra paprastas priskyrimas: `a = b` ir kombinuotas, pavyzdžiui, `a *= 2`.

Bitų operacijos
: Bitų operatoriai su 32 bitų sveikaisiais skaičiais dirba žemiausiu, bitų lygiu. Daugiau apie jų galite perskaityti [MDN](mdn:/JavaScript/Guide/Expressions_and_Operators#Bitwise).

Sąlyginiai operatoriai
: Vienintelis operatorius, turintis tris parametrus: `cond ? resultA : resultB`. Jeigu `cond` yra truthy, grąžina `resultA`, priešingu atveju `resultB`.

Loginiai operatoriai
: Loginiai IR `&&` ir ARBA `||` atlieka trumpąjį apdorojimą ir grąžina vertę, kurioje jie sustojo (nebūtinai `true`/`false`). Loginis NE `!` konvertuoja operandą į loginį tipą ir grąžina atvirkštinę vertę.

Nulinio susiliejimo operatorius.
: Operatorius `??` suteikia galimybę pasirinkti apibrėžtą vertę iš kintamųjų sąrašo. Rezultatas `a ?? b` yra `a`, išskyrus atvejus, kai `a` yra `null/undefined`, tada `b`.

Palyginimas
: Įvairių tipų verčių lygybės patikrinimas `==` paverčia jas skaičiumi (išskyrus `null` ir `undefined`, kurios lygios viena kitai ir niekam kitam), todėl toliau pateikti pavyzdžiai yra lygūs:

    ```js run
    alert( 0 == false ); // true
    alert( 0 == '' ); // true
    ```

    Kiti palyginimai taip pat konvertuojami į skaičių.

    Griežtosios lygybės operatorius `===` neatlieka konvertavimo: skirtingi tipai jam visada reiškia skirtingas vertes.

    Vertės `null` ir `undefined` yra ypatingos: jos lygios `==` viena kitai ir nėra lygios niekam kitam.

    Daugiau/mažiau palyginimo operatoriai palygina eilutes simbolis po simbolio, kiti tipai konvertuojami į skaičius.

Kiti operatoriai
: Yra keletas kitų operatorių, pavyzdžiui, kablelio operatorius.

Išsamiau: <info:operators>, <info:comparison>, <info:logical-operators>, <info:nullish-coalescing-operator>.

## Ciklai

- Mes apžvelgėme 3 tipų ciklus:

    ```js
    // 1
    while (condition) {
      ...
    }

    // 2
    do {
      ...
    } while (condition);

    // 3
    for(let i = 0; i < 10; i++) {
      ...
    }
    ```

- Kintamasis, deklaruotas `for(let...)` cikle, yra matomas tik ciklo viduje. Tačiau taip pat galime praleisti `let` ir pakartotinai panaudoti egzistuojantį kintamąjį.
- Direktyvos `break/continue` leidžia išeiti iš viso ciklo/dabartinės iteracijos. Naudokite žymas norėdami išeiti iš įdėtų ciklų.

Išsamiau: <info:while-for>.

Vėliau mes nagrinėsime daugiau ciklų, skirtų darbui su objektais.

## “switch” konstrukcija

Konstrukcija “switch” gali pakeisti kelis `if` patikrinimus. Palyginimui naudojama `===` (griežta lygybė).

Pavyzdžiui:

```js run
let age = prompt('Jūsų amžius?', 18);

switch (age) {
  case 18:
    alert("neveikia"); // prompt rezultatas yra eilutė, o ne skaičius
    break;

  case "18":
    alert("Tai veikia!");
    break;

  default:
    alert("Bet kuri vertė, nelygi vienai iš aukščiau nurodytų verčių");
}
```

Išsamiau: <info:switch>.

## Funkcijos

Mes apžvelgėme tris būdus, kaip galima sukurti funkciją JavaScript:

1. Funkcijos deklaravimas: funkcija pagrindiniame kodo sraute

    ```js
    function sum(a, b) {
      let result = a + b;

      return result;
    }
    ```

2. Function Expression: funkcija išraiškos kontekste

    ```js
    let sum = function(a, b) {
      let result = a + b;

      return result;
    };
    ```

3. Rodyklės funkcijos (ang. *“arrow functions”*):

    ```js
    // išraiška dešinėje pusėje
    let sum = (a, b) => a + b;

    // kelių eilučių kodas figūriniuose skliaustuose { ... }, čia reikalingas return:
    let sum = (a, b) => {
      // ...
      return a + b;
    }

    // be argumentų
    let sayHi = () => alert("Hello");

    // su vienu argumentu
    let double = n => n * 2;
    ```


- Funkcijos gali turėti lokalinius kintamuosius: tuos, kurie yra deklaruoti jų viduje arba jų parametrų sąraše. Tokie kintamieji matomi tik funkcijos viduje.
- Parametrai gali turėti numatytąsias vertes: `function sum(a = 1, b = 2) {...}`.
- Funkcijos visada ką nors grąžina. Jei nėra teiginio `return`, rezultatas yra `undefined`.

Išsamiau: <info:function-basics>, <info:arrow-functions-basics>.

## Toliau mes išmoksime daugiau

Tai buvo trumpas JavaScript funkcijų sąrašas. Kol kas susipažinome tik su pagrindais. Toliau vadovėlyje jūs rasite daugiau specialiųjų ir išplėstinių JavaScript funkcijų.