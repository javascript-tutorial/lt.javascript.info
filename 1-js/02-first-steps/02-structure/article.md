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

Kodas mums atiduoda `6`, nes JavaScript šiuo atveju neįterpia kabliataškio tarp eilučių. Intuityviai akivaizdu, kad jeigu eilutė pasibaigia pliusu `"+"`, tai yra nepabaigta išraiška (ang. "incomplete expression"), tokiu atveju kabliataškis nereikalingas. O kodas suveikia taip kaip buvo tikėtasi.

**Bet yra situacijų kada JavaScript "nepavyksta" numanyti kabliataškio, kai jo iš tikrųjų reikia.**

Klaidas tokiais atvejais dažnai sunku surasti ir pataisyti.

````smart header="Klaidos pavyzdys"
Jeigu jums smalsu pamatyti tokios klaidos konkretų pavyzdį, patikrinkite sekantį kodą:

```js run
[1, 2].forEach(alert)
```

Kol kas negalvokite apie šiuos skliaustelius `[]` ir `forEach`. Juos studijuosime vėliau. Jums reikia tik prisiminti kodo rezultatą: jis rodo `1` tada `2`.

O dabar pridėkime `alert` prieš kodą ir *neužbaikime* jo su kabliataškiu:

```js run no-beautify
alert("Tai bus klaida")

[1, 2].forEach(alert)
```

Dabar jeigu paleisime šį kodą, tik pirmasis `alert` pasirodo, o tada gauname klaidą!

Bet jeigu pridedame kabliataškį po `alert` vėl viskas gerai:
```js run
alert("Dabar viskas gerai");

[1, 2].forEach(alert)  
```

Gauname "Dabar viskas gerai" žinutę, kurią seka `1` ir `2`.


Klaida variante be kabliataškio atsiranda dėl to, kad JavaScript nenumato galimo kabliataškio prieš laužtinius skliaustelius `[...]`.

Kadangi kabliataškis nėra automatiškai įtraukiamas, pirmojo pavyzdžio kodas laikomas vienu pilnu pareiškimu. Štai kaip jį mato sistema:

```js run no-beautify
alert("Tai bus klaida")[1, 2].forEach(alert)
```

Bet tai turėtų būti du atskiri pareiškimai, ne vienas. Toks sujungimas šiuo atveju yra neteisingas, dėl to ir gauname klaidą. Taip gali nutikti ir kitose situacijose.
````

Mes rekomenduojame dėti kabliataškius pareiškimų pabaigoje net jeigu jie yra atskirose eilutėse. Tokia taisyklė yra plačiai naudojama. Dar kartą prisiminkime -- *įmanoma* daugeliu atvejų kabliataškių nedėti. Bet daug saugiau -- ypač naujokams -- juos naudoti.

## Komentarai

Laikui bėgant programos tampa vis sudėtingesnės, dėl to svarbu pridėti komentarus (ang. *comments*), kurie paaiškintų ką kodas daro ir kodėl.

Komentarus galima dėti bet kurioje skriptų vietoje. Jie nedaro įtakos kodo atlikimui, nes sistema juos paprasčiausiai ignoruoja.

**Vienos eilutės komentarai prasideda su dviem į priekį pasvirusiais brūkšniais (ang. forward slashes) `//`.**

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
Didžiojoje dalyje redaktorių vieno kodo eilutė gali būti paversta komentaru spaudžiant klaviatūroje vienu metu `key:Ctrl+/`, o kelių eilučių komentaras gaunamas spaudžiant `key:Ctrl+Shift+/` -- (išbandykite tai patys su savo kodu). Mac kompiuteriuose, naudokite `key:Cmd` vietoje `key:Ctrl`.
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
