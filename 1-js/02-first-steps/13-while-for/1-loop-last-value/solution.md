Atsakymas: `1`.

```js run
let i = 3;

while (i) {
  alert( i-- );
}
```

Kiekviena ciklo iteracija sumažina `i` per `1`. Patikrinimas `while(i)` sustabdo ciklą kai `i = 0`.

Dėl to žingsniai iš paskutinio ciklo suformuoja tokią seką (“atskleistas ciklas”):

```js
let i = 3;

alert(i--); // parodo 3, sumažina i iki 2

alert(i--) // parodo 2, sumažina i iki 1

alert(i--) // parodo 1, sumažina i iki 0

// viskas, while(i) patikrinimas sustabdo ciklą
```
