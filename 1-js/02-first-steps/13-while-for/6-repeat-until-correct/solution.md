
```js run demo
let num;

do {
  num = prompt("Įveskite skaičių didesnį nei 100?", 0);
} while (num <= 100 && num);
```

Ciklas`do..while` pakartoja kol abu patikrinimai yra truthy:

<<<<<<< HEAD:1-js/02-first-steps/12-while-for/6-repeat-until-correct/solution.md
1. Patikrinimas dėl `num <= 100` -- tai yra, įvesta vertė vis dar nėra didesnė už `100`.
2. Patikrinimas `&& num` yra neteisingas, jeigu `num` yra `null` arba tuščia eilutė. Tada `while` ciklas taip pat sustoja.
=======
1. The check for `num <= 100` -- that is, the entered value is still not greater than `100`.
2. The check `&& num` is false when `num` is `null` or an empty string. Then the `while` loop stops too.
>>>>>>> 246c600f11b4e6c52b4ae14f83e65319671f998f:1-js/02-first-steps/13-while-for/6-repeat-until-correct/solution.md

P.S. Jeigu `num` yra `null` tada `num <= 100` yra `true`, tad be antro patikrinimo ciklas nesustotų, jeigu lankytojas paspaustų CANCEL. Abu patikrinimai yra reikalingi.
