# Loginiai operatoriai

<<<<<<< HEAD
JavaScript yra trys loginiai operatoriai: `||` (OR - arba), `&&` (AND - ir), `!` (NOT - ne).
=======
There are four logical operators in JavaScript: `||` (OR), `&&` (AND), `!` (NOT), `??` (Nullish Coalescing). Here we cover the first three, the `??` operator is in the next article.
>>>>>>> 8d04d0d2db97276dbb2b451c30a7bd3e05d65831

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

Galime paleisti ir daugiau sąlygų:

```js run
let hour = 12;
let isWeekend = true;

if (hour < 10 || hour > 18 || isWeekend) {
  alert( 'Ofisas uždarytas.' ); // nes savaitgalis
}
```

<<<<<<< HEAD
## ARBA "||" suranda pirmąją truthy vertę
=======
## OR "||" finds the first truthy value [#or-finds-the-first-truthy-value]
>>>>>>> 8d04d0d2db97276dbb2b451c30a7bd3e05d65831

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

<<<<<<< HEAD
Kitaip sakant ARBA `"||"` grandinė grąžina pirmąją truthy vertę arba pačią paskutinę vertę, jeigu teisinga vertė nebuvo rasta.
=======
In other words, a chain of OR `||` returns the first truthy value or the last one if no truthy value is found.
>>>>>>> 8d04d0d2db97276dbb2b451c30a7bd3e05d65831

Pavyzdžiui:

```js run
<<<<<<< HEAD
alert( 1 || 0 ); // 1 (1 yra truthy)
alert( true || 'nesvarbu kas' ); // (true yra truthy)

alert( null || 1 ); // 1 (1 yra pirmoji truthy vertė)
alert( null || 0 || 1 ); // 1 (pirmoji truthy vertė)
alert( undefined || null || 0 ); // 0 (visos falsy, grąžinama paskutinė vertė)
=======
alert( 1 || 0 ); // 1 (1 is truthy)

alert( null || 1 ); // 1 (1 is the first truthy value)
alert( null || 0 || 1 ); // 1 (the first truthy value)

alert( undefined || null || 0 ); // 0 (all falsy, returns the last value)
>>>>>>> 8d04d0d2db97276dbb2b451c30a7bd3e05d65831
```

Tai veda prie labai įdomių panaudojimo būdų, lyginant su "grynu, klasikiniu, loginiu ARBA".

1. **Gaunant pirmą truthy vertę iš kintamųjų ar išraiškų sąrašo.**

<<<<<<< HEAD
    Įsivaizduokite, kad turime sąrašą kintamųjų, kuriuose arba yra duomenys arba `null/undefined`. Kaip mums surasti pirmąjį su duomenimis?

    Galime naudoti ARBA `||`:
=======
    For instance, we have `firstName`, `lastName` and `nickName` variables, all optional (i.e. can be undefined or have falsy values).

    Let's use OR `||` to choose the one that has the data and show it (or `"Anonymous"` if nothing set):
>>>>>>> 8d04d0d2db97276dbb2b451c30a7bd3e05d65831

    ```js run
    let firstName = "";
    let lastName = "";
    let nickName = "SuperCoder";

    *!*
<<<<<<< HEAD
    let name = currentUser || defaultUser || "bevardis";
    */!*

    alert( name ); // pasirenka "John" – pirmąją truthy vertę
    ```

    Jeigu abu `currentUser` ir `defaultUser` būtų falsy, rezultatas būtų `"bevardis"`.
2. **Supaprastintas įvertinimas.**

    Operandai gali būti ne tik vertės, bet ir sutartinės išraiškos. ARBA juos įvertina ir testuoja iš kairės į dešinę. Įvertinimas sustoja kai pasiekiama truthy vertė ir ta vertė sugrąžinama. Toks procesas yra vadinamas "supaprastintu įvertinimu" (ang. "a short-circuit evaluation"), nes jis vyksta taip trumpai iš kairės į dešinę kaip tik įmanoma.

    Tai labai akivaizdu kai išraiška, duota kaip antras argumentas, turi tokį šalutinį efektą kaip kintamojo priskyrimą.

    Pavyzdyje žemiau `x` nėra priskiriamas:
=======
    alert( firstName || lastName || nickName || "Anonymous"); // SuperCoder
    */!*
    ```

    If all variables were falsy, `"Anonymous"` would show up.

2. **Short-circuit evaluation.**

    Another feature of OR `||` operator is the so-called "short-circuit" evaluation.
>>>>>>> 8d04d0d2db97276dbb2b451c30a7bd3e05d65831

    It means that `||` processes its arguments until the first truthy value is reached, and then the value is returned immediately, without even touching the other argument.

    The importance of this feature becomes obvious if an operand isn't just a value, but an expression with a side effect, such as a variable assignment or a function call.

<<<<<<< HEAD
    alert(x); // undefined, nes (x = 1) nėra įvertinamas
    ```

    Tačiau jeigu pirmas argumentas yra `false`, `||` įvertina antrąjį, tada įvykdomas priskyrimas:
=======
    In the example below, only the second message is printed:
>>>>>>> 8d04d0d2db97276dbb2b451c30a7bd3e05d65831

    ```js run no-beautify
    *!*true*/!* || alert("not printed");
    *!*false*/!* || alert("printed");
    ```

<<<<<<< HEAD
    Asignavimas yra paprastas atvejis. Tam gali būti šalutinių efektų, kurie nepasirodys, jeigu įvertinimas jų nepasieks.

    Kaip matote toks naudojimo atvejis yra "trumpesnis būdas" nei `if`". Pirmasis operandas paverčiamas logine verte, antrasis įvertinamas.

    Vis dėlto dažniausiai, geriau naudoti "įprastinį" `if`, kad kodas būtų lengviau įskaitomas, bet kartais toks būdas gali būti naudingas.
=======
    In the first line, the OR `||` operator stops the evaluation immediately upon seeing `true`, so the `alert` isn't run.

    Sometimes, people use this feature to execute commands only if the condition on the left part is falsy.
>>>>>>> 8d04d0d2db97276dbb2b451c30a7bd3e05d65831

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

Turint daug IR verčių:

```js
result = value1 && value2 && value3;
```

Operatorius IR `&&` veikia sekančiai:

- Įvertina operandus iš kairės į dešinę.
- Kiekvieną operandą paverčia į loginę vertę. Jeigu rezultatas yra `false`, sustoja ir grąžina originalią operando vertę.
- Jeigu visi operandai buvo įvertinti (pvz. visi buvo truthy), grąžina paskutinį operandą.

Kitais žodžiais IR grąžina pirmą falsy vertę arba jeigu tokių nerado, pačią paskutinę vertę.

Taisyklės aukščiau yra panašios į ARBA. Skirtumas toks, kad IR grąžina pirmą *falsy* vertę kai tuo tarpu ARBA grąžina pirmą *truthy* vertę.

Pavyzdžiai:

```js run
// jeigu pirmasis operandas yra truthy,
// IR grąžins antrąjį operandą:
alert( 1 && 0 ); // 0
alert( 1 && 5 ); // 5

// jeigu pirmasis operandas yra falsy,
// IR jį grąžins. Antrasis operandas ignoruojamas
alert( null && 5 ); // null
alert( 0 && "nesvarbu kas" ); // 0
```

Mes taip pat galime praleisti kelias vertes iš eilės. Atkreipkite dėmesį kaip yra grąžinamas pirmasis falsy:

```js run
alert( 1 && 2 && null && 3 ); // null
```

Kai visos vertės yra truthy, grąžinama paskutinė vertė:

```js run
alert( 1 && 2 && 3 ); // 3, paskutinis
```

````smart header="IR `&&` pirmenybė yra aukštesnė už ARBA `||`"
IR `&&` operatoriaus pirmenybė yra aukštesnė už ARBA `||`.

Tad kodas `a && b || c && d` būtų tas pats lyg `&&` išraiškos būtų tarp skliaustelių: `(a && b) || (c && d)`.
````

<<<<<<< HEAD
Taip pat kaip ir ARBA, operatorius IR `&&` kartais gali pakeisti `if`.
=======
````warn header="Don't replace `if` with `||` or `&&`"
Sometimes, people use the AND `&&` operator as a "shorter way to write `if`".
>>>>>>> 8d04d0d2db97276dbb2b451c30a7bd3e05d65831

Pavyzdžiui:

```js run
let x = 1;

(x > 0) && alert( 'Didesnis nei nulis!' );
```

Veiksmas dešinėje `&&` pusėję įvyktų tik tokiu atveju jeigu įvertinimas jį pasiektų. Tai yra, jeigu `(x > 0)` yra tiesa.

Tad mes tiesiog turime analogą šiai išraiškai:

```js run
let x = 1;

<<<<<<< HEAD
if (x > 0) {
  alert( 'Didesnis nei nulis!' );
}
```

Variantas su `&&` atrodo trumpesnis. Bet `if` yra labiau akivaizdus ir dėl to yra geriau įskaitomas.

Mes rekomenduojame naudoti kiekvieną konstruktą pagal paskirtį: naudokite `if` jeigu norite if, o `&&` jeigu norite IR.
=======
if (x > 0) alert( 'Greater than zero!' );
```

Although, the variant with `&&` appears shorter, `if` is more obvious and tends to be a little bit more readable. So we recommend using every construct for its purpose: use `if` if we want `if` and use `&&` if we want AND.
````

>>>>>>> 8d04d0d2db97276dbb2b451c30a7bd3e05d65831

## ! (NE)

Loginis NE operatorius yra atsotvaujamas šauktuko ženklo `!`.

Sintaksė paprasta:

```js
result = !value;
```

Operatorius priima vieną argumentą ir atlieka sekančius veiksmus:

1. Konvertuoja operatorių į loginę vertę: `true/false`.
2. Grąžina atvirkštinę vertę.

Pavyzdžiui:

```js run
alert( !true ); // false
alert( !0 ); // true
```

Dvigubas NE `!!` kartais naudojamas, kad paverstų vertę į loginį tipą:

```js run
alert( !!"ne tuščia eilutė" ); // true
alert( !!null ); // false
```

Tai yra, pirmasis NE paverčia vertę į loginę ir grąžina atvirkštinį variantą, o antrasis NE jį atverčia atgalios. Galų gale turime paprastą konversiją į loginę vertę.

Yra kiek mažiau žodžių reikalaujantis kelias, kuris daro tą patį -- iš anksto paruošta loginė `Boolean` funkcija:

```js run
alert( Boolean("ne tuščia eilutė") ); // true
alert( Boolean(null) ); // false
```

Pirmenybė NE `!` yra aukščiausia iš visų loginių operatorių, tad jis visada įvykdomas pirmiau nei `&&` ar `||`.
