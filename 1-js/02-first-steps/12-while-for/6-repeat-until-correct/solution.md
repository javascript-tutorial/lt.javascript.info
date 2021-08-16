
```js run demo
let num;

do {
  num = prompt("Įveskite skaičių didesnį nei 100?", 0);
} while (num <= 100 && num);
```

Ciklas`do..while` pakartoja kol abu patikrinimai yra truthy:

1. Patikrinimas dėl `num <= 100` -- tai yra, įvesta vertė vis dar nėra didesnė už `100`.
2. Patikrinimas `&& num` yra neteisingas, jeigu `num` yra `null` arba tuščia eilutė. Tada `while` ciklas taip pat sustoja.

P.S. Jeigu `num` yra `null` tada `num <= 100` yra `true`, tad be antro patikrinimo ciklas nesustotų, jeigu lankytojas paspaustų CANCEL. Abu patikrinimai yra reikalingi.
