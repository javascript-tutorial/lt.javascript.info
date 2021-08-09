# Šiuolaikinis režimas, "use strict"

Ilgą laiką, JavaScript tobulėjo be jokių problemų dėl suderinamumo. Naujos funkcijos buvo pridedamos nekeičiant senojo funkcionalumo.

Tai buvo naudinga, nes senas jau egzistuojantis kodas galėjo likti nepaveiktas. Tačiau neigiama to pusė yra tai, kad bet kokia klaida ar netobulas sprendimas padarytas JavaScript kūrėjų, užstrigdavo kalboje amžiams.

Taip buvo iki kol 2009 metais atsirado ECMAScript 5 (ES5). Ji pridėjo naujų funkcijų ir patobulino jau egzistuojančias. Kad senasis kodas toliau galėtų veikti, didžioji dalis tokių patobulinimų yra išjunti pagal nutylėjimą. Juos turite aiškiai įgalinti su specialia direktyva: `"use strict"`(vert. naudoti griežtą).

## "use strict"

Direktyva atrodo kaip vėrinys (ang. "string"): `"use strict"` arba `'use strict'`. Kai jis rašomas skripto viršuje, visas skriptas leidžiamas "moderniu" būdu.

Pavyzdžiui:

```js
"use strict";

// šis kodas suveiks moderniu būdu
...
```

<<<<<<< HEAD
Mes greitai mokinsimės funkcijas (tam tikras būdas grupuoti komandas), bet užbėgant už akių, galime pažymėti, kad `"use strict"` gali būti dedamas funkcijos pradžioje. Tokiu būdų tik funkcijos korpusas (ang. "body") turi griežtą režimą, o ne visas skriptas. Bet dažniausiai žmonės naudoja šį režimą visame skripte.

=======
Quite soon we're going to learn functions (a way to group commands), so let's note in advance that `"use strict"` can be put at the beginning of a function. Doing that enables strict mode in that function only. But usually people use it for the whole script.
>>>>>>> bc08fd1b32285304b14afea12a9deaa10d13452b

````warn header="Įsitikinkite, kad \"use strict\" yra viršuje"
Prašau, įsitikinkite, kad `"use strict"` yra jūsų skriptų viršuje, kitu atveju griežtasis režimas gali nesuveikti. 

Šiuo atveju griežtasis režimas nėra įgalintas:

```js no-strict
alert("kažkoks kodas");
// "use strict" esantis apačioje ignoruojamas--jis privalo būti viršuje

"use strict";

// griežtas režimas neaktyvuotas
```

Anksčiau už `"use strict"` gali būti tik komentarai.
````

```warn header="Nėra būdo kaip atšaukti `use strict`"
Nėra tokios direktyvos kaip `"no use strict"`, kuris sugrąžintų sistemą į senąjį funkcionavimą.

<<<<<<< HEAD
Kai jau įžengiame į griežtą režimą, kelio atgal nebėra.
=======
Once we enter strict mode, there's no going back.
>>>>>>> bc08fd1b32285304b14afea12a9deaa10d13452b
```

## Naršyklės konsolė

<<<<<<< HEAD
Ateičiai, kai naudosite naršyklės konsolės testavimo funkcijas, žinokite, kad ji nenaudoja `use strict` pagal numatytus nustatymus.
=======
When you use a [developer console](info:devtools) to run code, please note that it doesn't `use strict` by default.
>>>>>>> bc08fd1b32285304b14afea12a9deaa10d13452b

Kartais, kai `use strict` įtaka yra svarbi, galite gauti neteisingus rezultatus.

<<<<<<< HEAD
Norėdami konsolėje suvesti daugiau nei vieną eilutę paspauskite `key:Shift+Enter`, tokiu būdu galite užrašyti `use strict` viršuje, štai taip:
=======
So, how to actually `use strict` in the console?

First, you can try to press `key:Shift+Enter` to input multiple lines, and put `use strict` on top, like this:
>>>>>>> bc08fd1b32285304b14afea12a9deaa10d13452b

```js
'use strict'; <Shift+Enter perkels jus į naują eilutę>
//  ...
<Paspauskite enter, kad paleistumėte kodą>
```

Tai suveikia didžiojoje dalyje naršyklių, tarp jų Firefox ir Chrome.

<<<<<<< HEAD
Jeigu nesuveikia, geriausias būdas įsitikinti, kad `use strict` veiks, kai kodas konsolėje paleidžiamas tokiu būdu:
=======
If it doesn't, e.g. in an old browser, there's an ugly, but reliable way to ensure `use strict`. Put it inside this kind of wrapper:
>>>>>>> bc08fd1b32285304b14afea12a9deaa10d13452b

```js
(function() {
  'use strict';

<<<<<<< HEAD
  // ...jūsų kodas...
})()
```

## Visada naudokite "use strict"

Dar aptarsime skirtumus tarp griežto režimo ir numatytojo (ang. "default") režimo.

Sekančiuose skyriuose, kai mokinsimės kalbos savybes, pastebėsime skirtumus tarp griežto ir numatyto režimo. Laimei, jų nėra labai daug ir jie iš tikrųjų palengvina mūsų gyvenimus. 

Kol kas užtenka žinoti apie tai pagrindinius dalykus:

1. Naudojant direktyvą `"use strict"` sistema persijungia į "modernų" režimą, pakeisdama kai kurių įmontuotų savybių elgseną. Detaliau apie tai pamatysite vėlesnėse pamokose.
2. Griežtas režimas paleidžiamas užrašant `"use strict"` skripto arba funkcijos viršuje. Kai kurios kalbos savybės, kaip klasės (ang. "classes") ir moduliai (ang. "modules") griežtą režimą paleidžia automatiškai.
3. Griežtą režimą palaiko visos modernios naršyklės.
4. Rekomenduojame visus skriptus pradėti su `"use strict"`. Visi šių pamokų pavyzdžiai numano, kad griežtas režimas yra naudojamas, nebent (labai retais atvejais) yra nurodoma kitaip. 
=======
  // ...your code here...
})()
```

## Should we "use strict"?

The question may sound obvious, but it's not so.

One could recommend to start scripts with `"use strict"`... But you know what's cool?

Modern JavaScript supports "classes" and "modules" - advanced language structures (we'll surely get to them), that enable `use strict` automatically. So we don't need to add the `"use strict"` directive, if we use them.

**So, for now `"use strict";` is a welcome guest at the top of your scripts. Later, when your code is all in classes and modules, you may omit it.**

As of now, we've got to know about `use strict` in general.

In the next chapters, as we learn language features, we'll see the differences between the strict and old modes. Luckily, there aren't many and they actually make our lives better.

All examples in this tutorial assume strict mode unless (very rarely) specified otherwise.
>>>>>>> bc08fd1b32285304b14afea12a9deaa10d13452b
