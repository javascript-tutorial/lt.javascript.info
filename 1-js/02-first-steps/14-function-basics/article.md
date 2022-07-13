# Funkcijos

Dažnai tą patį veiksmą reikia pakartoti daugelyje programos dalių.

Pavyzdžiui, reikia parodyti lankytojui gražų pranešimą, kai jis įeina į svetainę, kai jis išeina iš svetainės arba bet kur kitur.

Siekiant išvengti to paties kodo kartojimo daugelyje vietų, buvo sugalvotos funkcijos. Funkcijos - tai pagrindiniai programos blokai.

Jus jau matėte integruotų funkcijų pavyzdžių - tai `alert(message)`, `prompt(message, default)` ir `confirm(question)`. Tačiau taip pat galima kurti savo funkcijas

## Funkcijos deklaravimas

Norėdami sukurti funkcijas, galime naudoti *funkcijos deklaravimų*.

Funkcijos deklaravimo pavyzdys:

```js
function showMessage() {
  alert( 'Labas visiems!' );
}
```

Pirmiausia įrašomas raktažodis `funkcija`, po jo nurodomas funkcijos pavadinimas, po to skliausteliuose pateikiamas parametrų sąrašas, atskirtas kableliais (aukščiau pateiktame pavyzdyje jis yra tuščias), ir, galiausiai, funkcijos kodas, dar vadinamas «funkcijos turiniu», riestiniuose skliaustuose.

```js
function name(parameters) {
  ...body...
}
```

Mūsų naująją funkciją galima iškviesti jos pavadinimu: `showMessage()`.

Pavyzdžiui:

```js run
function showMessage() {
  alert( 'Labas visiems!' );
}

*!*
showMessage();
showMessage();
*/!*
```

Kai mes iškviečiame `showMessage()`, įvykdomas funkcijos kodas. Čia matysime pranešimą du kartus.

Šis pavyzdys aiškiai parodo vieną iš pagrindinių funkcijų tikslų - atsikratyti kodo dubliavimo.

Jei reikia pakeisti pranešimą arba jo išvedimo būdą, užteks pakeisti ją vienoje vietoje: funkcijoje, kuri išveda šį pranešimą.

## Lokaliniai kintamieji

Funkcijoje deklaruoti kintamieji matomi tik toje funkcijoje.

Pavyzdžiui:

```js run
function showMessage() {
*!*
  let message = "Sveiki, aš esu JavaScript!"; // lokalinis kintamasis
*/!*

  alert( message );
}

showMessage(); // Sveiki, aš esu JavaScript!

alert( message ); // <-- bus sukelta klaida, nes kintamasis matomas tik funkcijos viduje.
```

## Išoriniai kintamieji

Funkcija turi prieigą prie išorinių kintamųjų, pavyzdžiui:

```js run no-beautify
let *!*userName*/!* = 'John';

function showMessage() {
  let message = 'Labas, ' + *!*userName*/!*;
  alert(message);
}

showMessage(); // Labas, John
```

Funkcija turi pilną prieigą prie išorinių kintamųjų ir gali keisti jų vertę.

Pavyzdžiui:

```js run
let *!*userName*/!* = 'John';

function showMessage() {
  *!*userName*/!* = "Bob"; // (1) keičiame išorinio kintamojo vertę

  let message = 'Labas, ' + *!*userName*/!*;
  alert(message);
}

alert( userName ); // *!*John*/!* prieš funkcijos iškvietimą

showMessage();

alert( userName ); // *!*Bob*/!*, vertė, pakeista funkcija
```

Išorinis kintamasis naudojamas tik tuo atveju, jei nėra lokalinio kintamojo.

Jei funkcijos viduje deklaruojame kintamąjį, kuris buvo deklaruotas už funkcijos ribų, išorinis kintamasis bus ignoruojamas. Pavyzdžiui, toliau pateiktame kode funkcija naudoja lokalinį kintamąjį `userName`. Išorinis bus ignoruojamas:

```js run
let userName = 'John';

function showMessage() {
*!*
  let userName = "Bob"; // deklaruojame vietinį kintamąjį
*/!*

  let message = 'Labas, ' + userName; // *!*Bob*/!*
  alert(message);
}

// funkcija sukurs savo kintamąjį userName ir jį naudos
showMessage();

alert( userName ); // *!*John*/!*, niekas nepasikeitė, funkcija nepakeitė išorinio kintamojo
```

```smart header="Globalūs kintamieji"
Kintamieji, deklaruojami už visų funkcijų ribų, pvz., išorinis kintamasis `userName` aukščiau pateiktame kode, vadinami globaliaisiais.

Globalūs kintamieji matomi bet kurioje funkcijoje (nebent tose funkcijose yra to paties pavadinimo kintamųjų).

Patartina kuo mažiau naudoti globaliuosius kintamuosius. Šiuolaikiniame kode paprastai globalių kintamųjų būna nedaug arba jų iš viso nebūna. Nors kartais jos yra naudingos svarbiausiems projekto duomenims saugoti.
```

## Parametrai

Naudodami parametrus (dar vadinamus *funkcijos argumentais*) funkcijai galime perduoti bet kokią informaciją.

Žemiau pateiktame pavyzdyje funkcijai perduodami du argumentai: `from` ir `text`.

```js run
function showMessage(*!*from, text*/!*) { // argumentai: from, text
  alert(from + ': ' + text);
}

*!*
showMessage('Ana', 'Sveiki!'); // Ana: Sveiki! (*)
showMessage('Ana', "Kaip sekasi?"); // Ana: Kaip sekasi? (**)
*/!*
```

Kai funkcija iškviečiama eilutėse `(*)` ir `(**)`, perduotos vertės perkeliamos į lokalinius kintamuosius `from` ir `text`. Tada jie naudojami funkcijos turinyje.

Štai dar vienas pavyzdys: turime kintamąjį `from` ir perduodame jį funkcijai. Atkreipkite dėmesį: funkcija pakeičia reikšmę `from`, tačiau šis pokytis nėra matomas iš išorės. Funkcija visada gauna tik vertės kopiją:


```js run
function showMessage(from, text) {

*!*
  from = '*' + from + '*'; // papuoškime from
*/!*

  alert( from + ': ' + text );
}

let from = "Ana";

showMessage(from, "Hello"); // *Ana*: Sveiki

// "from" vertė lieka ta pati, funkcija pakeitė tik lokalinio kintamojo vertę
alert( from ); // Ana
```

## Numatytieji parametrai

Jei parametras nenurodytas, jo reikšmė tampa `undefined`.

Pavyzdžiui, aukščiau pateiktą funkciją `showMessage(from, text)` galima iškviesti su vienu argumentu:

```js
showMessage("Ana");
```

Tai nesukels klaidos. Po tokio iškvietimo rašoma `"*Ana*: undefined"`. Kvietime nenurodytas `text` parametras, todėl laikoma, kad `text === undefined`.

Jei norime nustatyti numatytąją `text` parametro vertę, turime ją nurodyti po `=`:

```js run
function showMessage(from, *!*text = "tekstas nepridėtas"*/!*) {
  alert( from + ": " + text );
}

showMessage("Ana"); // Ana: tekstas nepridėtas
```

Dabar, jei `text` parametras nenurodytas, jo vertė bus `"tekstas nepridėtas"`.

Šiuo atveju `"tekstas nepridėtas"` yra eilutė, tačiau vietoj jos gali būti sudėtingesnė išraiška, kuri apskaičiuojama ir priskiriama, kai nėra parametro. Pavyzdžiui:

```js run
function showMessage(from, text = anotherFunction()) {
  // anotherFunction() bus vykdoma tik tuo atveju, jei `text` nebus perduotas
  // rezultatas yra `text` vertė.
}
```

```smart header="Numatytųjų parametrų apskaičiavimas"
JavaScript kalba numatytieji parametrai apskaičiuojami kiekvieną kartą, kai funkcija iškviečiama be atitinkamo parametro.

Aukščiau pateiktame pavyzdyje `anotherFunction()` bus iškviečiama kiekvieną kartą, kai `showMessage()` bus iškviesta be `text` parametro.
```

````smart header="Numatytųjų nustatymų naudojimas ankstesnėse JavaScript versijose"
Ankstyvosios JavaScript versijos nepalaiko numatytųjų parametrų. Todėl senesniuose skriptiniuose tekstuose galima rasti alternatyvių būdų.

Pavyzdžiui, patikrinimas dėl `undefined`:

```js
function showMessage(from, text) {
*!*
  if (text === undefined) {
    text = 'tekstas nepridėtas';
  }
*/!*

  alert( from + ": " + text );
}
```

...Arba naudodami operatorių `||`:

```js
function showMessage(from, text) {
  // jei text vertę yra false, nustatyti text parametro numatytąją vertę
  text = text || 'tekstas nepridėtas';
  ...
}
```


````


## Grąžintina vertė

Funkcija gali grąžinti rezultatą, kuris bus perduotas ją iškvietusiam kodui.

Paprasčiausias pavyzdys - dviejų skaičių sudėjimo funkcija:

```js run no-beautify
function sum(a, b) {
  *!*return*/!* a + b;
}

let result = sum(1, 2);
alert( result ); // 3
```

`Return` direktyva gali būti bet kurioje funkcijos turinio vietoje. Kai tik vykdymas pasiekia šį tašką, funkcija sustoja ir vertė grąžinama ją iškvietusiam kodui (priskirta aukščiau nurodytam kintamajam `result`).

Funkcijoje `return' gali būti naudojamas kelis kartus, pavyzdžiui:

```js run
function checkAge(age) {
  if (age > 18) {
*!*
    return true;
*/!*
  } else {
*!*
    return confirm('O tėvai leido?');
*/!*
  }
}

let age = prompt('Kiek jums metų?', 18);

if ( checkAge(age) ) {
  alert( 'Suteikta prieiga' );
} else {
  alert( 'Prieiga uždrausta' );
}
```

Galima naudoti `return` be vertės. Dėl to funkcija bus iš karto baigta.

Pavyzdžiui:

```js
function showMovie(age) {
  if ( !checkAge(age) ) {
*!*
    return;
*/!*
  }

  alert( "Jums rodomas filmas" ); // (*)
  // ...
}
```

Aukščiau pateiktame kode, jei `checkAge(age)` grąžina `false`, `showMovie` neįvykdys `alert`.

````smart header="Funkcijos rezultatas su tuščiu `return` arba be jo yra `undefined`"

Jei funkcija negrąžina vertės, tai yra tas pats, lyg ji būtų grąžinusi `undefined` vertę:

```js run
function doNothing() { /* tuščia */ }

alert( doNothing() === undefined ); // true
```

Tuščias `return` yra analogiškas `return undefined`:

```js run
function doNothing() {
  return;
}

alert( doNothing() === undefined ); // true
```
````

````warn header="Niekada nedėkite eilutės laužimo tarp `return` ir jo vertės"
Ilgos išraiškos `return` atveju gali kilti pagunda ją pateikti keliose atskirose eilutėse, pvz., taip:

```js
return
 (some + long + expression + or + whatever * f(a) + f(b))
```
Kodas nebus vykdomas, nes JavaScript interpretatorius po `return` įterpia kabliataškį. Jam šis kodas atrodys taip:

```js
return*!*;*/!*
 (some + long + expression + or + whatever * f(a) + f(b))
```

Tai iš tikrųjų tampa tuščiu `return`.

Jei norime, kad grąžinimo išraiška apimtų kelias eilutes, turime ją pradėti toje pačioje eilutėje kaip ir `return`. Arba bent jau įterpti skliaustus, pvz., taip:

```js
return (
  some + long + expression
  + or +
  whatever * f(a) + f(b)
  )
```
Tada viskas veiks taip, kaip buvo numatyta.
````

## Funkcijos pavadinimo pasirinkimas

Funkcija - tai veiksmas. Todėl funkcijos pavadinimas dažniausiai yra veiksmažodis. Jis turi būti paprastas, tikslus ir apibūdinti funkcijos veiksmą taip, kad programuotojas, kuris skaitys kodą, teisingai suprastų, ką funkcija daro.

Paprastai veiksmažodžių priešdėliai vartojami bendram veiksmo pobūdžiui reikšti, o po jų eina paaiškinimas. Paprastai programuotojų komandos yra sudariusios susitarimus dėl šių priešdėlių reikšmių.

Pavyzdžiui, funkcijos, prasidedančios žodžiu `"show"`, paprastai ką nors parodo.

Funkcijos, prasidedančios nuo...

- `"get…"` -- grąžina vertę,
- `"calc…"` -- ką nors apskaičiuoja,
- `"create…"` -- ką nors sukuria,
- `"check…"` -- ką nors patikrina ir grąžina "Boolean" vertę ir t. t.

Tokių pavadinimų pavyzdžiai:

```js no-beautify
showMessage(..)     // rodo pranešimą
getAge(..)          // grąžina amžių
calcSum(..)         // apskaičiuoja sumą ir grąžina rezultatą
createForm(..)      // sukuria formą (ir dažniausiai ją grąžina).
checkPermission(..) // tikrina prieigą ir grąžina true/false
```

Dėl priešdėlių iš pirmo žvilgsnio aišku, ką funkcijos pavadinimas daro ir kokią vertę gali grąžinti.

```smart header="Viena funkcija - vienas veiksmas"
Funkcija turėtų atlikti tik tai, ką aiškiai nurodo jos pavadinimas. Tai turėtų būti vienas veiksmas.

Du nepriklausomi veiksmai paprastai reiškia dvi funkcijas, net jei jos turi būti iškviestos kartu (tokiu atveju galime sukurti trečią funkciją joms iškviesti).

Štai keletas pavyzdžių, kurie pažeidžia šią taisyklę:

- `getAge` -- būtų netinkamas pasirinkimas, jei funkcija išveda `alert` su amžiumi (turėtų tik grąžinti jį).
- `createForm` -- būtų netinkamas pasirinkimas, jei funkcija pakeistų dokumentą, pridėdama į jį formą (turėtų tik sukurti formą ir ją grąžinti).
- `checkPermission` -- būtų netinkamas pasirinkimas, jei funkcija rodytų pranešimą su tekstu "Prieiga suteikta / uždrausta" (turėtų tik atlikti patikrinimą ir grąžinti jo rezultatą).

Šiuose pavyzdžiuose naudotos bendrinės priešdėlių reikšmės. Žinoma, savo komandoje galite susitarti ir dėl kitų reikšmių, tačiau jos paprastai nedaug skiriasi nuo bendrųjų. Bet kokiu atveju jūs ir jūsų komanda turėtumėte tiksliai suprasti, ką reiškia priešdėlių, ką funkcija gali ir ko negali su juo daryti.
```

```smart header="Ypač trumpi funkcijų pavadinimai"
Labai dažnai naudojami funkcijų pavadinimai kartais būna itin trumpi.

Pavyzdžiui, [jQuery](http://jquery.com) framework'e yra funkcija, pavadinta `$`. [Lodash](http://lodash.com/) bibliotekoje pagrindinę funkciją žymi vardas `_`.

Tai yra išimtys. Apskritai funkcijų pavadinimai turėtų būti vidutiniškai trumpi ir apibūdinti funkcijų veiksmus.
```

## Funkcijos == Komentarai

Funkcijos turėtų būti trumpos ir atlikti tik vieną veiksmą. Jei funkcija yra didelė, ją tikslinga suskaidyti į kelias mažesnes. Kartais nelengva laikytis šios taisyklės, tačiau ji tikrai gera.

Nedidelės funkcijos ne tik palengvina testavimą ir derinimą -- pats tokių funkcijų egzistavimas atlieka gerų komentarų vaidmenį!

Pavyzdžiui, palyginkime žemiau pateiktas dvi `showPrimes(n)` funkcijas. Kiekviena iš jų išveda [paprastąjį skaičių](https://en.wikipedia.org/wiki/Prime_number) iki n.

Pirmame variante naudojama `nextPrime` žyma:

```js
function showPrimes(n) {
  nextPrime: for (let i = 2; i < n; i++) {

    for (let j = 2; j < i; j++) {
      if (i % j == 0) continue nextPrime;
    }

    alert( i ); // paprastas skaičius
  }
}
```

Antrajame variante naudojama papildoma funkcija `isPrime(n)`, skirta patikrinti, ar yra paprastųjų skaičių:

```js
function showPrimes(n) {

  for (let i = 2; i < n; i++) {
    *!*if (!isPrime(i)) continue;*/!*

    alert(i);  // paprastas skaičius
  }
}

function isPrime(n) {
  for (let i = 2; i < n; i++) {
    if ( n % i == 0) return false;
  }
  return true;
}
```

Antrąjį variantą lengviau suprasti, ar ne? Vietoj kodo dalies matome veiksmo pavadinimą (`isPrime`). Kartais programišiai šį kodą vadina *savaiminiu dokumentavimu*.

Todėl galima kurti funkcijas, net jei neplanuojame jų pakartotinai naudoti. Tokios funkcijos struktūrizuoja kodą ir daro jį aiškesnį.

## Iš viso

Funkcijos deklaravimas atrodo taip:

```js
function name(kableliais, atskirti, parametrai) {
  /* kodas */
}
```

- Perduotos vertės nukopijuojamos į funkcijos parametrus ir tampa lokaliniais kintamaisiais.
- Funkcijos turi prieigą prie išorinių kintamųjų. Tačiau tai veikia tik iš vidaus į išorę. Kodas, esantis už funkcijos ribų, neturi prieigos prie jos lokalinių kintamųjų.
- Funkcija gali grąžinti vertę. Jei funkcija nieko negrąžina, rezultatas yra `undefined`.

Kad kodas būtų švaresnis ir aiškesnis, rekomenduojama naudoti lokalinius kintamuosius ir funkcijų parametrus, o ne išorinius kintamuosius.

Funkcija, kuri gauna parametrus, dirba su jais ir grąžina rezultatą, yra daug aiškesnė nei funkcija, kuri iškviečiama be parametrų, bet keičia išorinius kintamuosius, o tai gali turėti šalutinį poveikį.

Funkcijos pavadinimo pasirinkimas:

- Funkcijos pavadinimas turėtų būti aiškus ir aiškiai išreikšti jos paskirtį. Kai pamatysite, kad ji iškviečiama kode, iš karto suprasite, ką ji daro ir ką grąžina.
- Funkcija - tai veiksmas, todėl jos pavadinimas paprastai yra veiksmažodis.
- Yra daug bendrinių priešdėlių, pvz: `create…`, `show…`, `get…`, `check…` ir t. t. Naudokite juos kaip užuominas, paaiškinančias, ką funkcija daro.

Funkcijos yra pagrindinės skriptų sudedamosios dalys. Apžvelgėme tik JavaScript funkcijų pagrindus, tačiau jau galime jas kurti ir naudoti. Tai tik kelionės pradžia. Prie funkcijų grįšime daug kartų ir jas vis giliau nagrinėsime.
