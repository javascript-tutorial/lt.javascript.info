importance: 4

---

# Ar "else" yra privalomas?

Ši funkcija grąžina `true`, jei parametras `age` yra didesnis nei `18`.

Priešingu atveju ji prašo patvirtinimo per `confirm` ir grąžina rezultatą:

```js
function checkAge(age) {
  if (age > 18) {
    return true;
*!*
  } else {
    // ...
    return confirm('Ar tėvai leido?');
  }
*/!*
}
```

Ar ši funkcija veiks kitaip, jei `else` bus pašalinta?

```js
function checkAge(age) {
  if (age > 18) {
    return true;
  }
*!*
  // ...
  return confirm('Ar tėvai leido?');
*/!*
}
```

Ar yra nors vienas šio varianto elgsenos skirtumas?
