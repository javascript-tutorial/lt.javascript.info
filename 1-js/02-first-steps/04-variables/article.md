# Kintamieji (ang. variables)

Dažniausiai JavaScript paraiška turi dirbti su informacija. Štai du pavyzdžiai:
1. Internetinė parduotuvė -- informacija gali apimti parduodamas prekes ir pirkimo krepšelį.
2. Pokalbių programėlė -- informacija gali apimti vartotojus, žinutes ir daug daugiau.

Kintamieji yra naudojami tam, kad kauptų šią informaciją. 

## Kintamasis

[Kintamasis](https://en.wikipedia.org/wiki/Variable_(computer_science)) yra "įvardinta saugykla" duomenims. Mes galime naudoti kintamuosius, kad kauptume gėrybes, lankytojus ir kitus duomenis.

Norėdami sukurti kintamąjį su JavaScript, naudokite `let` raktinį žodį (ang. "keyword").

Žemiau esantis pareiškimas sukuria (kitais žodžiais: *declaruoja* ang.*declares*) kintamąjį su pavadinimu "message":

```js
let message;
```

Dabar į jį galime patalpinti duomenis naudodami užduoties operatorių `=`:

```js
let message;

*!*
message = 'Labas'; // patalpinama eilutė
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

Dėl glaustumo galime sujungti kintamojo deklaraciją ir užduotį į vieną eilę:

```js run
let message = 'Labas!'; // apibrėžti kintamąjį ir priskirti jam vertę

alert(message); // Labas!
```

Mes taip pat galime deklaruoti kelis kintamuosius vienoje eilėje:

```js no-beautify
let user = 'John', age = 25, message = 'Labas';
```

Tai atrodo trumpiau, bet iš tikrųjų mes nerekomenduojame taip daryti. Tam, kad būtų lengviau perskaityti kodą, prašau, naudokite vieną eilę kiekvienam kintamajam.

Kelių eilučių variantas ilgesnis, bet jį lengviau perskaityti:

```js
let user = 'John';
let age = 25;
let message = 'Labas';
```

Kai kurie žmonės apibrėžia kelis kintamuosius tokiu kelių eilių stiliumi:
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
Senesniuose skriptuose galite rasti raktažodį: `var` vietoje `let`:

```js
*!*var*/!* message = 'Labas';
```

Raktažodis `var` yra *beveik* tas pats kaip `let`. Jis taip pat deklaruoja kintamąjį, bet šiekt eik kitokiu, "senoviniu" būdu.

Yra subtilūs skirtumai tarp `let` ir `var`, bet kol kas jie mums nėra svarbūs. Mes apie juos kalbėsime detaliau skyriuje <info:var>.
````

## Tikro gyvenimo analogija

Mes galime lengviau suprasti "kintamojo" sąvoką jeigu įsivaizduotume jį kaip "dėžę" skirtą duomenims ant kurios priklijuotas unikaliai pavadintas lipdukas.

Pavyzdžiui kintamąjį `message` galime įsivaizduoti kaip dėžę su etikete `"message"`, kurios viduje yra patalpinta vertė `"Labas!"`:

![](variable.svg)

Mes galime į dėžę įdėti bet kokią vertę.

Mes taip pat galime ją pakeisti kiek norime kartų:
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

```smart header="Funkcinės kalbos"
Yra įdomu pastebėti, kad egzistuoja [funkcinės](https://en.wikipedia.org/wiki/Functional_programming) programavimo kalbos, tokios kaip [Scala](http://www.scala-lang.org/) arba [Erlang](http://www.erlang.org/), kurios draudžia keisti kintamųjų vertes.

Tokiose kalbose, kai vertė yra patalpinama "į dėžę", ji ten ir pasilieka amžiams. Jeigu norime patalpinti kažką kito, kalba mus priverčia sukurti naują dėžę (deklaruoti naują kintamąjį). Mes nebegalime dar kartą panaudoti senojo.

Nors tai atrodo keistai iš pirmo žvilgsnio, tačiau šios kalbos yra gana gabios rimtame programų kūrime. Dar daugiau, yra tam tikrų sričių kaip lygiagretusis skaičiavimas (ang. "parallel computations") kur toks apribojimas suteikia tam tikros naudos. Studijuoti tokią kalbą (net jeigu neplanuojate jos greitu laiku naudoti) yra rekomenduotina, kad praplėstumėte savo mąstymą. 
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

Kai pavadinimas susideda iš kelių žodžių, dažniausiai naudojamas [camelCase](https://en.wikipedia.org/wiki/CamelCase) (tiesioginis vertimas - kupranugario atvejis). Tai reiškia: žodžiai seka vienas kitą, kiekvienas žodis išskyrus pirmąjį prasideda iš didžiosios raidės: `manoLabaiIlgasVardas`.

Įdomu -- dolerio `'$'` ir pabrėžimo `'_'` ženklai gali būti naudojami pavadinimuose. Jie yra normalūs simboliai, taip pat kaip raidės, be jokios ypatingos reikšmės.

These names are valid:

```js run untrusted
let $ = 1; // declared a variable with the name "$"
let _ = 2; // and now a variable with the name "_"

alert($ + _); // 3
```

Examples of incorrect variable names:

```js no-beautify
let 1a; // cannot start with a digit

let my-name; // hyphens '-' aren't allowed in the name
```

```smart header="Case matters"
Variables named `apple` and `AppLE` are two different variables.
```

````smart header="Non-Latin letters are allowed, but not recommended"
It is possible to use any language, including cyrillic letters or even hieroglyphs, like this:

```js
let имя = '...';
let 我 = '...';
```

Technically, there is no error here, such names are allowed, but there is an international tradition to use English in variable names. Even if we're writing a small script, it may have a long life ahead. People from other countries may need to read it some time.
````

````warn header="Reserved names"
There is a [list of reserved words](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#Keywords), which cannot be used as variable names because they are used by the language itself.

For example: `let`, `class`, `return`, and `function` are reserved.

The code below gives a syntax error:

```js run no-beautify
let let = 5; // can't name a variable "let", error!
let return = 5; // also can't name it "return", error!
```
````

````warn header="An assignment without `use strict`"

Normally, we need to define a variable before using it. But in the old times, it was technically possible to create a variable by a mere assignment of the value without using `let`. This still works now if we don't put `use strict` in our scripts to maintain compatibility with old scripts.

```js run no-strict
// note: no "use strict" in this example

num = 5; // the variable "num" is created if it didn't exist

alert(num); // 5
```

This is a bad practice and would cause an error in strict mode:

```js
"use strict";

*!*
num = 5; // error: num is not defined
*/!*
```
````

## Constants

To declare a constant (unchanging) variable, use `const` instead of `let`:

```js
const myBirthday = '18.04.1982';
```

Variables declared using `const` are called "constants". They cannot be reassigned. An attempt to do so would cause an error:

```js run
const myBirthday = '18.04.1982';

myBirthday = '01.01.2001'; // error, can't reassign the constant!
```

When a programmer is sure that a variable will never change, they can declare it with `const` to guarantee and clearly communicate that fact to everyone.


### Uppercase constants

There is a widespread practice to use constants as aliases for difficult-to-remember values that are known prior to execution.

Such constants are named using capital letters and underscores.

For instance, let's make constants for colors in so-called "web" (hexadecimal) format:

```js run
const COLOR_RED = "#F00";
const COLOR_GREEN = "#0F0";
const COLOR_BLUE = "#00F";
const COLOR_ORANGE = "#FF7F00";

// ...when we need to pick a color
let color = COLOR_ORANGE;
alert(color); // #FF7F00
```

Benefits:

- `COLOR_ORANGE` is much easier to remember than `"#FF7F00"`.
- It is much easier to mistype `"#FF7F00"` than `COLOR_ORANGE`.
- When reading the code, `COLOR_ORANGE` is much more meaningful than `#FF7F00`.

When should we use capitals for a constant and when should we name it normally? Let's make that clear.

Being a "constant" just means that a variable's value never changes. But there are constants that are known prior to execution (like a hexadecimal value for red) and there are constants that are *calculated* in run-time, during the execution, but do not change after their initial assignment.

For instance:
```js
const pageLoadTime = /* time taken by a webpage to load */;
```

The value of `pageLoadTime` is not known prior to the page load, so it's named normally. But it's still a constant because it doesn't change after assignment.

In other words, capital-named constants are only used as aliases for "hard-coded" values.  

## Name things right

Talking about variables, there's one more extremely important thing.

A variable name should have a clean, obvious meaning, describing the data that it stores.

Variable naming is one of the most important and complex skills in programming. A quick glance at variable names can reveal which code was written by a beginner versus an experienced developer.

In a real project, most of the time is spent modifying and extending an existing code base rather than writing something completely separate from scratch. When we return to some code after doing something else for a while, it's much easier to find information that is well-labeled. Or, in other words, when the variables have good names.

Please spend time thinking about the right name for a variable before declaring it. Doing so will repay you handsomely.

Some good-to-follow rules are:

- Use human-readable names like `userName` or `shoppingCart`.
- Stay away from abbreviations or short names like `a`, `b`, `c`, unless you really know what you're doing.
- Make names maximally descriptive and concise. Examples of bad names are `data` and `value`. Such names say nothing. It's only okay to use them if the context of the code makes it exceptionally obvious which data or value the variable is referencing.
- Agree on terms within your team and in your own mind. If a site visitor is called a "user" then we should name related variables `currentUser` or `newUser` instead of `currentVisitor` or `newManInTown`.

Sounds simple? Indeed it is, but creating descriptive and concise variable names in practice is not. Go for it.

```smart header="Reuse or create?"
And the last note. There are some lazy programmers who, instead of declaring new variables, tend to reuse existing ones.

As a result, their variables are like boxes into which people throw different things without changing their stickers. What's inside the box now? Who knows? We need to come closer and check.

Such programmers save a little bit on variable declaration but lose ten times more on debugging.

An extra variable is good, not evil.

Modern JavaScript minifiers and browsers optimize code well enough, so it won't create performance issues. Using different variables for different values can even help the engine optimize your code.
```

## Summary

We can declare variables to store data by using the `var`, `let`, or `const` keywords.

- `let` -- is a modern variable declaration.
- `var` -- is an old-school variable declaration. Normally we don't use it at all, but we'll cover subtle differences from `let` in the chapter <info:var>, just in case you need them.
- `const` -- is like `let`, but the value of the variable can't be changed.

Variables should be named in a way that allows us to easily understand what's inside them.
