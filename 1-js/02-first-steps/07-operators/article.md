# Operatoriai

Mes žinome daug operatorių iš mokyklos. Tokie kaip sudėtis `+`, daugyba `*`, atimtis `-` ir taip toliau.

Šiame skyriuje, susikoncentruosime prie tokio operatorių aspekto, kuris nėra aptariamas mokykloje.

## Terminai: "unary", "binary", "operand"

Prieš tęsiant, išsiaiškinkime įprastinę terminologiją.

- *An operand* -- operandas yra tai kam operatoriai yra naudojami. Pavyzdžiui šioje daugyboje `5 * 2` yra du operandai: kairysis operandas yra `5`, o dešinysis yra `2`. Kartais žmonės juos vadina argumentais, o ne operandais.
- Operatorius yra *unarinis* (ang. *unary*), jeigu turi vieną operandą. Pavyzdžiui unarinis neiginys (ang. negation) `-` paverčia skaičių neigiamu:

    ```js run
    let x = 1;

    *!*
    x = -x;
    */!*
    alert( x ); // -1, pritaikytas unarinis neiginys
    ```
- Operatorius yra *binarinis* (ang. *binary*) kai turi du operandus. Tas pats minusas egzistuoja ir binarinėse formose:

    ```js run no-beautify
    let x = 1, y = 3;
    alert( y - x ); // 2, binarinis minusas atima vertes
    ```

    Formaliai aukščiau esančiame pavyzdyje mes turime du skirtingus operatorius, kurie dalinasi tuo pačiu simboliu: neigimo operatoriumi, t.y. unariniu operatoriumi, kuris pakeičia simbolį, ir atimties operatoriumi, t.y. binarinu operatoriumi, kuris atima vieną skaičių iš kito. 

## Eilutės sujungimas, binarinis +

Dabar susipažinkime su ypatingomis JavaScript savybėmis, kurios pranoksta mokyklos aritmetiką.

Dažniausiai operatorius pliusas `+` sumuoja skaičius.

Bet jeigu binarinis `+` pritaikomas eilutėms, pliusas jas sulieja (sujungia):

```js
let s = "my" + "string";
alert(s); // mystring
```

Atkreipkite dėmesį, jeigu vienas iš operandų yra eilutė, tai kitas taip pat paverčiamas eilute.

Pavyzdžiui:

```js run
alert( '1' + 2 ); // "12"
alert( 2 + '1' ); // "21"
```

Kaip matote nėra svarbu ar pirmasis operandas ar antrasis yra eilutė. Taisyklė paprasta: jeigu bent vienas operandas yra eilutė, kitas taip pat paverčiamas eilute.

Tačiau pastebėkite, kad operacijos vyksta iš kairės į dešinę. Jeigu pirmiau yra du numeriai, kuriuos seka eilutė, numeriai bus susumuoti ir tik tada paversti į eilutę:


```js run
alert(2 + 2 + '1' ); // "41" bet ne "221"
```

Eilutės sujungimas ir konversija yra ypatinga binarinio pliuso savybė `+`. Kiti aritmetiniai operatoriai veikia tik su skaičiais ir visada konvertuoja savo operandus į skaičius.

Pavyzdžiui, atimtis ir dalyba:

```js run
alert( 2 - '1' ); // 1
alert( '6' / '2' ); // 3
```

## Skaitinė konversija, unarinis +

Pliusas `+` egzistuoja dviejose formose: binarinėje formoje, kurią matėme aukščiau ir unarinėje formoje.

Unarinis pliusas arba kitaip sumos operatorius `+`, pritaikytas vienetinei vertei, nieko nedaro skaičiams. Bet jeigu operandas nėra skaičius, unarinis pliusas paverčia jį skaičiumi. 

Pavyzdžiui:

```js run
// Jokio efekto skaičiams
let x = 1;
alert( +x ); // 1

let y = -2;
alert( +y ); // -2

*!*
// Paverčia ne skaičius į skaičius
alert( +true ); // 1
alert( +"" );   // 0
*/!*
```

Tiesą sakant jis daro tą patį kaip `Number(...)`, bet daug trumpesne versija.

Poreikis eilutes pakeisti skaičiais pasitaiko labai dažnai. Pavyzdžiui kai gauname vertes iš HTML formų laukelių, jie dažniausiai yra eilutės. Kas jeigu mums reikia jas susumuoti? 

Binarinis pliusas juos sujungtų į eilutę:

```js run
let apples = "2";
let oranges = "3";

alert( apples + oranges ); // "23", binarinis pliusas eilutes sujungia
```

Jeigu mes norime skaičių, pirma turime juos konvertuoti ir tik tada galime susumuoti:

```js run
let apples = "2";
let oranges = "3";

*!*
// abi vertės iš anksto konvertuojamos į skaičius prieš binarinį pliusą
alert( +apples + +oranges ); // 5
*/!*

// ilgesnis variantas
// alert( Number(apples) + Number(oranges) ); // 5
```

Iš matematiko perspektyvos gausybė pliusų gali atrodyti keistai. Bet iš programuotojo pozicijos, tai nėra nieko ypatingo: unariniai pliusai pritaikomi pirmi, jie pakeičia eilutes į skaičius, o tada binarinis pliusas juos susumuoja.

Kodėl unariniai pliusai pritaikomi vertėms pirmiau nei binarinis? Kaip pamatysime vėliau, taip nutinka dėl jų *aukštesnio prioriteto* (ang. *higher precedence*).

## Operatorių pirmenybė

Jeigu išraiška turi daugiau operatorių nei vieną, jų vykdymo tvarka yra nustatoma pagal jų *pirmenybę*, arba kitaip sakant, iš ankto numatytąjį operatorių prioritetą. 

Dar mokykloje sužinojome, kad daugyba tokioje išraiškoje `1 + 2 * 2` turėtų būti suskaičiuojama prieš sudėtį. Tai ir yra pirmenybė. Yra tariama, kad daugyba turi *aukštesnį prioritetą* negu sudėtis.

Skliausteliai perrašo bet kokią pirmenybę, tad jeigu mums netinka numatyta tvarka, mes galime juos panaudoti, kad tai pakeistume. Pavyzdžiui rašydami `(1 + 2) * 2`.

JavaScript turi daug operatorių. Kiekvienas operatorius turi atitinkamą pirmenybės numerį. Tas kas turi aukštenį numerį įvykdomas pirmiau. Jeigu prioritetas vienodas, įvykdymo eilė yra iš kairės į dešinę. 

Štai ištrauka iš [pirmenybės lentelės](https://developer.mozilla.org/en/JavaScript/Reference/operators/operator_precedence) (jums nereikia šito prisiminti, bet žinokite, kad unariniai operatoriai yra aukščiau už atitinkamus binarinius operatorius):

| Pirmenybė | Pavadinimas | Ženklas |
|------------|------|------|
| ... | ... | ... |
| 16 | unarinis pliusas | `+` |
| 16 | unarinis minusas | `-` |
| 14 | daugyba | `*` |
| 14 | dalyba | `/` |
| 13 | sudėtis | `+` |
| 13 | atimtis | `-` |
| ... | ... | ... |
| 3 | asignavimas | `=` |
| ... | ... | ... |

Kaip matome, "unarinis pliusas" turi pirmenybę `16`, kuri yra didesnė nei "sudėties" `13` (binarinis pliusas). Dėl tos priežasties, išraiškoje `"+apples + +oranges"`, unariniai pliusai suveikia pirmiau už sudėtį.

## Asignavimas

Atkreipkite dėmesį, kad asignavimas (kitaip užduoties operatorius) `=` taip pat yra operatorius. Lentelėje jis įrašytas kaip turintis labai žemą pirmenybę `3`.

Dėl tos priežasties kai mes priskiriame kintamąjį, kaip `x = 2 * 2 + 1`, visų pirma suskaičiuojama vertė ir tik tada `=` yra įvertinamas bei rezultatas patalpinamas į `x`.

```js
let x = 2 * 2 + 1;

alert( x ); // 5
```

Asignavimus įmanoma sujungti į grandinę:

```js run
let a, b, c;

*!*
a = b = c = 2 + 2;
*/!*

alert( a ); // 4
alert( b ); // 4
alert( c ); // 4
```

Sujungti į grandinę asignavimai įvertinami iš dešinės į kairę. Visų pirmą įvykdoma dešiniausiai esanti išraiška `2 + 2` ir priskiriama kintamiesiems esantiems dešinėje: `c`, `b` ir `a`. Galų gale visi kintamieji dalinasi viena verte.

````smart header="Užduoties operatorius `\"=\"` grąžina vertę"
Operatorius visada grąžina vertę. Tai yra akivaizdu tokiems atvejams kaip sudėtis `+` arba daugyba `*`. Bet asignavimas taip pat seka šita taisykle.

Šaukimas `x = value` įrašo `value` į `x` *ir tada ją grąžina*.

Štai pavyzdys su asignavimu sudėtingesnėje išraiškoje:

```js run
let a = 1;
let b = 2;

*!*
let c = 3 - (a = b + 1);
*/!*

alert( a ); // 3
alert( c ); // 0
```

Pavyzdyje aukščiau, išraiškos `(a = b + 1)` rezultatas yra vertė, kuri buvo priskirta `a` (tai yra `3`). Vėliau ji naudojama tolesniuose vertinimuose.

Koks juokingas kodas, juk taip? Turėtume suprasti kaip jis veikia, nes kartais tokius dalykus randame JavaScript bibliotekose, bet patys tokių geriau nerašykite. Tokie triukai tikrai nepaverčia kodo aiškesniu ir įskaitomesniu.
````

## Liekana %

Liekanos operatorius `%`, nepaisant jo išvaizdos, nėra susijęs su procentais.

Šios išraiškos `a % b` rezultatas yra liekana po sveikų skaičių dalybos `a` iš `b`.

Pavyzdžiui:

```js run
alert( 5 % 2 ); // 1 yra liekana kai 5 padalinami iš 2
alert( 8 % 3 ); // 2 yra liekana kai 8 padalinami iš 3
alert( 6 % 3 ); // 0 yra liekana kai 6 padalinami iš 3
```

## Kėlimas laipsniu **

Kėlimo laipsniu (ang. exponentiation) operatorius `**` yra naujas kalbos priedas.

Natūraliajam skaičiui `b`, kai `a ** b` rezultatas yra `a` padaugintas iš savęs `b` kartus.

Pavyzdžiui:

```js run
alert( 2 ** 2 ); // 4  (2 * 2)
alert( 2 ** 3 ); // 8  (2 * 2 * 2)
alert( 2 ** 4 ); // 16 (2 * 2 * 2 * 2)
```

Operatorius veikia ir su trupmenomis.

Pavyzdžiui:

```js run
alert( 4 ** (1/2) ); // 2 (laipsnis 1/2 yra taip pat kaip traukti iš šaknies, tai paprasta matematika)
alert( 8 ** (1/3) ); // 2 (laipsnis 1/3 taip pats kaip kubinė šaknis)
```

## Padidėjimas/sumažėjimas

<!-- Can't use -- in title, because built-in parse turns it into – -->

Skaičiaus padidinimas arba sumažinimas vienetu yra viena dažniausiai naudojamų įprastinių skaičių operacijų. 

Tad tam netgi yra specialūs operatoriai:

- **Padidinimas** `++` (ang. increment) kintamąjį padidina 1-u:

    ```js run no-beautify
    let counter = 2;
    counter++;        // veikia taip pat kaip counter = counter + 1, bet yra trumpesnis
    alert( counter ); // 3
    ```
- **Sumažinimas** `--` (ang. decrement) sumažina kintamajį 1-u:

    ```js run no-beautify
    let counter = 2;
    counter--;        // veikia taip kaip counter = counter - 1, bet yra trumpesnis
    alert( counter ); // 1
    ```

```warn
Padidinimas/sumažinimas gali būti taikomas tik kintamiesiems. Bandymas jį naudoti vertei kaip pavyzdžiui `5++` sukels klaidą.
```

Operatoriai `++` ir `--` gali būti dedami tiek prieš, tiek ir po kintamojo.

- Kai operatorius eina po kintamojo, jis yra "priedėlio formoje" (ang. "postfix form"): `counter++`.
- "Priešdėlio forma" (ang. "prefix form") yra tada kai operatorius eina prieš kintamąjį: `++counter`.

Abu šie teiginiai daro tą patį: padidina `counter` vienu `1`.

Ar yra koks nors skirtumas? Taip, bet jį galime pamatyti tik naudodami grąžintą vertę iš `++/--`.

Pasiaiškinkime. Kaip žinoma, visi operatoriai grąžina vertę. Padidinimas/sumažinimas ne išimtis. Priešdėlio forma grąžina naują vertę kai tuo tarpu priedėlio forma grąžina senąją formą (prieš padidinimą/sumažinimą). 

Tam kad pamatytume skirtumą, pavyzdys:

```js run
let counter = 1;
let a = ++counter; // (*)

alert(a); // *!*2*/!*
```

Eilėje `(*)`, *priešdėlio* forma `++counter` padidina `counter` ir grąžina vertę `2`. Tad `alert` parodo `2`.

Dabar patikrinkime priedėlio formą:

```js run
let counter = 1;
let a = counter++; // (*) pakeitėme ++counter į counter++

alert(a); // *!*1*/!*
```

Eilutėje `(*)`, *priedėlio* forma `counter++` taip pat padidina `counter`, bet grąžina *senąją* vertę (dar prieš padidinimą. Tad `alert` parodo `1`.

Apibendrintai:

- Jeigu padidinimo/sumažinimo rezultatas nėra naudojamas, nėra jokio skirtumo kokią formą naudoti:

    ```js run
    let counter = 0;
    counter++;
    ++counter;
    alert( counter ); // 2, abi eilės viršuje padarė tą patį
    ```
- Jeigu norime padidinti vertę *ir* iš karto panaudoti operatoriaus rezultatą, mums reikia priešdėlio formos:

    ```js run
    let counter = 0;
    alert( ++counter ); // 1
    ```
- Jeigu norime padidinti vertę, bet naudoti jos senąją formą, mums reikia priedėlio formos:

    ```js run
    let counter = 0;
    alert( counter++ ); // 0
    ```

````smart header="Padidinimas/sumažinimas tarp kitų operatorių"
Operatoriai `++/--` gali būti naudojami su išraiškomis. Pirmumas yra aukštesnis už didelę dalį kitų aritmetinių veiksmų.

Pavyzdžiui:

```js run
let counter = 1;
alert( 2 * ++counter ); // 4
```

Palyginkite tai su:

```js run
let counter = 1;
alert( 2 * counter++ ); // 2, nes counter++ grąžina *senąją* vertę
```

Nors techniškai viskas yra gerai, bet tokie žymėjimai dažniausiai padaro kodą sunkiau įskaitomu. Viena eilutė atlieka daug veiksmų -- negerai.

Skaitant kodą, greitas "vertikalus" skanavimas akimis gali praleisti tokį užrašą kaip `counter++` ir nebus pilnai aišku, kad kintamasis padidėjo.

Mes patariame naudoti "viena eilutė -- vienas veiksmas" stilių:

```js run
let counter = 1;
alert( 2 * counter );
counter++;
```
````

## Bitų operatoriai

Bitų (ang. bitwise) operatoriai su argumentais elgiasi kaip su 32-bit sveikaisiais skaičias ir dirba jų binarinio pateikimo lygyje.

Tokie operatoriai nėra specifiniai vien JavaScript kalbai. Jie yra palaikomi didžiojoje dalyje programinių kalbų.

Operatorių sąrašas:

- AND ( `&` )
- OR ( `|` )
- XOR ( `^` )
- NOT ( `~` )
- LEFT SHIFT ( `<<` )
- RIGHT SHIFT ( `>>` )
- ZERO-FILL RIGHT SHIFT ( `>>>` )

Šie operatoriai naudojami labai retai. Kad juos suprastume, mums reikia pasinerti į žemo-lygio skaičių taikimą ir tai daryti šiuo metu nebūtų optimalu, juolabiau, kad mums jų greitu laiku neprireiks. Jeigu jums įdomu, galite daugiau paskaityti apie [Bitwise Operators](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Operators/Bitwise_Operators) MDN straipsnyje. Daug praktiškiau tai padaryti kai iškils tikras poreikis. 

## Keitimas vietoje (ang. Modify-in-place)

Mums dažnai tenka kintamajam pritaikyti operatorių ir tuo pačiu patalpinti naują rezultatą į tą patį kintamajį.

Pavyzdžiui:

```js
let n = 2;
n = n + 5;
n = n * 2;
```

Šis užrašas gali būti sutrumpintas naudojant operatorius `+=` ir `*=`:

```js run
let n = 2;
n += 5; // dabar n = 7 (tas pats kaip n = n + 5)
n *= 2; // dabar n = 14 (tas pats kaip n = n * 2)

alert( n ); // 14
```

Trumpieji "keitimo-ir-priskyrimo" operatoriai egzistuoja visiems aritmetiniams ir bitų operatoriams: `/=`, `-=` ir t.t.

Tokie operatoriai turi tokį patį pirmumą kaip ir įprastiniai asignavimai, tad jie dažniausiai vykdomi po didžiosios dalies kitų skaičiavimų:

```js run
let n = 2;

n *= 3 + 5;

alert( n ); // 16  (pirma įvykdoma dešinė pusė, tas pats kaip būtų n *= 8)
```

## Kablelis

Kablelio operatorius `,` yra vienas iš rečiausių ir neįprasčiausių operatorių. Kartais jis naudojamas, kad sutrumpintume kodą, tad turime apie jį žinoti, kad suprastume kas vyksta.

Kablelio operatorius leidžia įvertinti kelias išraiškas, atskirdamas jas kableliu `,`. Kiekviena jų įvykdoma, tačiau grąžinamas tik rezultatas iš paskutinės išraiškos. 

Pavyzdžiui:

```js run
*!*
let a = (1 + 2, 3 + 4);
*/!*

alert( a ); // 7 (3 + 4 rezultatas)
```

šiuo atveju išraiška `1 + 2`  yra įvertinama, bet jos rezultatas išmetamas. Tada įvertinama `3 + 4` ir grąžinamas jos rezultatas.

```smart header="Kablelis turi labai žemą prioritetą"
Atkreipkite dėmesį, kad kablelio operatorius turi labai žemą prioritetą, žemesnį nei `=`, dėl to skliausteliai yra labai svarbūs kaip pavyzdyje aukščiau.

Be jų: `a = 1 + 2, 3 + 4` pirma įvertina `+` susumuodamas visus skaičius į `a = 3, 7`, o tada užduoties operatorius `=` priskiria `a = 3`, o visa kita yra ignoruojama. Panašiai lyg tai būtų `(a = 1 + 2), 3 + 4`.
```

Kam mums reikalingas operatorius, kuris išmeta viską išskyrus paskutinę išraišką? 

Kartais žmonės jį naudoja sudėtingesniuose konstruktuose, kad sudėtų kelis veiksmus į vieną eilę. 

Pavyzdžiui:

```js
// trys operacijos vienoje eilutėje
for (*!*a = 1, b = 3, c = a * b*/!*; a < 10; a++) {
 ...
}
```

Tokie triukai dažnai naudojami JavaScript struktūrose (ang. frameworks). Dėl to juos ir paminėjome. Bet dažniausiai jie nepalengvina kodo skaitymo tad turėtume gerai pagalvoti prieš juos naudodami.
