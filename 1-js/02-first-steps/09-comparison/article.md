# Palyginimai

Mes žinome daugybę palyginimo operatorių iš matematikos.

JavaScript kalboje jie užrašomi taip:

- Daugiau/mažiau negu: <code>a &gt; b</code>, <code>a &lt; b</code>.
- Daugiau/mažiau arba lygu negu: <code>a &gt;= b</code>, <code>a &lt;= b</code>.
- Lygu: `a == b`, atkreipkite dėmesį, kad dvigubas lygybės ženklas `==` reiškia lygybės patikrinimą, o viengubas `a = b` reiškia priskyrimą.
- Nelygus: Matematikoje toks ženklas yra <code>&ne;</code>, bet JavaScript jis rašomas kaip priskyrimas su šauktuku prieš jį <code>a != b</code>.

Šiame straipsnyje daugiau sužinosime apie įvairių tipų palyginimus, kaip JavaScript juos atlieka, įskaitant svarbius ypatumus.

Pabaigoje jūs rasite gerą patarimą, kaip išvengti JavaScript palyginimo “keistenybių”.

## Boolean yra rezultatas

Visi palyginimo operatoriai grąžina loginę (Boolean) vertę:

- `true` -- reiškia “taip”, “teisingai” arba “tiesa”.
- `false` -- reiškia “ne”, “neteisingai” arba “netiesa”.

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

Kad patikrintų ar viena eilutė yra didesnė už kitą, JavaScript naudoja taip vadinamą “žodyną” arba “leksikografinį” eiliškumą

Kitais žodžiais, eilutės yra lyginamos paraidžiui.

Pavyzdžiui:

```js run
alert( 'Z' > 'A' ); // true
alert( 'Glow' > 'Glee' ); // true
alert( 'Bee' > 'Be' ); // true
```

Algoritmas eilučių palyginimui yra labai paprastas:

1. Palyginti abiejų eilučių pirmus ženklus.
2. Jeigu pirmas ženklas iš pirmos eilutės yra didesnis (ar mažesnis) negu kitos eilutės, tada pirma eilutė yra didesnė (ar mažesnė) už antrąją. Pabaiga.
3. Kitu atveju, jeigu abiejų eilučių pirmi ženklai yra vienodi, tada lyginami antri ženklai tuo pačiu principu.
4. Pakartoti iki vienos iš eilučių pabaigos.
5. Jeigu abi eilutės baigiasi tuo pačiu metu, jos yra vienodos. Kitu atveju ilgesnė eilutė yra didesnė.

Pirmajame pavyzdyje palyginimas `'Z' > 'A'` duoda rezultatą pirmajame žingsnyje.

Antrojo palyginimo `'Glow'` ir `'Glee'` žingsnių reikia daugiau, nes eilutės lyginamos paraidžiui:

1. `G` tas pats kaip `G`.
2. `l` tas pats kaip `l`.
3. `o` yra didesnis nei `e`. Čia sustojame. Pirma eilutė yra didesnė.

```smart header="Ne tikras žodynas, bet Unicode eiliškumas"
Palyginimo algoritmas esantis aukščiau yra maždaug panašus į tokį koks naudojamas žodynuose ir telefonų knygoje, tačiau jis nėra visiškai toks pats.

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

Taip pat yra ir “griežtos nelygybės” operatorius `!==` analogiškas `!=`.

Griežtos lygybės operatorius yra ilgesnis, bet jis padeda kodui atrodyti aiškesniu ir palieka mažiau vietos klaidoms. 

## Palyginimai su null ir undefined

Kai lyginami`null` ar `undefined`su kitomis vertėmis elgesys nėra intuityvus.

Griežtos lygybės patikrinime `===`
: Šios vertės yra skirtingos, nes kiekviena jų yra skirtingo tipo.

    ```js run
    alert( null === undefined ); // false
    ```

Negriežtos lygybės patikrai `==`
: Yra speciali taisyklė. Šie du yra "saldi porelė": jie yra lygūs vienas kitam (kai yra `==`), bet jokioms kitoms vertėms.

    ```js run
    alert( null == undefined ); // true
    ```

Matematiniuose ir kitokiuose palyginimuose `< > <= >=`
: `null/undefined` yra paverčiami skaičiais: `null` tampa `0`, tuo tarpu `undefined` tampa `NaN`.

Dabar pasižiūrėkime į juokingus atvejus kai šios taisyklės būna pritaikomos. Ir visų svarbiausia kaip dėl jų nepakliūti į spąstus.

### Keistas rezultatas: null vs 0

Palyginkime `null` su nuliu:

```js run
alert( null > 0 );  // (1) false
alert( null == 0 ); // (2) false
alert( null >= 0 ); // (3) *!*true*/!*
```

Tai labai keista matematiškai. Rezultatas sako, kad "`null` yra didesnis arba lygus nuliu", vadinasi viename iš aukščiau esančių palyginimų turėtų būti taip pat `true`, bet jie abu yra neteisingi.

To priežastis yra tai, kad lygybės patikrinimas `==` ir palyginimai `> < >= <=` veikia kitaip. Palyginimai paverčia `null` į skaičių ir laiko jį nuliu `0`. Štai dėl ko (3) `null >= 0` yra tiesa, o `null > 0` yra netiesa.

Iš kitos pusės, lygybės patikrinimas `==` kaip jau yra apibūdinta, `undefined` ir `null` kai jie nėra konvertuojami, jie yra vienas kitam lygūs, bet nelygūs niekam kitam. Štai kodėl (2) `null == 0` yra netiesa.

### Nepalyginimasis undefined

Vertė `undefined` neturėtų būti lyginima su kitomis vertėmis:

```js run
alert( undefined > 0 ); // false (1)
alert( undefined < 0 ); // false (2)
alert( undefined == 0 ); // false (3)
```

Kodėl jis taip nemėgsta nulio? Visada netiesa!

Gauname tokius rezultatas, nes:

- Palyginimai `(1)` ir `(2)` grąžina `false`, nes `undefined` paverčiamas į `NaN`, o `NaN` yra ypatinga skaitinė vertė, kuri visoms vertėms grąžina `false`.
- Lygybės patikrinimas `(3)` grąžina `false`, nes `undefined` yra lygus tik `null`, `undefined` ir jokiai kitai vertei.

### Išvenkite problemų

Kodėl aptarėme šiuos pavyzdžius? Ar turėtume nuolat prisiminti šiuos ypatumus? Na, ne visai. Tiesą sakant, laikui bėgant šie subtilūs dalykai palaipsniui taps įprasti, tačiau yra patikimas būdas išvengti su jais susijusių problemų:

- Bet kokį palyginimą su `undefined/null`, išskyrus griežtos lygybės `===`, atlikite itin atsargiai.
- Nenaudokite palyginimų `>= > > < <=` su kintamuoju, kuris gali būti `null/undefined`, nebent tikrai žinote, ką darote. Jei kintamasis gali turėti šias vertes, tikrinkite jas atskirai.

## Santrauka

- Palyginimų operatoriai grąžina loginę vertę.
- Eilutės yra tikrinamos paraidžiui "žodynėlio" eiliškumo principu.
- Kai lyginamos skirtingų tipų vertės, jos yra paverčiamos į skaičius (išskyrus tik griežtą lygybės patikrinimą).
- Vertės `null` ir `undefined` yra lygios `==` viena kitai, bet nelygios jokiai kitai vertei.
- Būkite atsargūs kai naudojate tokius palyginimus kaip `>` arba `<` su kintamaisiai, kurie laikas nuo laiko gali būti `null/undefined`. Gera mintis yra patikrinti `null/undefined` atskirai.
