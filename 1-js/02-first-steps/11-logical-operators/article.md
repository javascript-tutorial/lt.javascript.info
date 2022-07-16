# Loginiai operatoriai

JavaScript yra keturi loginiai operatoriai: `||` (ARBA), `&&` (IR), `!` (NE), `??` (Nulinis susiliejimas). Čia apžvelgsime pirmuosius tris, operatorius `??` -- kitame straipsnyje.

Nors jie vadinami “loginiais”, juos galima naudoti su bet kokio tipo vertėmis, ne vien loginėmis. Jų rezultatas taip pat gali būti bet kokio tipo.

Pažiūrėkime detaliau.

## || (ARBA)

Dvi vertikalios linijos atstoja “ARBA” operatorių:

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

## ARBA "||" suranda pirmąją truthy vertę [#or-finds-the-first-truthy-value]

Aukščiau apibūdinta logika yra klasikinė. Dabar pridėkime “ekstra” JavaScript savybių.

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

Kitaip tariant, grandinė ARBA `||` grąžina pirmąją truthy vertę arba paskutinę, jei nerandama truthy vertės.

Pavyzdžiui:

```js run
alert( 1 || 0 ); // 1 (1 yra truthy)

alert( null || 1 ); // 1 (1 yra pirmoji truthy vertė)
alert( null || 0 || 1 ); // 1 (pirmoji truthy vertė)

alert( undefined || null || 0 ); // 0 (visos falsy, grąžinama paskutinė vertė)
```

Tai veda prie labai įdomių panaudojimo būdų, lyginant su "grynu, klasikiniu, loginiu ARBA".

1. **Gaunant pirmą truthy vertę iš kintamųjų ar išraiškų sąrašo.**

    Pavyzdžiui, mes turime kintamuosius `firstName`, `lastName` ir `nickName`, kurie visi yra neprivalomi (t. y. gali būti undefined arba turėti falsy reikšmes).

    Naudokime ARBA `||`, kad pasirinktume tą, kuriame yra duomenų, ir jį parodytume (arba `"Anonimas"`, jei nieko nenurodyta):

    ```js run
    let firstName = "";
    let lastName = "";
    let nickName = "SuperCoder";

    *!*
    alert( firstName || lastName || nickName || "Anonimas"); // SuperCoder
    */!*
    ```

    Jei visi kintamieji būtų falsy, būtų rodomas `"Anonimas"`.

2. **Sutrumpintas apskaičiavimas.**

    Kita ARBA `||` operatoriaus savybė yra vadinamasis “sutrumpintas apskaičiavimas”.

    Tai reiškia, kad `||` analizuoja savo argumentus tol, kol pasiekiama pirmoji truthy vertė, o tada ji iš karto grąžinama, net neliečiant kito argumento.

    Šios savybės svarba tampa akivaizdi, jei operandas yra ne tik vertė, bet ir išraiška su šalutiniu poveikiu, pavyzdžiui, kintamojo priskyrimas arba funkcijos iškvietimas.

    Žemiau pateiktame pavyzdyje rodomas tik antrasis pranešimas:

    ```js run no-beautify
    *!*true*/!* || alert("ne rodomas");
    *!*false*/!* || alert("rodomas");
    ```

    Pirmoje eilutėje operatorius ARBA `||` sustabdo apdorojimą iš karto, kai tik pasirodo `true`, todėl `alert` nėra paleidžiamas.

    Kartais žmonės naudojasi šia funkcija, norėdami vykdyti komandas tik tuo atveju, jei kairėje dalyje esanti sąlyga yra falsy.

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


## IR “&&” suranda pirmąją falsy vertę

Turint daug IR verčių:

```js
result = value1 && value2 && value3;
```

Operatorius IR `&&` veikia sekančiai:

- Įvertina operandus iš kairės į dešinę.
- Kiekvieną operandą paverčia į loginę vertę. Jeigu rezultatas yra `false`, sustoja ir grąžina originalią operando vertę.
- Jeigu visi operandai buvo įvertinti (pvz., visi buvo truthy), grąžina paskutinį operandą.

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

````warn header="Nekeiskite `if` į `||` arba `&&`"
Kartais žmonės naudoja operatorių IR `&&` kaip “trumpesnį būdą parašyti `if`”.

Pavyzdžiui:

```js run
let x = 1;

(x > 0) && alert( 'Didesnis nei nulis!' );
```

Veiksmas dešinėje `&&` pusėję įvyktų tik tokiu atveju jeigu įvertinimas jį pasiektų. Tai yra, jeigu `(x > 0)` yra tiesa.

Tad mes tiesiog turime analogą šiai išraiškai:

```js run
let x = 1;

if (x > 0) alert( 'Didesnis nei nulis!' );
```

Nors variantas su `&&` atrodo trumpesnis, `if` yra akivaizdesnis ir šiek tiek skaitomesnis. Taigi rekomenduojame kiekvieną konstrukciją naudoti pagal paskirtį: jei norime `if`, naudojame `if`, o jei norime IR, naudojame `&&`.
````

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
