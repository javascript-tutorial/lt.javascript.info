Atsakymas: pirma ir antra bus įvykdytos.

Details:

```js run
// Paleidžiama.
// Rezultatas iš -1 || 0 = -1, truthy
if (-1 || 0) alert( 'pirmas' );

// Nepaleidžiamas
// -1 && 0 = 0, falsy
if (-1 && 0) alert( 'antras' );

// Įvykdomas
// Operatorius && turi aukštesnį prioritetą negu ||
// tad -1 && 1 įvykdomas pirmiau, sukurdamas mums grandinę:
// null || -1 && 1  ->  null || 1  ->  1
if (null || -1 && 1) alert( 'trečias' );
```

