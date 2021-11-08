# Interakcija: alert, prompt, confirm

<<<<<<< HEAD:1-js/02-first-steps/09-alert-prompt-confirm/article.md
Šioje pamokų dalyje kalbėsime apie JavaScript kalbą "tokia kokia ji yra", be aplinkai būdingų pataisymų.

Bet vis dar naudosime naršykles kaip mūsų pavyzdinę aplinką, tad turėtume žinoti bent kelias vartotojo sąsajos (ang. user-interface) savybes. Šiame skyriuje susipažinsime su šiomis naršyklės funkcijomis `alert`, `prompt` ir `confirm`.

## alert

Sintaksė:

```js
alert(message);
```

Parodo žinutę ir sustabdo skriptą iki kol vartotojas paspaus "OK".
=======
As we'll be using the browser as our demo environment, let's see a couple of functions to interact with the user: `alert`, `prompt` and `confirm`.

## alert

This one we've seen already. It shows a message and waits for the user to press "OK".
>>>>>>> 4541b7af7584014a676da731f6e8774da5e059f6:1-js/02-first-steps/06-alert-prompt-confirm/article.md

Pavyzdžiui:

```js run
alert("Labas");
```

<<<<<<< HEAD:1-js/02-first-steps/09-alert-prompt-confirm/article.md
Miniatiūrinis langelis su žinute yra vadinamas *modaliniu langeliu* (ang. *modal window*). Žodis "modalinis" reiškia, kad lankytojas negali naudotis likusiu puslapiu, spausti kitų mygtukų ir t.t. kol nesusitvarkė su langeliu. Šiuo atveju -- iki kol paspaus "OK".
=======
The mini-window with the message is called a *modal window*. The word "modal" means that the visitor can't interact with the rest of the page, press other buttons, etc, until they have dealt with the window. In this case -- until they press "OK".
>>>>>>> 4541b7af7584014a676da731f6e8774da5e059f6:1-js/02-first-steps/06-alert-prompt-confirm/article.md

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

<<<<<<< HEAD:1-js/02-first-steps/09-alert-prompt-confirm/article.md
Lankytojas gali ką nors įvesti laukelyje ir paspausti OK. Arba jie gali atšaukti paspausdami Cancel ar klaviatūroje `key:Esc` mygtuką.
=======
```smart header="The square brackets in syntax `[...]`"
The square brackets around `default` in the syntax above denote that the parameter is optional, not required.
```

The visitor can type something in the prompt input field and press OK. Then we get that text in the `result`. Or they can cancel the input by pressing Cancel or hitting the `key:Esc` key, then we get `null` as the `result`.
>>>>>>> 4541b7af7584014a676da731f6e8774da5e059f6:1-js/02-first-steps/06-alert-prompt-confirm/article.md

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
