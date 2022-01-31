

```js run demo
let userName = prompt("Kas čia?", '');

if (userName === 'Admin') {

  let pass = prompt('Slaptažodis?', '');

<<<<<<< HEAD
  if (pass == 'TheMaster') {
    alert( 'Sveiki!' );
  } else if (pass == '' || pass == null) {
    alert( 'Atšaukta' );
=======
  if (pass === 'TheMaster') {
    alert( 'Welcome!' );
  } else if (pass === '' || pass === null) {
    alert( 'Canceled' );
>>>>>>> 0f748275e20a81700c8514f22a7cc80c4422d09c
  } else {
    alert( 'Neteisingas slaptažodis' );
  }

<<<<<<< HEAD
} else if (userName == '' || userName == null) {
  alert( 'Atšaukta' );
=======
} else if (userName === '' || userName === null) {
  alert( 'Canceled' );
>>>>>>> 0f748275e20a81700c8514f22a7cc80c4422d09c
} else {
  alert( "Aš jūsų nepažįstu" );
}
```

Atkreipkite dėmesį į vertikalius įgilėjimus viduje `if` rinkinio. Techniškai jie nėra būtini, bet jie paverčia kodą lengviau skaitomu.
