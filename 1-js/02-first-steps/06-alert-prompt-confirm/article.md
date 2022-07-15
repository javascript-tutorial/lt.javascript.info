# Interakcija: alert, prompt, confirm

Kadangi kaip demonstracinę aplinką mes naudosime naršyklę, pažiūrėkime keletą funkcijų, skirtų interakcijai su naudotoju: `alert`, `prompt` ir `confirm`.

## alert

Šitą jau matėme. Jis rodo pranešimą ir laukia, kol naudotojas paspaus "OK".

Pavyzdžiui:

```js run
alert("Labas");
```

Miniatiūrinis langelis su žinute yra vadinamas *modaliniu langeliu* (ang. “*modal window*”). Žodis “modalinis” reiškia, kad lankytojas negali naudotis puslapiu, spausti kitų mygtukų ir t.t. kol nesusitvarkė su langeliu. Šiuo atveju -- iki kol paspaus “OK”.

## prompt

Funkcija `prompt` priima du argumentus:

```js no-beautify
result = prompt(title, [default]);
```

Parodo modalinį langelį su paprasta tekstine žinute, įvesties laukeliu lankytojui ir mygtukus OK/Cancel.

`title`
: Tekstas, kurį reikės parodyti lankytojui.

`default`
: Nebūtinas antras parametras, pradinė vertė įvesties laukeliui.

```smart header="Kvadratiniai skliausteliai sintaksėje`[...]`"
Kvadratiniai skliausteliai aplink `default` aukščiau pateiktoje sintaksėje reiškia, kad parametras yra neprivalomas.
```

Lankytojas gali ką nors įvesti į įvesties lauką ir paspausti OK. Tada šį tekstą gausime kintamajame `result`. Arba jis gali atšaukti įvestį paspausdamas Cancel arba paspausdamas klavišą `key:Esc`, tada kaip kintamąjį `result` gausime `null`.

Iššauktas `prompt` grąžina tekstą iš įvesties laukelio arba `null`, jeigu įvestis buvo atšaukta.

Pavyzdžiui:

```js run
let age = prompt('Kiek jums metų?', 100);

alert(`Jums yra ${age} metų!`); // Jums yra 100 metų!
```

````warn header="IE naršyklėje: visada nurodykite `default`"
Antras parametras nėra būtinas, bet jeigu jo nepateiksite, Internet Explorer įtrauks `"undefined"` į prompt tekstą.

Norėdami išbandyti, paleiskite šį kodą Internet Explorer naršyklėje:

```js run
let test = prompt("Testas");
```

Tad tam, kad prompt visada gerai atrodytų IE, mes rekomenduojame visada pateikti antrą argumentą:

```js run
let test = prompt("Testas", ''); // <-- skirta IE
```
````

## confirm

Sintaksė:

```js
result = confirm(question);
```

Funkcija `confirm` parodo modalinį langelį su `question` (klausimu) ir dviem mygtukais: OK ir Cancel.

Rezultatas būna `true`, jeigu paspaudžiamas OK ir `false` kitu atveju.

Pavyzdžiui:

```js run
let isBoss = confirm("Ar tu esi bosas?");

alert( isBoss ); // true, jeigu paspaudžiamas OK
```

## Santrauka

Mes aptarėme 3 naršyklei būdingas funkcijas skirtas bendrauti su lankytojais:

`alert`
: parodo žinutę.

`prompt`
: parodo žinutę prašydamas vartotojo įvesti tekstą. Grąžina tekstą arba, jeigu paspaudžiamas Cancel ar `key:Esc` grąžinamas `null`.

`confirm`
: parodo žinutę ir laukia kol lankytojas paspaus "OK" arba "Cancel". Grąžina `true` kai OK ir `false` kai Cancel/`key:Esc`.

Visi šie veiksmai yra modaliniai: jie sustabdo skripto vykdymą ir neleidžia lankytojams naudotis likusiu puslapiu kol langelis nėra uždaromas.

Visus anksčiau minėtus metodus sieja du apribojimai:

1. Naršyklė nustato tikslią modalinio langelio vietą. Dažniausiai tai yra centras.
2. Tiksli langelio išvaizda taip pat priklauso nuo naršyklės. Mes jo pakeisti negalime.

Tokia yra paprastumo kaina. Yra daug kitų būdų parodyti gražesnius langelius ir naudoti puikesnį bendravimą su lankytojais, bet jeigu nėra labai svarbu įmantrumai esami metodai veikia kuo puikiausiai. 
