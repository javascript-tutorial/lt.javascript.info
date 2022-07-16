# Pagrindiniai operatoriai, matematika

Mes žinome daug operatorių iš mokyklos. Tokie kaip sudėtis `+`, daugyba `*`, atimtis `-` ir taip toliau.

Šiame skyriuje pradėsime nuo paprastųjų operatorių, o paskui aptarsime specifinius JavaScript aspektus, kurių neapima mokyklinė aritmetika.

## Terminai: “unarinis”, “binarinis”, “operandas”

Prieš tęsiant, išsiaiškinkime įprastinę terminologiją.

- *Operandas* -- yra tai, kam operatoriai yra naudojami. Pavyzdžiui šioje daugyboje `5 * 2` yra du operandai: kairysis operandas yra `5`, o dešinysis yra `2`. Kartais žmonės juos vadina argumentais, o ne operandais.
- Operatorius yra *unarinis*, jeigu turi vieną operandą. Pavyzdžiui, unarinis neiginys `-` paverčia skaičių neigiamu:

    ```js run
    let x = 1;

    *!*
    x = -x;
    */!*
    alert( x ); // -1, pritaikytas unarinis neiginys
    ```
- Operatorius yra *binarinis* jeigu turi du operandus. Tas pats minusas egzistuoja ir binarinėse formose:

    ```js run no-beautify
    let x = 1, y = 3;
    alert( y - x ); // 2, binarinis minusas atima vertes
    ```

    Formaliai aukščiau esančiame pavyzdyje mes turime du skirtingus operatorius, kurie dalinasi tuo pačiu simboliu: neigimo operatoriumi, t.y. unariniu operatoriumi, kuris pakeičia simbolį, ir atimties operatoriumi, t.y. binarinu operatoriumi, kuris atima vieną skaičių iš kito. 

## Matematika

Yra palaikomos šios matematinės operacijos:

- Sudėtis `+`,
- Atimtis `-`,
- Daugyba `*`,
- Dalyba `/`,
- Dalybos liekanos ėmimas `%`,
- Kėlimas laipsniu `**`.

Pirmieji keturi yra aiškūs, o apie `%` ir `**` reikia pasakyti keletą žodžių.

### Dalybos liekanos ėmimas %

Dalybos liekanos ėmimo operatorius `%`, nepaisant jo išvaizdos, neturi nieko bendro su procentais.

Rezultatas `a % b` yra dalybos iš `a` ir `b` [likutis](https://en.wikipedia.org/wiki/Remainder).

Pavyzdžiui:

```js run
alert( 5 % 2 ); // 1, likutis, gautas padalijus 5 iš 2
alert( 8 % 3 ); // 2, likutis, gautas padalijus 8 iš 3
```

### Kėlimas laipsniu **

Kėlimo laipsniu operatorius `a ** b` pakelia `a` iki `b` laipsnio.

Mokyklinėje matematikoje mes rašome tai kaip a<sup>b</sup>.

Pavyzdžiui:

```js run
alert( 2 ** 2 ); // 2² = 4
alert( 2 ** 3 ); // 2³ = 8
alert( 2 ** 4 ); // 2⁴ = 16
```

Kaip ir matematikoje, kėlimo laipsniu operatorius tinka ir ne sveikiesiems skaičiams. 

Pavyzdžiui, norėdami gauti skaičiaus kvadratinę šaknį, turime ji pakelti iki ½ laipsnio:

```js run
alert( 4 ** (1/2) ); // 2 (kvadratinė šaknis iš a yra lygiavertė a pakėlimui iki 1/2 laipsnio)
alert( 8 ** (1/3) ); // 2 (kubinė šaknis iš a yra lygiavertė a pekėlimui iki 1/3 laipsnio)
```


## Eilučių sudėtis naudojant binarinį +

Apžvelkime ypatingas JavaScript operatorių savybes, kurios išeina už mokyklinės aritmetikos ribų.

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

Nesvarbu, ar pirmasis operandas yra eilutė, ar antrasis.

Štai sudėtingesnis pavyzdys:

```js run
alert(2 + 2 + '1' ); // "41" bet ne "221"
```

Čia operatoriai veikia vienas po kito. Pirmasis `+` sumuoja du skaičius, todėl grąžina `4`, o kitas `+` prie jų prideda eilutę `1`, taigi gaunama `4 + '1' = '41'`.

```js run
alert('1' + 2 + 2); // "122" bet ne "14"
```
Šiuo atveju pirmasis operandas yra eilutė, o kitus du operandus kompiliatorius taip pat traktuoja kaip eilutes. Elementas `2` sujungiamas su elementu `'1'`, todėl gaunasi `'1' + 2 = "12"` ir `"12" + 2 = "122"`.

Binarinis pliusas `+` yra vienintelis operatorius, kuris taip veikia su eilutėmis. Kiti aritmetiniai operatoriai dirba tik su skaičiais ir visada konvertuoja savo operandus į skaičius.

Čia pateikiama atimties ir dalybos demonstracija:

```js run
alert( 6 - '2' ); // 4, konvertuoja '2' į skaičių
alert( '6' / '2' ); // 3, konvertuoja abu operandus į skaičius
```

## Skaitmenų konvertavimas, unarinis +

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

Kodėl unariniai pliusai pritaikomi vertėms pirmiau nei binarinis? Kaip pamatysime vėliau, taip nutinka dėl jų *aukštesnio prioriteto*.

## Operatorių pirmenybė

Jeigu išraiška turi daugiau operatorių nei vieną, jų vykdymo tvarka yra nustatoma pagal jų *pirmenybę*, arba kitaip sakant, iš ankto numatytąjį operatorių prioritetą. 

Dar mokykloje sužinojome, kad daugyba tokioje išraiškoje `1 + 2 * 2` turėtų būti suskaičiuojama prieš sudėtį. Tai ir yra pirmenybė. Yra tariama, kad daugyba turi *aukštesnį prioritetą* negu sudėtis.

Skliausteliai perrašo bet kokią pirmenybę, tad jeigu mums netinka numatyta tvarka, mes galime juos panaudoti, kad tai pakeistume. Pavyzdžiui rašydami `(1 + 2) * 2`.

JavaScript turi daug operatorių. Kiekvienas operatorius turi atitinkamą pirmenybės numerį. Tas kas turi aukštenį numerį įvykdomas pirmiau. Jeigu prioritetas vienodas, įvykdymo eilė yra iš kairės į dešinę. 

Štai ištrauka iš [pirmenybės lentelės](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence) (jums nereikia šito prisiminti, bet žinokite, kad unariniai operatoriai yra aukščiau už atitinkamus binarinius operatorius):

| Pirmenybė | Pavadinimas | Ženklas |
|------------|------|------|
| ... | ... | ... |
| 15 | unarinis pliusas | `+` |
| 15 | unarinis minusas | `-` |
| 14 | kėlimas laipsniu | `**` |
| 13 | daugyba | `*` |
| 13 | dalyba | `/` |
| 12 | sudėtis | `+` |
| 12 | atimtis | `-` |
| ... | ... | ... |
| 2 | priskyrimas | `=` |
| ... | ... | ... |

Kaip matome, “unarinio pliuso” prioritetas yra `15`, t. y. aukštesnis už “sudėties” (binarinio pliuso) prioritetą `12`. Todėl išraiškoje `"+apples + +oranges"` unarinis pliusas veikia pirmiau už sudėtinį pliusą.

## Priskyrimas

Atkreipkime dėmesį, kad priskyrimas `=` taip pat yra operatorius. Pirmenybės lentelėje jis įrašytas su labai mažu prioritetu - `2`.

Dėl tos priežasties kai mes priskiriame kintamąjį, kaip `x = 2 * 2 + 1`, visų pirma suskaičiuojama vertė ir tik tada `=` yra įvertinamas bei rezultatas patalpinamas į `x`.

```js
let x = 2 * 2 + 1;

alert( x ); // 5
```

### Priskyrimas = grąžina vertę

Tai, kad `=` yra operatorius, o ne “stebuklinga” kalbos konstrukcija, turi įdomią pasekmę.

Visi JavaScript operatoriai grąžina vertę. Kai kuriems operatoriams, pavyzdžiui, `+` ir `-`, tai akivaizdu. Tačiau priskyrimo operatorius `=` nėra išimtis.

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

Linksmas priskyrimo panaudojimas, ar ne? Mes turime suprasti, kaip tai veikia, nes kartais tai matome JavaScript bibliotekose.

Tačiau nerekomenduojama rašyti šiuo stiliumi. Tokie triukai nepadarys jūsų kodą aiškesnį ar lengviau skaitomą.

### Grandinės priskyrimas

Dar viena įdomi galimybė - atlikti priskyrimus grandininiu būdu:

```js run
let a, b, c;

*!*
a = b = c = 2 + 2;
*/!*

alert( a ); // 4
alert( b ); // 4
alert( c ); // 4
```

Toks priskyrimas vykdomas iš dešinės į kairę. Pirmiausia apskaičiuojama dešinioji išraiška `2 + 2` ir priskiriama kairiesiems kintamiesiems: `c`, `b` ir `a`. Galiausiai visi kintamieji turi vieną vertę.

Vėlgi, kad būtų lengviau skaityti, tokį kodą geriau suskirstyti į kelias eilutes:

```js
c = 2 + 2;
b = c;
a = c;
```
Šio stiliaus nauda ypač pastebima greitai peržiūrint kodą.

## Sutrumpinta aritmetika su priskyrimu

Mums neretai reikia taikyti operatorių kintamajam ir naują rezultatą saugoti tame pačiame kintamajame.

Pavyzdžiui:

```js
let n = 2;
n = n + 5;
n = n * 2;
```

Šį užrašą galima sutrumpinti naudojant operatorius `+=` ir `*=`:

```js run
let n = 2;
n += 5; // dabar n = 7 (tas pats kaip ir n = n + 5)
n *= 2; // dabar n = 14 (tas pats kaip ir n = n * 2)

alert( n ); // 14
```

Visiems aritmetiniams ir bitų lygybės operatoriams taikomi trumpi “modify-and-assign” (liet. *“pakeisti ir priskirti”*) operatoriai: Tai gali būti `/=`, `-=` ir t. t.

Tokie operatoriai turi tokią pačią pirmenybę kaip ir įprasti priskyrimai, todėl jie atliekami po daugumos kitų skaičiavimų:

```js run
let n = 2;

n *= 3 + 5;

alert( n ); // 16  (pirmiausiai bus vykdoma dešinioji pusė, išraiška yra identiška n *= 8)
```

## Padidėjimas/sumažėjimas

<!-- Can't use -- in title, because the built-in parser turns it into a 'long dash' – -->

Skaičiaus padidinimas arba sumažinimas vienetu yra viena dažniausiai naudojamų įprastinių skaičių operacijų. 

Tad tam netgi yra specialūs operatoriai:

- **Padidinimas** `++` (ang. *“increment”*) kintamąjį padidina 1-u:

    ```js run no-beautify
    let counter = 2;
    counter++;        // veikia taip pat kaip counter = counter + 1, bet yra trumpesnis
    alert( counter ); // 3
    ```
- **Sumažinimas** `--` (ang. *“decrement”*) sumažina kintamajį 1-u:

    ```js run no-beautify
    let counter = 2;
    counter--;        // veikia taip kaip counter = counter - 1, bet yra trumpesnis
    alert( counter ); // 1
    ```

```warn
Padidinimas/sumažinimas gali būti taikomas tik kintamiesiems. Bandymas jį naudoti vertei kaip pavyzdžiui `5++` sukels klaidą.
```

Operatoriai `++` ir `--` gali būti dedami tiek prieš, tiek ir po kintamojo.

- Kai operatorius eina po kintamojo, jis yra “priedėlio formoje” (ang. *"postfix form"*): `counter++`.
- “Priešdėlio forma” (ang. *“prefix form”*) yra tada kai operatorius eina prieš kintamąjį: `++counter`.

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

Skaitant kodą, greitas “vertikalus” skanavimas akimis gali praleisti tokį užrašą kaip `counter++` ir nebus pilnai aišku, kad kintamasis padidėjo.

Mes patariame naudoti “viena eilutė -- vienas veiksmas” stilių:

```js run
let counter = 1;
alert( 2 * counter );
counter++;
```
````

## Bitų operatoriai

Bitų (ang. *“bitwise”*) operatoriai su argumentais elgiasi kaip su 32-bit sveikaisiais skaičias ir dirba jų binarinio pateikimo lygyje.

Tokie operatoriai nėra specifiniai vien JavaScript kalbai. Juos palaiko daugelis programavimo kalbų.

Operatorių sąrašas:

- AND ( `&` )
- OR ( `|` )
- XOR ( `^` )
- NOT ( `~` )
- LEFT SHIFT ( `<<` )
- RIGHT SHIFT ( `>>` )
- ZERO-FILL RIGHT SHIFT ( `>>>` )

Šie operatoriai naudojami labai retai, kai reikia atlikti veiksmus su skaičiais pačiu žemiausiu (bitų) lygiu. Šių operatorių artimiausiu metu mums neprireiks, nes interneto svetainių kūrimui jie mažai reikalingi, tačiau kai kuriose specialiose srityse, pavyzdžiui, kriptografijoje, jie yra naudingi. MDN galite perskaityti [skyrių apie juos](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#Bitwise), kai to tikrai prireiks.

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

Tokie triukai dažnai naudojami JavaScript struktūrose (ang. *“frameworks”*). Dėl to juos ir paminėjome. Bet dažniausiai jie nepalengvina kodo skaitymo tad turėtume gerai pagalvoti prieš juos naudodami.
