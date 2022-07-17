
```js run
function ask(question, yes, no) {
  if (confirm(question)) yes();
  else no();
}

ask(
  "Ar jus sutinkate?",
*!*
  () => alert("Jus sutikote."),
  () => alert("Jus atšaukėte vykdymą.")
*/!*
);
```

Atrodo trumpai ir švariai, ar ne?