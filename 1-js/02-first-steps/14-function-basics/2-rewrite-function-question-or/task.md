importance: 4

---

# Perrašykite funkciją naudodami operatorių '?' arba '||'

Ši funkcija grąžina `true`, jei parametras `age` yra didesnis nei `18`.

Priešingu atveju klausiama `confirm' ir grąžinamas rezultatas.

```js
function checkAge(age) {
  if (age > 18) {
    return true;
  } else {
    return confirm('Ar tėvai leido?');
  }
}
```

Perrašykite funkciją taip, kad ji darytų tą patį, bet be `if`, vienoje eilutėje.

Sukurkite dvi funkcijos `checkAge` variantus:

1. Naudojant operatorių `?`
2. Naudojant operatorių `||`
