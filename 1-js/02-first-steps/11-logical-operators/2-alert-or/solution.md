Atsakymas yra: pirma `1`, tada `2`.

```js run
alert( alert(1) || 2 || alert(3) );
```

Šaukimas `alert` negrąžina jokios vertės. Arba kitaip sakant, jis grąžina `undefined`.

1. Pirmasis ARBA `||` įvertina kairėje esantį operandą `alert(1)`. Jis parodo žinutę su `1`.
2. `alert` grąžina `undefined`, tad ARBA eina prie sekančio operando ieškodamas truthy vertės.
3. Antrasis operandas `2` yra truthy, tad operacija sustabdoma, grąžinamas `2` ir parodomas per išorinį alert.

Nebebus `3`, nes įvertinimas nepasiekia `alert(3)`.
