Pirmi du patikrinimai pavirsta į dvi atskiras bylas `case`. Trečias patikrinimas išskiriamas į dvi bylas:

```js run
let a = +prompt('a?', '');

switch (a) {
  case 0:
    alert( 0 );
    break;

  case 1:
    alert( 1 );
    break;

  case 2:
  case 3:
    alert( '2,3' );
*!*
    break;
*/!*
}
```

Atkreipkite dėmesį: pabaigoje esantis `break` nėra reikalingas. Bet mes jį pridedame tam, kad kodas būtų paruoštas ateities pakeitimams.

Yra galimybė, kad ateityje norėsime pridėti dar vieną bylą `case`, pavyzdžiui `case 4`. Jeigu prieš tai būsime pamiršę pridėti `break`, tokiu atveju `case 3` pabaigoje bus klaida. Tad tai yra mūsų pačių apsidraudimas.
