importance: 5

---

# Perrašykite “switch” į “if”

Perrašykite kodą naudodami `if..else`, kuris atitiktų sekantį `switch`:

```js
switch (browser) {
  case 'Edge':
    alert( "Jūs turite Edge!" );
    break;

  case 'Chrome':
  case 'Firefox':
  case 'Safari':
  case 'Opera':
    alert( 'Puiku, mes palaikome ir šias naršykles' );
    break;

  default:
    alert( 'Mes tikimės, kad šis puslapis veikia gerai!' );
}
```

