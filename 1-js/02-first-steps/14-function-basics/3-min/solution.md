Sprendimo variantas naudojant `if`:

```js
function min(a, b) {
  if (a < b) {
    return a;
  } else {
    return b;
  }
}
```

Sprendimo variantas su operatoriumi `?`:

```js
function min(a, b) {
  return a < b ? a : b;
}
```

P.S. Lygybės `a == b` atveju nesvarbu, ką grąžinti.
