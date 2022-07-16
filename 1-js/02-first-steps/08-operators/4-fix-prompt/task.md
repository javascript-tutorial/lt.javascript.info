importance: 5

---

# Ištaisykite sudėtį

Čia pateikiamas kodas, kuris paprašo naudotojo pateikti du skaičius ir parodo jų sumą.

Jis veikia neteisingai. Toliau pateiktame pavyzdyje išvestis yra `12` (numatytosioms `prompt` vertėms).

Kodėl taip yra? Ištaisykite tai. Rezultatas turėtų būti `3`.

```js run
let a = prompt("Pirmasis skaičius?", 1);
let b = prompt("Antrasis skaičius?", 2);

alert(a + b); // 12
```
