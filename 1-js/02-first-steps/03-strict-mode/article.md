# Šiuolaikinis režimas, "use strict"

Ilgą laiką, JavaScript tobulėjo be jokių problemų dėl suderinamumo. Naujos funkcijos buvo pridedamos nekeičiant senojo funkcionalumo.

Tai buvo naudinga, nes senas jau egzistuojantis kodas galėjo likti nepaveiktas. Tačiau neigiama to pusė yra tai, kad bet kokia klaida ar netobulas sprendimas padarytas JavaScript kūrėjų, užstrigdavo kalboje amžiams.

Taip buvo iki kol 2009 metais atsirado ECMAScript 5 (ES5). Ji pridėjo naujų funkcijų ir patobulino jau egzistuojančias. Kad senasis kodas toliau galėtų veikti, didžioji dalis tokių patobulinimų yra išjunti pagal nutylėjimą. Juos turite aiškiai įgalinti su specialia direktyva: `"use strict"`.

## "use strict"

Direktyva atrodo kaip eilutė (ang. “string”): `"use strict"` arba `'use strict'`. Kai jis rašomas skripto viršuje, visas skriptas leidžiamas “moderniu” būdu.

Pavyzdžiui:

```js
"use strict";

// šis kodas suveiks moderniu būdu
...
```

Mes greitai mokinsimės funkcijas (tam tikras būdas grupuoti komandas), bet užbėgant už akių, galime pažymėti, kad `"use strict"` gali būti dedamas funkcijos pradžioje. Tokiu būdų tik funkcijos korpusas turi griežtą režimą, o ne visas skriptas. Bet dažniausiai žmonės naudoja šį režimą visame skripte.


````warn header="Įsitikinkite, kad \"use strict\" yra viršuje"
Prašau, įsitikinkite, kad `"use strict"` yra jūsų skriptų viršuje, kitu atveju griežtasis režimas gali nesuveikti. 

Šiuo atveju griežtasis režimas nėra įgalintas:

```js no-strict
alert("kažkoks kodas");
// "use strict" esantis apačioje ignoruojamas - jis privalo būti viršuje

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

Kai naudojate [programuotojo konsolę](info:devtools) kodui paleisti, atkreipkite dėmesį, kad pagal numatytuosius nustatymus ji nenaudoja `use strict`.

Kartais, kai `use strict` įtaka yra svarbi, galite gauti neteisingus rezultatus.

Taigi, kaip konsolėje panaudoti `use strict`?

Pirmiausia galite pabandyti paspausti `key:Shift+Enter`, kad įvestumėte kelias eilutes, ir viršuje įrašyti `use strict`, štai taip:

```js
'use strict'; <Shift+Enter perkels jus į naują eilutę>
//  ...
<Paspauskite enter, kad paleistumėte kodą>
```

Tai suveikia didžiojoje dalyje naršyklių, tarp jų Firefox ir Chrome.

Jeigu nesuveikia, pvz., senojoje naršyklėje, yra negražus, bet veiksmingas būdas užtikrinti `use strict`. Įdėkite jį į tokį apvalkalą:

```js
(function() {
  'use strict';

  // ...jūsų kodas...
})()
```

## Ar mums reikia naudoti "use strict"?

Klausimas gali skambėti akivaizdžiai, bet taip nėra.

Galima būtų rekomenduoti pradėti skriptus nuo `"use strict"`... Bet žinote, kas yra šaunu?

Šiuolaikinis JavaScript palaiko "klases" ir "modulius" (ang. “classes/modules”) - pažangias kalbos struktūras (prie jų dar priartėsime), kurios automatiškai įjungia `"use strict"`. Taigi, jei jas naudosime, mums nereikės pridėti direktyvos `"use strict`".

**Taigi, kol kas `"use strict";` yra laukiamas svečias jūsų skriptų viršuje. Vėliau, kai visas jūsų kodas bus sudarytas iš klasių ir modulių, galėsite jo atsisakyti.**

Nuo šiol žinome apie `use strict` apskritai.

Kituose skyriuose, mokydamiesi kalbos funkcijų, pamatysime griežtojo ir senojo režimų skirtumus. Laimei, jų nėra daug ir jie iš tikrųjų pagerina mūsų gyvenimą.

Visuose šio vadovėlio pavyzdžiuose laikoma, kad naudojamas griežtasis režimas, nebent (labai retai) nurodyta kitaip.