Yra daug algoritmų šiai užduočiai.

Panaudokime matrioškinį ciklą:

```js
Kiekvienam i intervale {
  patikrinkite ar i turi daliklį iš 1..i
  jeigu taip => vertė nėra pirminis skaičius
  jeigu ne => vertė yra pirminis skaičius, parodykite ją
}
```

Kodas naudojant etiketę:

```js run
let n = 10;

nextPrime:
for (let i = 2; i <= n; i++) { // kiekvienam i...

  for (let j = 2; j < i; j++) { // ieškoti daliklio..
    if (i % j == 0) tęsti nextPrime; // ne pirminis skaičius, eiti prie sekančio i
  }

  alert( i ); // pirminis
}
```

Yra daug vietos, kur galima jį optimizuoti. Pavyzdžiui, galėtume ieškoti daliklių nuo `2` iki `i` šaknies. Bet kokiu atveju, jeigu norime būti efektyvūs dideliems intervalams, reikia pakeisti priėjimo būdus ir pasitikėti pažengusia matematika ir sudėtingais algoritmais kaip [Quadratic sieve](https://en.wikipedia.org/wiki/Quadratic_sieve), [General number field sieve](https://en.wikipedia.org/wiki/General_number_field_sieve) etc.
