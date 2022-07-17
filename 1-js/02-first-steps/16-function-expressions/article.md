# Function Expression

JavaScript kalboje funkcija yra ne “stebuklinga kalbos struktūra”, o specialios rūšies vertė.

Sintaksė, kurią naudojome anksčiau, vadinama *Function Declaration* (liet. *“funkcijos deklaravimas”*):

```js
function sayHi() {
  alert( "Labas" );
}
```

Egzistuoja ir kita funkcijos kūrimo sintaksė, vadinama *Function Expression* (liet. *“Funkcinė išraiška”*).

Ji leidžia sukurti naują funkciją bet kurios išraiškos viduryje.

Pavyzdžiui:

```js
let sayHi = function() {
  alert( "Labas" );
};
```

Čia mes galime pamatyti kintamąjį `sayHi`, kuris gauna vertę, naują funkciją, sukurtą kaip `function() { alert("Labas"); }`.

Kadangi funkcija kuriama priskyrimo išraiškos kontekste (dešinėje `=` pusėje), tai yra *Function Expression*.

Atkreipkite dėmesį, kad po raktažodžio `function` nėra pavadinimo. Jei naudojame `Function Expressions`, galime jo praleisti.

Čia mes iš karto priskiriame ją kintamajam, todėl šių kodo pavyzdžių prasmė yra ta pati: “sukurti funkciją ir įdėti ją į kintamąjį `sayHi`”.

Sudėtingesniais atvejais, su kuriais susidursime vėliau, funkcija gali būti sukurta ir iš karto iškviesta arba suplanuota vėlesniam vykdymui, niekur nesaugoma, todėl lieka anoniminė.

## Funkcija yra vertė

Dar kartą pakartokime: nesvarbu, kaip sukurta funkcija, funkcija yra vertė. Abiejuose pavyzdžiuose funkcija saugoma kintamajame `sayHi`.

Naudodami `alert` galime netgi išvesti šią vertę:

```js run
function sayHi() {
  alert( "Labas" );
}

*!*
alert( sayHi ); // rodo funkcijos kodą
*/!*
```

Atkreipkite dėmesį, kad paskutinėje eilutėje funkcija nėra paleidžiama, nes po `sayHi` nėra skliaustų. Yra programavimo kalbų, kuriose bet koks funkcijos pavadinimo paminėjimas sukelia jos vykdymą, tačiau JavaScript nėra tokia kalba.

JavaScript kalboje funkcija yra vertė, todėl su ja galime dirbti kaip su verte. Aukščiau esančiame kode funkcija vaizduojama kaip eilutė

Be abejo, funkcija yra ypatinga vertė ta prasme, kad ją galime iškviesti kaip `sayHi()`.

Tačiau tai vis tiek yra vertė. Taigi su ja galime dirbti kaip ir su kitomis vertėmis.

Mes galime nukopijuoti funkciją į kitą kintamąjį:

```js run no-beautify
function sayHi() {   // (1) sukurti
  alert( "Labas" );
}

let func = sayHi;    // (2) nukopijuoti

func(); // Labas     // (3) paleisti kopiją (veikia)!
sayHi(); // Labas    //     tai vis dar veikia (kodėl gi ne)
```

Išsamiai apžvelkime viską, kas čia įvyko:

1. Function Declaration `(1)` sukuria funkciją ir įrašo ją į kintamąjį pavadinimu `sayHi`.
2. Eilutėje `(2)` nukopijavome jos vertę į kintamąjį `func`. Dar kartą atkreipkite dėmesį: po `sayHi` nėra skliaustų. Jeigu taip būtų, tada `func = sayHi()` į `func` įrašytų *iškvietimo rezultatą* `sayHi()`, o ne *pačią funkciją* `sayHi`.
3. Dabar funkciją galima iškviesti ir kaip `sayHi()`, ir kaip `func()`.

Pirmoje eilutėje mes taip pat galėtume naudoti Function Expression, kad sukurtume `sayHi`:

```js
let sayHi = function() { // (1) sukurti
  alert( "Labas" );
};

let func = sayHi;
// ...
```

Viskas veiktų taip pat.

````smart header="Kodėl pabaigoje dedamas kabliataškis?"
Jums gali kilti klausimas, kodėl Function Expression pabaigoje turi kabliataškį `;`, o Function Declaration -- ne:

```js
function sayHi() {
  // ...
}

let sayHi = function() {
  // ...
}*!*;*/!*
```

Atsakymas yra paprastas: Function Expression čia sukurtas kaip `function(…) {…}` priskyrimo teiginyje: `let sayHi = …;`. Kabliataškį `;` rekomenduojama rašyti teiginio pabaigoje, jis nėra funkcijos sintaksės dalis.

Kabliataškis būtų naudojamas paprastesniam priskyrimui, pavyzdžiui, `let sayHi = 5;`, taip pat ir funkcijos priskyrimui.
````

## Callback funkcijos

Apžvelkime daugiau pavyzdžių, kaip perduoti funkcijas kaip vertes ir naudoti funkcinių išraiškų.

Mes parašysime funkciją `ask(question, yes, no)` su trimis parametrais:

`question`
: Klausimo tekstas

`yes`
: Funkcija, paleidžiama, jei atsakymas yra “Yes”

`no`
: Funkcija, paleidžiama, jei atsakymas yra “No”

Funkcija turėtų užduoti klausimą `question` ir, priklausomai nuo naudotojo atsakymo, iškviesti `yes()` arba `no()`:

```js run
*!*
function ask(question, yes, no) {
  if (confirm(question)) yes()
  else no();
}
*/!*

function showOk() {
  alert( "Jus sutikote." );
}

function showCancel() {
  alert( "Jus atšaukėte vykdymą." );
}

// naudojimas: funkcijos showOk, showCancel perduodamos kaip argumentai
ask("Ar sutinkate?", showOk, showCancel);
```

Praktikoje tokios funkcijos yra gana naudingos. Pagrindinis skirtumas tarp “realaus” `ask` ir aukščiau pateikto pavyzdžio yra tas, kad realios funkcijos naudoja sudėtingesnius sąveikos su naudotoju būdus nei paprastas `confirm`. Naršyklėje tokios funkcijos paprastai atvaizduoja gražiai atrodantį klausimo langą. Bet tai jau kita istorija.

**Funkcijos `ask` argumentai vadinamos *callback-funkcijomis* arba *callback'ais*.**

Idėja yra ta, kad mes perduodame funkciją ir tikimės, kad prireikus vėliau ji bus “iškviesta atgal” (ang. *“call back”* -- grįžtamasis iškvietimas). 

Norėdami užrašyti tą pačią funkciją daug trumpiau, galime naudoti `Function Expression`:

```js run no-beautify
function ask(question, yes, no) {
  if (confirm(question)) yes()
  else no();
}

*!*
ask(
  "Ar sutinkate?",
  function() { alert("Jus sutikote."); },
  function() { alert("Jus atšaukėte vykdymą."); }
);
*/!*
```

Šiuo atveju funkcijos deklaruojamos pačiame `ask(...)` iškvietime. Jie neturi pavadinimo, todėl vadinami *anoniminiais*.
Tokios funkcijos nepasiekiamos už `ask` ribų (nes jos nėra priskirtos kintamiesiems), tačiau čia norime būtent to.

Toks mūsų skripte esantis kodas atrodo labai natūraliai ir atitinka JavaScript dvasią.

```smart header="Funkcija yra vertė, vaizduojanti \"veiksmą\""
Įprastos vertės, pavyzdžiui, eilutės arba skaičiai, yra *duomenys*.

Funkcijas, kita vertus, galima traktuoti kaip *veiksmus*.

Mes galime perduoti jas tarp kintamųjų ir paleisti, kuomet norime.
```


## Function Expression palyginus su Function Declaration

Apžvelkime pagrindinius Function Expression ir Function  Declaration skirtumus.

Pirma, sintaksė: kaip juos atskirti kode.

- *Function Declaration:* funkcija, deklaruojama kaip atskiras teiginys pagrindiniame kodo sraute.

    ```js
    // Function Declaration
    function sum(a, b) {
      return a + b;
    }
    ```
- *Function Expression:* funkcija, sukurta išraiškos viduje arba kitoje sintaksės konstrukcijoje. Šiuo atveju funkcija sukuriama dešinėje “priskyrimo išraiškos” `=` pusėje:

    ```js
    // Function Expression
    let sum = function(a, b) {
      return a + b;
    };
    ```

Subtilesnis skirtumas yra tas, *kada* funkciją sukuria JavaScript variklis.

**Function Expression sukuriama, kai ją pasiekia vykdymas, ir gali būti naudojama tik nuo to momento.**

Kai vykdymo srautas pereina į dešinę priskyrimo `let sum = function…` pusę, funkcija yra sukurta ir nuo šiol gali būti naudojama (priskiriama, iškviečiama ir t.t.).

Su Function Declaration yra kitaip.

**Function Declaration gali būti iškviesta anksčiau, nei ji yra apibrėžta.**

Pavyzdžiui, globalus Function Declaration yra matomas visame skripte, nesvarbu, kur jis būtų

Taip yra dėl vidinių algoritmų. Kai JavaScript ruošiasi paleisti skriptą, pirmiausia jame ieško globalių `Function Declaration` ir sukuria funkcijas. Galime tai laikyti “inicializavimo etapu”.

Po to, kai visos `Function Declaration` yra apdorotos, kodas yra vykdomas. Taigi jis turi prieigą prie šių funkcijų.

Pavyzdžiui, tai veikia:

```js run refresh untrusted
*!*
sayHi("Jonas"); // Sveiki, Jonas
*/!*

function sayHi(name) {
  alert( `Sveiki, ${name}` );
}
```

Function Declaration `sayHi` sukuriama, kai JavaScript ruošiasi paleisti skriptą, ir yra matoma visur jame.

...Jeigu tai būtų Function Expression, toliau pateiktas kodas neveiktų:

```js run refresh untrusted
*!*
sayHi("Jonas"); // klaida!
*/!*

let sayHi = function(name) {  // (*) nebėra jokios magijos
  alert( `Sveiki, ${name}` );
};
```

Funkcijos, deklaruotos naudojant Function Expression, sukuriamos, kai jas pasiekia vykdymas. Tai atsitiks tik žvaigždute `(*)` pažymėtoje eilutėje. Per vėlai.

Kita ypatinga Function Declaration savybė yra jų bloko diapazonas (ang. *“block scope”*).

**Griežtuoju režimu (strict mode), kai funkcijos deklaravimas yra kodo bloke, jis yra matomas visuose to bloko dalyse. Bet ne už jo ribų.**

Pavyzdžiui, įsivaizduokime, kad mums reikia deklaruoti funkciją `welcome()`, priklausančią nuo `age` kintamojo, kurį gauname paleidimo metu. O tada užplanuosime kada nors ateityje šia funkcija panaudoti.

Jeigu naudosime Function Declaration, kodas neveiks taip, kaip numatyta:

```js run
let age = prompt("Kiek jums metų?", 18);

// priklausomai nuo sąlygos, deklaruojame funkciją
if (age < 18) {

  function welcome() {
    alert("Labas!");
  }

} else {

  function welcome() {
    alert("Laba diena!");
  }

}

// ...naudoti ją vėliau
*!*
welcome(); // Error: welcome is not defined
*/!*
```

Taip yra todėl, kad Function Declaration yra matomas tik tame kodo bloke, kuriame jis yra.

Štai dar vienas pavyzdys:

```js run
let age = 16; // kaip pavyzdį priskirsime 16

if (age < 18) {
*!*
  welcome();               // \   (bus vykdoma)
*/!*
                           //  |
  function welcome() {     //  |  
    alert("Labas!");       //  |  Function Declaration yra prieinamas
  }                        //  |  visame kodo bloke, kuriame jis deklaruotas.
                           //  |
*!*
  welcome();               // /   (bus vykdoma)
*/!*

} else {

  function welcome() {    
    alert("Laba diena!");
  }
}

// figūriniai skliaustai čia uždaromi,
// todėl mes negalime matyti juose esančių Function Declaration.

*!*
welcome(); // Error: welcome is not defined
*/!*
```

Ką galime padaryti, kad `welcome` būtų matomas už `if` ribų?

Teisingiausia būtų naudoti Function Expression ir priskirti `welcome` kintamajam, kuris yra deklaruotas už `if` ribų ir turi tinkamą matomumą.

Šis kodas veikia kaip numatyta:

```js run
let age = prompt("Kiek jums metų?", 18);

let welcome;

if (age < 18) {

  welcome = function() {
    alert("Labas!");
  };

} else {

  welcome = function() {
    alert("Laba diena!");
  };

}

*!*
welcome(); // dabar viskas gerai
*/!*
```

Arba mes galime dar labiau supaprastinti išraiška, naudodami klausimo ženklo operatorių `?`:

```js run
let age = prompt("Kiek jums metų?", 18);

let welcome = (age < 18) ?
  function() { alert("Labas!"); } :
  function() { alert("Laba diena!"); };

*!*
welcome(); // dabar viskas gerai
*/!*
```


```smart header="Kada rinktis Function Declaration, o kada - Function Expression?"
Paprastai, kai reikia deklaruoti funkciją, pirmiausia reikia atkreipti dėmesį į Function Declaration sintaksę. Ši sintaksė suteikia daugiau laisvės organizuojant kodą, nes tokias funkcijas galime iškviesti prieš jas deklaruodami.

Function Declaration taip pat geriau skaitomumo požiūriu, nes kode lengviau rasti `function f(...) {...}` nei `let f = function(...) {...};`. Function Declaration labiau “traukia akį”.

...Tačiau jei Function Declaration dėl kokių nors priežasčių mums netinka arba mums reikia sąlyginės deklaracijos (ką tik matėme pavyzdį), reikėtų naudoti Function Expression.
```

## Santrauka

- Funkcijos yra vertės. Jas galima priskirti, nukopijuoti arba deklaruoti bet kurioje kodo vietoje.
- Jeigu funkcija deklaruojama kaip atskiras teiginys pagrindiniame kodo sraute, tai vadinama “Function Declaration”.
- Jeigu funkcija sukurta kaip išraiškos dalis, ji vadinama "Function Expression".
- Function Declarations apdorojamos prieš vykdant kodo bloką. Jos matomos visur bloke.
- Function Expressions sukuriamos, kai vykdymo srautas jas pasiekia.

Dažniausiai, kai reikia deklaruoti funkciją, geriau naudoti Function Declaration, nes ji matoma prieš pačią deklaraciją. Tai suteikia daugiau lankstumo organizuojant kodą ir pagerina jo skaitomumą.

Todėl Function Expression turėtume naudoti tik tada, kai Function Declaration netinka užduočiai atlikti. Šiame skyriuje jau matėme keletą tokių pavyzdžių, o ateityje jų bus dar daugiau.
