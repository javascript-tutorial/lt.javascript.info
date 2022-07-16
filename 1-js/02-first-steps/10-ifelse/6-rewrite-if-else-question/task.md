importance: 5

---

# Perrašykite 'if..else' į '?'

Perrašykite `if..else` naudodami daugybinius ternarinius operatorius `'?'`.

Kad būtų lengviau skaityti, rekomenduojama kodą padalyti į kelias eilutes.

```js
let message;

if (login == 'Darbuotojas') {
  message = 'Labas';
} else if (login == 'Direktorius') {
  message = 'Sveiki';
} else if (login == '') {
  message = 'Nėra prisijungimo';
} else {
  message = '';
}
```
