Atsakymas: `1`, ir tada `undefined`.

```js run
alert( alert(1) && alert(2) );
```

Šaukimas `alert` grąžina `undefined` (tiesiog parodo žinutę, tad nebus prasmingo grąžinimo).

Dėl to `&&` įvertina kairį operandą (parodo `1`), ir iš karto sustoja, nes `undefined` yra falsy vertė. O `&&` ieško falsy vertės ir ją grąžina, ir sustoja.

