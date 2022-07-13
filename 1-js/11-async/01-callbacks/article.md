# Įvadas: callbacks

```warn header="We use browser methods here"
*Callback'ų*, *promise'ų* ir kitų abstrakčių koncepcijų veikimo demonstacijai, bus naudojami naršyklės metodai. Pagrinde bus atliekamos paprastos dokumentų manipuliacijos pasitelkiant skriptus.

Jeigu šie metodai Jums dar nepažįstami, jų naudojimas pavyzdžiuose trikdo ar tiesiog norėtumėte juos suprasti geriau, pamėginkite paskaityti kelis skyrius iš kitos šių pratybų [dalies](/document).
```

Daugelis veiksmų JavaScript'e yra *asinchroniški* (*asynchronous*). Kitaip tariant, mes juos inicijuojame dabar, bet jie įvykdomi vėliau.

Tokį veiksmą ateičiai mes galime suplanuoti naudodami `setTimeout` metodą.

Egzistuoja ir kiti asinchroninių veiksmų pavyzdžiai, tarkime, skriptų ir modulių (*modules*) užkrovimas (juos aptarsime vėlesniuose skyriuose).

Pažvelkite į `loadScript(src)` funkciją, kurį užkrauna skriptą su pateiktu `src`:

```js
function loadScript(src) {
  let script = document.createElement('script');
  script.src = src;
  document.head.append(script);
}
```

Ši funkcija prideda (*appends*) naują, dinamiškai sukurtą žymą (*tag*) `<script src="…">`. Naršyklės ją užkrauna ir įvykdo.

Šią funkciją mes galime panaudoti šitaip:

```js
// užkrauti ir vykdyti nurodytoje vietoje esantį skriptą
loadScript('/my/script.js');
```

Skriptas yra vykdomas „asinchroniškai“. Jis pradeda krautis dabar, bet įvykdomas vėliau, kai funkcijos vykdymas jau būna pasibaigęs.

Jeigu po `loadScript(…)` yra papildomas kodas, jis nelauks kol pasibaigs skripto krovimasis.

```js
loadScript('/my/script.js');
// kodas žemiau loadScript
// nelauks kol šio skripto krovimasis baigsis
// ...
```

Sakykime, mes norime panaudoti skriptą, kai tik jis užsikraus – galbūt jis deklaruoja naujas funkcijas ir mes norime jas naudoti.

Bet šitai nesuveiks, jei to imsimės tuoj po `loadScript(…)` iškvietimo:

```js
loadScript('/my/script.js'); // skriptas savyje turi funkciją "function newFunction() {…}"

*!*
newFunction(); // toksios funkcijos nėra!
*/!*
```

Suprantama, naršyklė, greičiausiai, neturėjo laiko užkrauti skriptui. Nuo šio momento funkcija `loadScript` nesuteikia galimybės sekti užsikrovimo baigties. Skriptas užsikrauna ir tiesiog yra įvykdomas. Bet mūsų tikslas yra žinoti, kada tai įvyksta, kad galėtume naudoti minėto skripto sukurtas naujas funkcijas ir kintamuosius.

Pridėkime `callback` funkciją kaip antrą `loadScript` funkcijos argumentą, kuri turėtų būti vykdoma, kai skriptas užsikraus:

```js
function loadScript(src, *!*callback*/!*) {
  let script = document.createElement('script');
  script.src = src;

*!*
  script.onload = () => callback(script);
*/!*

  document.head.append(script);
}
```

Jeigu mes norime iškviesti naujas funkcijas iš skripto, mes turėtume tai aprašyti *callback'e*:

```js
loadScript('/my/script.js', function() {
  // callback'as vykdomas po skripto užsikrovimo
  newFunction(); // dabar fukncija veikia
  ...
});
```

Idėja tokia: antrasis argumentas yra funkcija (dažniausia anoniminė), kuri paleidžiama, kai veiksmas yra užbaigtas.

Štai veikiantis pavyzdys su realiu skriptu:

```js run
function loadScript(src, callback) {
  let script = document.createElement('script');
  script.src = src;
  script.onload = () => callback(script);
  document.head.append(script);
}

*!*
loadScript('https://cdnjs.cloudflare.com/ajax/libs/lodash.js/3.2.0/lodash.js', script => {
  alert(`Cool, the script ${script.src} is loaded`);
  alert( _ ); // funkcija deklaruota užkrautame skripte
});
*/!*
```

Tai vadinama *callback'ais* grįstu (*callback-based*) asinchroniniu programavimu – kažką asinchroniškai vykdanti funkcija, turėtų savyje turėti *callback* argumentą, į kurią galima įdėti kitą funkciją, įvykdomą pirmajai pasibaigus.

Mes panašiai paderėme pavyzdynėje `loadScript` funkcijoje.

## Callback funkcija callback funkcijoje

O kaip paleisti du skriptus paeiliui? Pirmą, o po jo – antrą.

Naturalus sprendimas būtų įdėti antrąjį `loadScript` iškvietimą *callback'e*, štai taip:

```js
loadScript('/my/script.js', function(script) {

  alert(`Cool, the ${script.src} is loaded, let's load one more`);

*!*
  loadScript('/my/script2.js', function(script) {
    alert(`Cool, the second script is loaded`);
  });
*/!*

});
```

Kai išorinė `loadScript` funkcija įvykdoma, *callback'as* inicijuoja vidinę.

O kas, jeigu mums reikalingas dar vienas skriptas?

```js
loadScript('/my/script.js', function(script) {

  loadScript('/my/script2.js', function(script) {

*!*
    loadScript('/my/script3.js', function(script) {
      // ...tęsti tik visiems skriptams užsikrovus
    });
*/!*

  })

});
```

Taigi, kekviena nauja operacija yra *callback'o* viduje. Tai priimtina nedideliam kiekiui operacijų. Kitus šios problemos spredimo būdus aptarsime netrukus.

## Klaidų valdymas

Ankstesniuose pavyzdžiuose mes visiškai nekalbėjome apie klaidas (*errors*). Kas, jei skripto krovimasis nepavyksta? Tokiu atveju mūsų *callback'as* turėtų sugebėti į tai reaguoti.

Štai patobulinta `loadScript` versija, kuri suseka krovimosi klaidas.

```js
function loadScript(src, callback) {
  let script = document.createElement('script');
  script.src = src;

*!*
  script.onload = () => callback(null, script);
  script.onerror = () => callback(new Error(`Script load error for ${src}`));
*/!*

  document.head.append(script);
}
```

Ji iškviečia `callback(null, script)` sėkmingam krovimui ir `callback(error)` – nesėkmingam.

Panaudojimas:
```js
loadScript('/my/script.js', function(error, script) {
  if (error) {
    // apdoroti klaidą
  } else {
    // skriptas užkrautas sėkmingai
  }
});
```

Būdas, kuriuo mes pasinaudojome paleisti `loadScript`, yra gan dažnas. Jis pirmenybę teikia klaidų valdymui *callback'ais* ("error-first callback style").

Šio stiliaus konvencija teigia:
1. Pirmasis *callback'o* argumentas yra rezervuotas klaidai, jei jį pasitaikys. Čia kviečiama `callback(err)` funkcija.
2. Antrasis argumentas (ir tolimesni, jei jie reikalingi) yra skirtas sėkmingam rezultatui. Tuomet kviečiama `callback(null, result1, result2…)` funkcija.

Taigi, viena `callback` funkcija yra tinkama ir informavimui apie klaidas ir rezultatų grąžinimui.

## „Pražūties piramidė“ (Pyramid of Doom)

Iš pirmo žvilgstio – tai geras būdas asinchroniniam kodavimui. Vienam ar dviem sugrupuotiems funkcijų iškvietimams jis tikrai tinka.

Bet didesniam kiekiui viena kitą sekančių asinchroninių operacijų mes turėsime štai tokį kodą:

```js
loadScript('1.js', function(error, script) {

  if (error) {
    handleError(error);
  } else {
    // ...
    loadScript('2.js', function(error, script) {
      if (error) {
        handleError(error);
      } else {
        // ...
        loadScript('3.js', function(error, script) {
          if (error) {
            handleError(error);
          } else {
  *!*
            // ...tęsti užsikrovus visiems skriptams (*)
  */!*
          }
        });

      }
    })
  }
});
```

Šiame kode:
1. Mes krauname `1.js`, tuomet, jei nėra klaidų.
2. Mes krauname `2.js`, tuomet, jei nėra klaidų.
3. Mes krauname `3.js`, tuomet, jei nėra klaidų – darome kažką kito `(*)`.

Visi funkcijų iškvietimai tampa vis labiau sugrupuoti, kodas gilėja ir tampa sunkiai suvaldomu. Ypač, jei vietoj daugtaškių `...` turime tikrą kodą, su ciklais (*loops*), sąlyginėmis išraiškomis (*conditional statements*) ir t.t.

Tai kartais vadinama „*callback'ų* pragaru“ arba „pražūties piramide“.

<!--
loadScript('1.js', function(error, script) {
  if (error) {
    handleError(error);
  } else {
    // ...
    loadScript('2.js', function(error, script) {
      if (error) {
        handleError(error);
      } else {
        // ...
        loadScript('3.js', function(error, script) {
          if (error) {
            handleError(error);
          } else {
            // ...
          }
        });
      }
    })
  }
});
-->

![](callback-hell.svg)

Sugrupuotų funkcijų iškvietimų piramidė auga su kiekviena asinchronine operacija ir greitai tampa nekontroliuojama.

Todėl toks kodo rašymo būdas nėra labai geras.

Galime sušvelninti padėtį paversdami kiekvieną veiksmą savarankiška funkcija štai taip:

```js
loadScript('1.js', step1);

function step1(error, script) {
  if (error) {
    handleError(error);
  } else {
    // ...
    loadScript('2.js', step2);
  }
}

function step2(error, script) {
  if (error) {
    handleError(error);
  } else {
    // ...
    loadScript('3.js', step3);
  }
}

function step3(error, script) {
  if (error) {
    handleError(error);
  } else {
    // ...tęsti užsikrovus visiems skriptams (*)
  }
};
```

Matote? Ji daro tą patį, bet šiuo atveju nebeliko komplikuoto operacijų grupavimo, nes kiekvieną veiksmą mes pavertėme atskira *top-level* funkcija.

Viskas veikia, tačiau kodas atrodo prastai. Jis sunkiai skaitomas, o skaitytojas turi šokinėti nuo vienos kodo dalies prie kitos. Tai nepatogu, ypač jei skaitantysis nėra susipažinęs su šiuo kodu ir tiksliai nežino, kur ieškoti reikiamos kodo dalies.

Taipogi, funkcijos pavadinimu `step*` yra vienkartinės ir sukurtus tik „pražūties piramidei“ išvengti. Jos nebebus panaudoto šios kodo grandinės išorėje, tad susiduriame su vardų srities (*namespace*) teršimu.

Mums reikėtų kažko geresnio.

Laimei, yra kitų būdų išvengti minėtų „piramidžių“. Geriausias būdas yra naudoti „pažadus“ (*promises*), aptariamus kitame skyriuje.
