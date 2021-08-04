

```js run demo
let userName = prompt("Kas čia?", '');

if (userName == 'Admin') {

  let pass = prompt('Slaptažodis?', '');

  if (pass == 'TheMaster') {
    alert( 'Sveiki!' );
  } else if (pass == '' || pass == null) {
    alert( 'Atšaukta' );
  } else {
    alert( 'Neteisingas slaptažodis' );
  }

} else if (userName == '' || userName == null) {
  alert( 'Atšaukta' );
} else {
  alert( "Aš jūsų nepažįstu" );
}
```

Atkreipkite dėmesį į vertikalius įgilėjimus viduje `if` rinkinio. Techniškai jie nėra būtini, bet jie paverčia kodą lengviau skaitomu.
