# Kintamieji

Dažniausiai JavaScript paraiška dirba su informacija. Štai du pavyzdžiai:
1. Internetinė parduotuvė -- informacija gali apimti parduodamas prekes ir pirkimo krepšelį.
2. Pokalbių programėlė -- informacija gali apimti vartotojus, žinutes ir daug daugiau.

Kintamieji (ang. *“variables”*) yra naudojami tam, kad kauptų šią informaciją. 

## Kintamasis

[Kintamasis](https://en.wikipedia.org/wiki/Variable_(computer_science)) yra "įvardinta saugykla" duomenims. Mes galime naudoti kintamuosius, kad kauptume informacines gėrybes, lankytojus ir kitus duomenis.

Norėdami sukurti kintamąjį su JavaScript, naudokite `let` raktinį žodį.

Žemiau esantis pareiškimas sukuria (kitais žodžiais: *deklaruoja*) kintamąjį su pavadinimu “message”:

```js
let message;
```

Dabar į jį galime patalpinti duomenis naudodami priskyrimo operatorių `=`:

```js
let message;

*!*
message = 'Labas'; // įrašyti eilutę "Hello" į kintamąjį, pavadintą message
*/!*
```

Dabar eilutė yra išsaugota į atminties sritį susijusią su kintamuoju. Mes galime gauti prieigą naudodami kintamojo pavadinimą. 

```js run
let message;
message = 'Labas!';

*!*
alert(message); // parodo kintamojo turinį
*/!*
```

Dėl glaustumo galime sujungti kintamojo deklaraciją ir priskyrimą į vieną eilutę:

```js run
let message = 'Labas!'; // apibrėžti kintamąjį ir priskirti jam vertę

alert(message); // Labas!
```

Mes taip pat galime deklaruoti kelis kintamuosius vienoje eilėje:

```js no-beautify
let user = 'John', age = 25, message = 'Labas';
```

Taip atrodo trumpiau, bet iš tikrųjų nerekomenduojame šito daryti. Tam, kad būtų lengviau perskaityti kodą, rekomenduojame naudoti atskirą eilę kiekvienam kintamajam.

Kelių eilių variantas ilgesnis, bet jį lengviau perskaityti:

```js
let user = 'John';
let age = 25;
let message = 'Labas';
```

<<<<<<< HEAD
Kai kurie žmonės apibrėžia kelis kintamuosius tokiu kelių eilių stiliumi:
=======
Some people also define multiple variables in this multiline style:

>>>>>>> 20208769e528337949e946f526534d61d38bac47
```js no-beautify
let user = 'John',
  age = 25,
  message = 'Labas';
```

...Arba netgi "kablelis priekyje" stiliumi:

```js no-beautify
let user = 'John'
  , age = 25
  , message = 'Labas';
```

Techniškai, visi šie variantai daro tą patį. Tad tai daugiau asmeninio skonio ir estetikos reikalas. 


````smart header="`var` vietoje `let`"
Senesniuose skriptuose galite rasti kitą raktažodį: `var` vietoje `let`:

```js
*!*var*/!* message = 'Labas';
```

<<<<<<< HEAD
Raktažodis `var` yra *beveik* tas pats kaip `let`. Jis taip pat deklaruoja kintamąjį, bet šiek tiek kitokiu, “senoviniu” būdu.

Yra subtilūs skirtumai tarp `let` ir `var`, bet kol kas jie mums nėra svarbūs. Mes apie juos kalbėsime detaliau skyriuje <info:var>.
=======
The `var` keyword is *almost* the same as `let`. It also declares a variable but in a slightly different, "old-school" way.

There are subtle differences between `let` and `var`, but they do not matter to us yet. We'll cover them in detail in the chapter <info:var>.
>>>>>>> 20208769e528337949e946f526534d61d38bac47
````

## Realaus gyvenimo analogija

Tam kad būtų lengviau suprasti “kintamojo” sąvoką, įsivaizduokime jį kaip “dėžę” skirtą sudėti duomenims, ant kurios priklijuotas unikaliai pavadintas lipdukas.

<<<<<<< HEAD
Pavyzdžiui kintamąjį `message` galime įsivaizduoti kaip dėžę su etikete `"message"`, kurios viduje yra patalpinta vertė `"Labas!"`:
=======
For instance, the variable `message` can be imagined as a box labelled `"message"` with the value `"Hello!"` in it:
>>>>>>> 20208769e528337949e946f526534d61d38bac47

![](variable.svg)

Mes galime į dėžę įdėti bet kokią vertę.

<<<<<<< HEAD
Mes taip pat galime ją pakeisti kiek norime kartų:
=======
We can also change it as many times as we want:

>>>>>>> 20208769e528337949e946f526534d61d38bac47
```js run
let message;

message = 'Labas!';

message = 'Pasauli!'; // vertė pakeista

alert(message);
```

Kai vertė yra pakeičiama, seni duomenys panaikinami iš kintamojo:

![](variable-change.svg)

Mes taip pat galime deklaruoti du kintamuosius ir nukopijuoti duomenis iš vieno į kitą.

```js run
let hello = 'Labas pasauli!';

let message;

*!*
// nukopijuoti 'Labas pasauli' iš hello į message
message = hello;
*/!*

// dabar abu kintamieji savyje laiko tuos pačius duomenis
alert(hello); // Labas pasauli!
alert(message); // Labas pasauli!
```

````warn header="Dvigubas deklaravimas sukelia klaidą"
Kintamąjį reikia deklaruoti tik vieną kartą.

Pakartotinis to paties kintamojo deklaravimas yra klaida:

```js run
let message = "This";

// pakartotinis 'let' sukelia klaidą
let message = "That"; // SyntaxError: 'message' has already been declared
```
Taigi, kintamąjį turėtume deklaruoti vieną kartą, o tada į jį atsiremti be `let`.
````

<<<<<<< HEAD
```smart header="Funkcinės kalbos"
Yra įdomu pastebėti, kad egzistuoja [funkcinės](https://en.wikipedia.org/wiki/Functional_programming) programavimo kalbos, tokios kaip [Scala](http://www.scala-lang.org/) arba [Erlang](http://www.erlang.org/), kurios draudžia keisti kintamųjų vertes.
=======
```smart header="Functional languages"
It's interesting to note that there exist so-called [pure functional](https://en.wikipedia.org/wiki/Purely_functional_programming) programming languages, such as [Haskell](https://en.wikipedia.org/wiki/Haskell), that forbid changing variable values.
>>>>>>> 20208769e528337949e946f526534d61d38bac47

Tokiose kalbose, kai vertė yra patalpinama “į dėžę”, ji ten ir pasilieka amžiams. Jeigu norime patalpinti kažką kito, kalba mus priverčia sukurti naują dėžę (deklaruoti naują kintamąjį). Mes nebegalime dar kartą panaudoti senojo.

<<<<<<< HEAD
Nors tai atrodo keistai iš pirmo žvilgsnio, tačiau šios kalbos yra gana gabios rimtame programų kūrime. Dar daugiau, yra tam tikrų sričių kaip lygiagretusis skaičiavimas (ang. *“parallel computations”*) kur toks apribojimas suteikia tam tikros naudos. Studijuoti tokią kalbą (net jeigu neplanuojate jos greitu laiku naudoti) yra rekomenduotina, kad praplėstumėte savo mąstymą. 
=======
Though it may seem a little odd at first sight, these languages are quite capable of serious development. More than that, there are areas like parallel computations where this limitation confers certain benefits.
>>>>>>> 20208769e528337949e946f526534d61d38bac47
```

## Kintamųjų įvardinimas [#variable-naming]

Yra du apribojimai kintamųjų pavadinimams JavaScript:

1. Pavadinimas gali būti sudarytas tik iš raidžių, skaitmenų arba simbolių `$` ir `_`.
2. Pirmas ženklas negali būti skaičius.

Tinkamų pavadinimų pavyzdžiai:

```js
let userName;
let test123;
```

<<<<<<< HEAD
Kai pavadinimas susideda iš kelių žodžių, dažniausiai naudojamas [camelCase](https://en.wikipedia.org/wiki/CamelCase) stilius. Tai reiškia: žodžiai seka vienas kitą, kiekvienas žodis išskyrus pirmąjį prasideda iš didžiosios raidės: `manoLabaiIlgasVardas`.
=======
When the name contains multiple words, [camelCase](https://en.wikipedia.org/wiki/CamelCase) is commonly used. That is: words go one after another, with each word except the first starting with a capital letter: `myVeryLongName`.
>>>>>>> 20208769e528337949e946f526534d61d38bac47

Įdomu -- dolerio `'$'` ir pabrėžimo `'_'` simboliai gali būti naudojami pavadinimuose. Jie yra normalūs simboliai, taip pat kaip raidės, be jokios ypatingos reikšmės.

Šie pavadinimai yra tinkami:

```js run untrusted
let $ = 1; // deklaruotas kintamasis su pavadinimu "$"
let _ = 2; // o dabar kintamasis su pavadinimu "_"

alert($ + _); // 3
```

Pavyzdžiai neteisingų pavadinimų kintamiesiems:

```js no-beautify
let 1a; // negali prasidėti skaičiumi

let my-name; // brūkšniai '-' pavadinime neleidžiami
```

<<<<<<< HEAD
```smart header="Svarbu didžiosios ar mažosios raidės"
Kintamieji su pavadinimais `obuolys` ir `obuoLYS` yra du skirtingi kintamieji.
```

````smart header="Nelotyniškos raidės leidžiamos, bet nerekomenduojamos"
Galima naudoti bet kokią kalbą, įskaitant kirilicos raides ar net hieroglifus:
=======
```smart header="Case matters"
Variables named `apple` and `APPLE` are two different variables.
```

````smart header="Non-Latin letters are allowed, but not recommended"
It is possible to use any language, including Cyrillic letters, Chinese logograms and so on, like this:
>>>>>>> 20208769e528337949e946f526534d61d38bac47

```js
let имя = '...';
let 我 = '...';
```

<<<<<<< HEAD
Techniškai jokios klaidos tame nėra ir tokie pavadinimai yra leistini, tačiau tarptautinė tradicija yra naudoti angliškus kintamųjų pavadinimus. Net jeigu rašome trumpą skriptą, jo gyvenimas gali būti labai ilgas. Kada nors žmonėms iš kitų šalių gali tekti jį perskaityti.
=======
Technically, there is no error here. Such names are allowed, but there is an international convention to use English in variable names. Even if we're writing a small script, it may have a long life ahead. People from other countries may need to read it sometime.
>>>>>>> 20208769e528337949e946f526534d61d38bac47
````

````warn header="Rezervuoti pavadinimai"
Yra [rezervuotų žodžių sąrašas](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#Keywords), kurių negalima naudoti kaip kintamųjų, nes šie žodžiai yra naudojami pačioje kalboje.

Pavyzdžiui: `let`, `class`, `return` ir `function` yra rezervuoti.

Kodas apačioje grąžina sintaksės klaidą:

```js run no-beautify
let let = 5; // negalima kintamojo pavadinti "let", klaida!
let return = 5; // taip pat negalima pavadinti "return", klaida!
```
````

````warn header="Priskyrimas be `use strict`"

Dažniausiai, mums reikia apibrėžti kintamąjį prieš jį naudojant. Bet seniau techniškai buvo galima sukurti kintamąjį tiesiog priskiriant jam vertę ir nenaudojant `let`. Tai vis dar suveikia jeigu mūsų skirptuose nenurodome `use strict` skirtą palaikyti suderinamumą su senaisiais skirptais.

```js run no-strict
// atkreipkite dėmesį: "use strict" nenaudojamas šiame pavyzdyje

num = 5; // sukuriamas kintamasis "num", jeigu neegzistavo prieš tai

alert(num); // 5
```

Tai yra bloga praktika ir grąžina klaidą griežtame režime (ang. *“strict mode”*):

```js
"use strict";

*!*
num = 5; // klaida: num nėra apibrėžtas
*/!*
```
````

## Konstantos

Tam kad deklaruotume konstantą (pastovų) kintamąjį, naudokite `const` vietoje `let`:

```js
const myBirthday = '18.04.1982';
```

Kintamieji deklaruoti naudojant `const` yra vadinami “konstantomis”. Jie negali būti paskirti iš naujo. Bandymas tai padaryti grąžintų klaidą:

```js run
const myBirthday = '18.04.1982';

myBirthday = '01.01.2001'; // klaida, negalima priskirti konstantos iš naujo!
```

<<<<<<< HEAD
Kai programuotojas yra užtikrintas, kad kintamasis niekada nesikeis, gali deklaruoti jį su `const`, kad garantuotų ir aiškiai praneštų šį faktą ir kitiems.

=======
When a programmer is sure that a variable will never change, they can declare it with `const` to guarantee and communicate that fact to everyone.
>>>>>>> 20208769e528337949e946f526534d61d38bac47

### Konstantos didžiosiomis raidėmis

<<<<<<< HEAD
Plačiai paplitusi praktika naudoti konstantas kaip kodinius pavadinimus sunkiai įsimenamoms vertėms, kurios yra jau žinomos prieš atlikimą. 
=======
There is a widespread practice to use constants as aliases for difficult-to-remember values that are known before execution.
>>>>>>> 20208769e528337949e946f526534d61d38bac47

Tokios konstantos pavadinamos naudojant didžiąsias raides ir pabrėžimo ženklą.

Pavyzdžiui, sukurkime konstantas spalvoms su taip vadinamu internetiniu (šešioliktainiu, ang. *“hexadecimal”*) formatu:

```js run
const COLOR_RED = "#F00";
const COLOR_GREEN = "#0F0";
const COLOR_BLUE = "#00F";
const COLOR_ORANGE = "#FF7F00";

// ...kai mums reikia išsirinkti spalvą
let color = COLOR_ORANGE;
alert(color); // #FF7F00
```

Nauda:

- `COLOR_ORANGE` daug lengviau prisiminti nei `"#FF7F00"`.
- Daug lengviau būtų įvelti klaidų spausdinant klaviatūra `"#FF7F00"` negu `COLOR_ORANGE`.
- Skaitant kodą, `COLOR_ORANGE` turės daugiau prasmės nei `#FF7F00`.

Kada turėtume naudoti didžiąsias raides konstantoms ir kada turėtume jas pavadinti normaliu būdu? Išsiaiškinkime.

<<<<<<< HEAD
Būti “konstanta” tereiškia, kad to kintamojo vertė niekada nesikeičia. Bet yra tokių konstantų, kurių vertė yra žinoma prieš kodo atlikimą (kaip pavyzdžiui šešioliktainė raudonos spalvos vertė) ir taip pat yra konstantos, kurios yra *išmatuojamos* (ang. *“calculated”*) veikimo metu kol vykdomas kodas, bet nesikeičia po jų pradinio paskyrimo. 

Pavyzdžiui:
=======
Being a "constant" just means that a variable's value never changes. But some constants are known before execution (like a hexadecimal value for red) and some constants are *calculated* in run-time, during the execution, but do not change after their initial assignment.

For instance:

>>>>>>> 20208769e528337949e946f526534d61d38bac47
```js
const pageLoadTime = /* kiek laiko užtruko paleisti puslapį */;
```

<<<<<<< HEAD
Vertė `pageLoadTime` nebuvo žinoma prieš paleidžiant puslapį, tad pavadinimas užrašytas įprastiniu būdu, bet tai vis dar konstanta, nes ji nesikeičia po paskyrimo.

Kitais žodžiais, didžiosiomis raidėmis pavadintos konstantos yra naudojamos kaip kodiniai žodžiai išanksto sukoduotoms (ang. *“hard-coded”*) vertėms.  
=======
The value of `pageLoadTime` is not known before the page load, so it's named normally. But it's still a constant because it doesn't change after the assignment.

In other words, capital-named constants are only used as aliases for "hard-coded" values.
>>>>>>> 20208769e528337949e946f526534d61d38bac47

## Teisingai įvardykite dalykus

Kalbant apie kintamuosius yra dar vienas labai svarbus punktas.

Kintamojo pavadinimas turi turėti švarią, aiškią reikšmę, apibūdinančią duomenis, kuriuos jis saugo.

<<<<<<< HEAD
Kintamųjų įvardinimas yra viena iš svarbiausių ir sudėtingiausių sugebėjimų programuojant. Žvilgtelėjus į kintamųjų pavadinimus galima nustatyti kurį kodą parašė naujokas, o kurį jau patyręs programuotojas.

Tikrame projekte, daugiausiai laiko yra skiriama modifikuoti ir išplėsti jau esamą kodą negu rašant kažką visiškai naujo nuo pat pradžių. Kai grįžtame prie kodo po to kai kurį laiką darėme kažką kito, daug lengviau kai randi informaciją su aiškiomis etiketėmis. Arba kitaip tariant, kai kintamieji turi gerus pavadinimus.
=======
Variable naming is one of the most important and complex skills in programming. A glance at variable names can reveal which code was written by a beginner versus an experienced developer.

In a real project, most of the time is spent modifying and extending an existing code base rather than writing something completely separate from scratch. When we return to some code after doing something else for a while, it's much easier to find information that is well-labelled. Or, in other words, when the variables have good names.
>>>>>>> 20208769e528337949e946f526534d61d38bac47

Prašau, skirkite laiko sugalvodami kintamajam tinkamą pavadinimą prieš jį deklaruodami. Toks įprotis jums tikrai vėliau atsipirks.

Kelios sektinos taisyklės:

<<<<<<< HEAD
- Naudokite žmogui lengvai perskaitomus pavadinimus, kaip `userName` arba `shoppingCart`.
- Laikykitės atokiau nuo sutrumpinimų arba trumpų pavadinimų kaip `a`, `b`, `c`, nebent tikrai žinote ką darote.
- Pavadinimus kurkite kaip galima labiau apibūdinančius, bet glaustus. Pavyzdžiui blogi pavadinimai yra tokie kaip `data` ir `value`. Tokie pavadinimai nieko nesako. Tinka tik tokiu atveju jeigu kodo turinys yaptingai aiškiai parodo, į kuriuos “data” arba “value” kintamasis nurodo.
- Susitarkite dėl terminų su komanda ir savo mintyse. Jeigu lankytojas puslapyje yra vadinamas “user” tai ir susiję kintamieji turi būti pavadinti `currentUser` arba `newUser` vietoje `currentVisitor` arba `newManInTown`.
=======
- Use human-readable names like `userName` or `shoppingCart`.
- Stay away from abbreviations or short names like `a`, `b`, and `c`, unless you know what you're doing.
- Make names maximally descriptive and concise. Examples of bad names are `data` and `value`. Such names say nothing. It's only okay to use them if the context of the code makes it exceptionally obvious which data or value the variable is referencing.
- Agree on terms within your team and in your mind. If a site visitor is called a "user" then we should name related variables `currentUser` or `newUser` instead of `currentVisitor` or `newManInTown`.
>>>>>>> 20208769e528337949e946f526534d61d38bac47

Skamba paprastai? Iš tikrųjų taip ir yra, bet praktikoje sukurti apibūdinančius ir tuo pačiu glaustus kintamųjų pavadinimus nėra lengva. Pabandykite.

```smart header="Panaudoti vėl ar sukurti naują?"
Ir paskutinė pastaba. Yra tingių programuotojų, kurie vietoje to, kad deklaruotų naujus kintamuosius, mėgsta dar kartą panaudoti jau egzistuojančius.

Dėl to jų kintamieji yra kaip tos dėžės į kurias kiti meta kas papuola nesivargindami pakeisti etikečių. Kas šiuo metu dėžėje? Kas žino. Tam reikia eiti arčiau ir tikrinti. 

Tokie programuotojai šiek tiek sutaupo kintamųjų deklaracijoms, bet praranda dešimt kartų daugiau laiko ieškodami ir taisydami klaidas.

Papildomas kintamasis yra gėris, ne blogis.

Modernios JavaScript minifikatoriai (kitaip - kodo sutrumpintojai, ang. *“minifiers”*) ir naršyklės pakankamai gerai optimizuoja kodą, kad nekiltų veiklos problemų. Naudodami skirtingus kintamuosius, skirtingoms vertėms netgi galite padėti sistemai optimizuoti jūsų kodą.
```

## Santrauka

Mes galime deklaruoti kintamuosius, kad talpintume duomenis naudodami `var`, `let` arba `const` raktažodžius.

- `let` -- yra moderni kintamojo deklaracija.
- `var` -- yra senoviška kintamojo deklaracija. Dažniausiai jo net nenaudojame, bet dar kalbėsime apie subtilius jo skirtumus nuo `let` skyriuje <info:var>, jeigu kartais jums jų reikėtų.
- `const` -- yra panašus į `let`, bet šio kintamojo vertė nebegali būti pakeista.

Kintamieji turi būti pavadinti taip, kad mums būtų lengva suprasti kas yra jų viduje.
