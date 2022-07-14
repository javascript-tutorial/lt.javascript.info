# Kodo struktūra

Pirmas dalykas, kurį studijuosime yra kodo sudėties blokai.

## Pareiškimai

Pareiškimai (ang. Statements) yra sintaksės konstruktai ir komandos, kurios atlieka veiksmus. 

Mes jau matėme šį pareiškimą, `alert('Labas, pasauli!')`, kuris parodo žinutę "Labas, pasauli!".

Mūsų kode gali būti tiek pareiškimų kiek mes norime. Pareiškimai gali būti atskirti kabliataškiu. 

Pavyzdžiui, čia mes atskirsime "Labas Pasauli" į du perspėjimus:

```js run no-beautify
alert('Labas'); alert('Pasauli');
```

Dažniausiai, pareiškimai yra rašomi atskirose eilutėse tam kad kodas būtų lengviau įskaitomas:

```js run no-beautify
alert('Labas');
alert('Pasauli');
```

## Kabliataškiai [#semicolon]

Kabliataškis dažnais atvejais gali būti praleidžiamas, kai pavyzdžiui yra pertrauka tarp eilučių.

Tai irgi suveiktų:

```js run no-beautify
alert('Hello')
alert('World')
```

Čia JavaScript interpretuoja pertrauką eilutėse kaip "numanomą" kabliataški. Tai vadinama [automatišku kabliataškio pridėjimu](https://tc39.github.io/ecma262/#sec-automatic-semicolon-insertion).

**Dažnais atvejais nauja eilutė numanoma kaip kabliataškio pakaitalas. Bet "dažnais atvejais" nereiškia "visada"!**

Yra tokių atvejų kai nauja eilutė nereiškia kabliataškio. Pavyzdiui:

```js run no-beautify
alert(3 +
1
+ 2);
```

Kodas išveda `6`, nes JavaScript čia neįterpia kabliataškio. Intuityviai akivaizdu, kad jei eilutė baigiasi pliusu `"+"`, tai yra "neužbaigta išraiška" (ang. *incomplete expression*), todėl kabliataškis čia būtų neteisingas. Ir šiuo atveju tai veikia taip, kaip numatyta.

**Bet yra situacijų kada JavaScript "nepavyksta" numanyti kabliataškio, kai jo iš tikrųjų reikia.**

Klaidas tokiais atvejais dažnai sunku surasti ir pataisyti.

````smart header="Klaidos pavyzdys"
Jeigu jums smalsu pamatyti tokios klaidos konkretų pavyzdį, patikrinkite sekantį kodą:

```js run
alert("Hello");

[1, 2].forEach(alert);
```

Kol kas negalvokite apie skliaustelius `[]` ir `forEach`. Juos nagrinėsime vėliau. Šiuo metu tiesiog prisiminkite, koks bus šio kodo vykdymo rezultatas: jis rodo `Hello`, tada `1`, paskui `2`.

Dabar pašalinkime kabliataškį po `alert`:

```js run no-beautify
alert("Sveiki")
[1, 2].forEach(alert);
```

Skirtumas, palyginti su pirmiau pateiktu kodu, yra tik vienas simbolis: pirmosios eilutės pabaigoje nebėra kabliataškio.

Jei paleisime šį kodą, pasirodys tik pirmas `Sveiki` (ir klaida, kuriai pamatyti gali tekti atidaryti konsolę). Daugiau skaičių nebėra.

Taip yra dėl to, kad JavaScript nenumato kabliataškio prieš kvadratinius skliaustus [...]. Taigi, paskutiniame pavyzdyje pateiktas kodas laikomas vienu teiginiu.

Štai kaip tai mato variklis:

```js run no-beautify
alert("Hello")[1, 2].forEach(alert);
```

Atrodo keistokai, ar ne? Toks sujungimas šiuo atveju yra tiesiog neteisingas. Kad kodas veiktų teisingai, po `alert` reikia dėti kabliataškį.

Taip gali atsitikti ir kitais atvejais.
````

Mes rekomenduojame dėti kabliataškius pareiškimų pabaigoje net jeigu jie yra atskirose eilutėse. Tokia taisyklė yra plačiai naudojama. Dar kartą prisiminkime -- *įmanoma* daugeliu atvejų kabliataškių nedėti. Bet daug saugiau -- ypač naujokams -- juos naudoti.

## Komentarai [#code-comments]

Laikui bėgant programos tampa vis sudėtingesnės, dėl to svarbu pridėti komentarus (ang. *comments*), kurie paaiškintų ką kodas daro ir kodėl.

Komentarus galima dėti bet kurioje skriptų vietoje. Jie nedaro įtakos kodo atlikimui, nes sistema juos paprasčiausiai ignoruoja.

**Vienos eilutės komentarai prasideda su dviem į priekį pasvirusiais brūkšniais (ang. *forward slashes*) `//`.**

Likusi eilutės dalis yra komentaras. Jis gali užimti pilną eilutę arba užbaigti pareiškimą.

Kaip šiuo atveju:
```js run
// Šis komentaras turi savo eilutę
alert('Labas');

alert('Pasauli'); // Šis komentaras seka paskui pareiškimą
```

**Kelių eilučių komentarai prasideda su pasvirusiu brūkšniu ir žvaigždute <code>/&#42;</code> ir pasibaigia žvaigždute ir pasvirusiu brūkšniu <code>&#42;/</code>.**

Kaip čia:

```js run
/* Pavyzdys su dviem žinutėmis.
Šis komentaras gali būti kelių eilučių.
*/
alert('Labas');
alert('Pasauli');
```

Komentarų turinys yra ignoruojamas, tad jeigu rašysime kodą tarp <code>/&#42; ... &#42;/</code> jis nebus įvykdytas.

Kartais būna naudinga trumpai paslėpti dalį kodo:

```js run
/* Komentaro pagalba paslepiamas kodas
alert('Labas');
*/
alert('Pasauli');
```

```smart header="Use hotkeys!"
Daugumoje redaktorių kodo eilutę galima užkomentuoti paspaudus spartųjį klavišą `key:Ctrl+/` (vienos eilutės komentarui) ir `key:Ctrl+Shift+/` -- kelių eilučių komentarui (pasirinkite kodo dalį ir paspauskite spartųjį klavišą). Jei naudojate Mac, vietoj `key:Ctrl` pabandykite naudoti `key:Cmd`, o vietoj `key:Shift` - `key:Option`.
```

````warn header="Sudedamieji (ang. nested) komentarai nėra galimi!"
Negali būti dar vieno `/*...*/` kitame `/*...*/`.

Toks kodas pasibaigs klaida:

```js run no-beautify
/*
  /* sudedamasis komentaras ?!? */
*/
alert( 'Pasauli' );
```
````

Prašau komentuokite savo kodą kaip galima dažniau.

Komentarai išplečia kodo užimamą vietą, tačiau tai nėra problema. Yra pakankamai įrankių, kurie sumažina kodą prieš jį paleisdami į serverius. Jie panaikina komentarus, kad jie nesimatytų dirbančiame kode, tad komentarai neturi neigiamo efekto produkcijai.

Vėliau pamokose bus skyrius apie kodo kokybę <info:code-quality>, kur taip pat paaiškinama kaip rašyti geresnius komentarus.
