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

Mes greitai mokinsimės funkcijas (tam tikras būdas grupuoti komandas), bet žiūrint į priekį, galime pažymėti, kad `"use strict"` gali būti dedamas funkcijos pradžioje. Tokiu būdų tik funkcijos korpusas (ang. "body") turi griežtą režimą, o ne visas skriptas. Bet dažniausiai žmonės naudoja šį režimą visame skripte.


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

Kai jau įžengiame į griežtą režimą, kelio atgal nebėra.
```

## Naršyklės konsolė

Ateičiai, kai naudosite naršyklės konsolės testavimo funkcijas, žinokite, kad ji nenaudoja `use strict` pagal numatytus nustatymus.

Kartais, kai `use strict` įtaka yra svarbi, galite gauti neteisingus rezultatus.

Norėdami konsolėje suvesti daugiau nei vieną eilutę paspauskite `key:Shift+Enter`, tokiu būdu galite užrašyti `use strict` viršuje, štai taip:

```js
'use strict'; <Shift+Enter perkels jus į naują eilutę>
//  ...
<Paspauskite enter, kad paleistumėte kodą>
```

Tai suveikia didžiojoje dalyje naršyklių, tarp jų Firefox ir Chrome.

Jeigu nesuveikia, geriausias būdas įsitikinti, kad `use strict` veiks, kai kodas konsolėje paleidžiamas tokiu būdu:

```js
(function() {
  'use strict';

  // ...jūsų kodas...
})()
```

## Visada naudokite "use strict"

Dar aptarsime skirtumus tarp griežto režimo ir numatytojo (ang. "default") režimo.

Sekančiuose skyriuose, kai mokinsimės kalbos savybes, pastebėsime skirtumus tarp griežto ir numatyto režimo. Laimei, jų nėra labai daug ir jie iš tikrųjų palengvina mūsų gyvenimus. 

Kol kas užtenka žinoti apie tai pagrindinius dalykus:

1. Naudojant direktyvą `"use strict"` sistema persijungia į "modernų" režimą, pakeisdama kai kurių įmontuotų savybių elgseną. Detaliau apie tai pamatysite vėlesnėse pamokose.
2. Griežtas režimas paleidžiamas užrašant `"use strict"` skripto arba funkcijos viršuje. Kai kurios kalbos savybės, kaip klasės (ang. "classes") ir modulia (ang. "modules") griežtą režimą paleidžia automatiškai.
3. Griežtą režimą palaiko visos modernios naršyklės.
4. Rekomenduojame visus skriptus pradėti su `"use strict"`. Visi šių pamokų pavyzdžiai numano, kad griežtas režimas yra naudojamas, nebent (labai retais atvejais) yra nurodoma kitaip. 
