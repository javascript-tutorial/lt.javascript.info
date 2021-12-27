Atsakymas yra: pirma `1`, tada `2`.

```js run
alert( alert(1) || 2 || alert(3) );
```

Šaukimas `alert` negrąžina jokios vertės. Arba kitaip sakant, jis grąžina `undefined`.

<<<<<<< HEAD
1. Pirmasis ARBA `||` įvertina kairėje esantį operandą `alert(1)`. Jis parodo žinutę su `1`.
2. `alert` grąžina `undefined`, tad ARBA eina prie sekančio operando ieškodamas truthy vertės.
3. Antrasis operandas `2` yra truthy, tad operacija sustabdoma, grąžinamas `2` ir parodomas per išorinį alert.
=======
1. The first OR `||` evaluates its left operand `alert(1)`. That shows the first message with `1`.
2. The `alert` returns `undefined`, so OR goes on to the second operand searching for a truthy value.
3. The second operand `2` is truthy, so the execution is halted, `2` is returned and then shown by the outer alert.
>>>>>>> 3c934b5a46a76861255e3a4f29da6fd54ab05c8c

Nebebus `3`, nes įvertinimas nepasiekia `alert(3)`.
