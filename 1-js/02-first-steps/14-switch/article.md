# Teiginys "switch"

Teiginys `switch` gali pakeisti daugybinius `if` patikrinimus.

Jis suteikia lengviau apibūdinamą kelią palyginti vertes su įvairiais variantais.

## Sintaksė

Teiginys `switch` turi vieną ir daugiau `case` (bylos) blokų ir numatytąjį pasirinkimą.

Tai atrodo taip:

```js no-beautify
switch(x) {
  case 'vertė1':  // if (x === 'vertė1')
    ...
    [break]

  case 'vertė2':  // if (x === 'vertė2')
    ...
    [break]

  default:
    ...
    [break]
}
```

- Vertė `x` yra patikrinama griežta lygybe su verte iš pirmos bylos `case` (tai yra `vertė1`) tada su antra (`vertė2`) ir taip toliau.
- Jeigu lygybė randama, `switch` pradeda vykdyti kodą nuo atitinkančios bylos `case`, iki artimiausio `break` (arba kol pasibaigs `switch`).
- Jeigu nei viena byla nesurado atitikimo, tokiu atveju yra įvykdomas `default` kodas (jeigu toks egzistuoja).

## Pavyzdys

Pavyzdys `switch` (įvykdytas kodas yra paryškintas):

```js run
let a = 2 + 2;

switch (a) {
  case 3:
    alert( 'Per mažas' );
    break;
*!*
  case 4:
    alert( 'Kaip tik!' );
    break;
*/!*
  case 5:
<<<<<<< HEAD:1-js/02-first-steps/13-switch/article.md
    alert( 'Per didelis' );
=======
    alert( 'Too big' );
>>>>>>> bae0ef44d0208506f6e9b7f3421ee640ab41af2b:1-js/02-first-steps/14-switch/article.md
    break;
  default:
    alert( "Tokios vertės nežinau" );
}
```

Šiuo atveju `switch` pradeda lyginti `a` iš pirmos bylos `case` variantą, kuris yra `3`. Atitikmuo nėra randamas.

Tada `4`. Atitikmuo randamas, tad pradedamas vykdymas nuo `case 4` iki artimiausio `break`.

**Jeigu nėra `break` tokiu atveju vykdymas tęsiasi su sekančia `case` be jokių patikrinimų.**

Pavyzdys be `break`:

```js run
let a = 2 + 2;

switch (a) {
  case 3:
    alert( 'Per mažas' );
*!*
  case 4:
    alert( 'Kaip tik!' );
  case 5:
    alert( 'Per didelis' );
  default:
    alert( "Tokios vertės nežinau" );
*/!*
}
```

Pavyzdyje aukščiau iš eilės matome kaip įvykdomi trys `alert`:

```js
alert( 'Kaip tik!' );
alert( 'Per didelis' );
alert( "Tokios vertės nežinau" );
```

````smart header="Bet kokia išraiška gali būti `switch/case` argumentu"
Abu `switch` ir `case` leidžia sutartines išraiškas.

Pavyzdžiui:

```js run
let a = "1";
let b = 0;

switch (+a) {
*!*
  case b + 1:
    alert("šitas preina, nes +a yra 1, tiksliai lygu b+1");
    break;
*/!*

  default:
    alert("tai nepasileidžia");
}
```
Čia `+a` atiduoda `1`, tai yra palyginama su `b + 1` byloje `case`, įvykdomas atitinkamas kodas.
````

## Grupavimas su "case"

Keli `case` variantai, kurie dalinasi tuo pačiu kodu gali būti sugrupuoti.

Pavyzdžiui, jeigu mes norime, kad tas pats kodas pasileistų byloms `case 3` ir `case 5`:

```js run no-beautify
let a = 3;

switch (a) {
  case 4:
    alert('Teisingai!');
    break;

*!*
  case 3: // (*) dvi bylos sugrupuotos
  case 5:
    alert('Neteisingai!');
    alert('Būtų neblogai apsilankyti matematikos pamokoje.');
    break;
*/!*

  default:
    alert('Rezultatas yra iš tikrųjų keistas.');
}
```

Dabar abu `3` ir `5` parodo tą pačią žinutę.

Gebėjimas "sugrupuoti" bylas yra šalutinis efektas to kaip `switch/case` veikia be `break`. Čia `case 3` vykdymas prasideda nuo eilės su `(*)` ir eina per bylą `case 5`, nes nėra `break`.

## Tipas yra svarbu

Pabrėžkime tai, kad lygybės patikrinimas yra visada griežtas. Vertės turi būti vienodo tipo, kad atitiktų viena kitą.

Pavyzdžiui, apsvarstykime tokį kodą:

```js run
let arg = prompt("Įveskite vertę?");
switch (arg) {
  case '0':
  case '1':
    alert( 'Vienas arba nulis' );
    break;

  case '2':
    alert( 'Du' );
    break;

  case 3:
    alert( 'Niekada nėra įvykdomas!' );
    break;
  default:
    alert( 'Nežinoma vertė' );
}
```

1. Kai įvedamas `0`, `1`, paleidžiamas pirmas `alert`.
2. Kai įvedamas `2` paleidžiamas antras `alert`.
3. Bet `3` neįvykdomas, kadangi `prompt` rezultatas yra eilutė `"3"`, o tai nėra griežtai lygu `===` skaičiui `3`. Tad mes turime neveikiantį kodą byloje `case 3`! Įvykdomas `default` variantas.
