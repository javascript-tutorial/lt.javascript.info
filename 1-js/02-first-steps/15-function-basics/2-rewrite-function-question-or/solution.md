Naudojant operatorių `?`:

```js
function checkAge(age) {
  return (age > 18) ? true : confirm('Ar tėvai leido?');
}
```

Naudojant operatorių `||` (trumpiausias variantas):

```js
function checkAge(age) {
  return (age > 18) || confirm('Ar tėvai leido?');
}
```

Atkreipkite dėmesį, kad skliaustai aplink `age > 18` yra neprivalomi. Jie skirti geresniam kodo skaitomumui užtikrinti.
