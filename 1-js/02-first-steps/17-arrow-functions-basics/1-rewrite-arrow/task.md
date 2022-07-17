
# Perrašykite naudodami rodyklių funkcijas

Žemiau pateiktame kode Function Expressions pakeiskite rodyklių funkcijomis:

```js run
function ask(question, yes, no) {
  if (confirm(question)) yes();
  else no();
}

ask(
  "Ar jus sutinkate?",
  function() { alert("Jus sutikote."); },
  function() { alert("Jus atšaukėte vykdymą."); }
);
```
