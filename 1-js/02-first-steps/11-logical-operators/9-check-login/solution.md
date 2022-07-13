

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
>>>>>>> 29216730a877be28d0a75a459676db6e7f5c4834
  } else {
    alert( 'Neteisingas slaptažodis' );
  }

<<<<<<< HEAD
} else if (userName == '' || userName == null) {
  alert( 'Atšaukta' );
=======
} else if (userName === '' || userName === null) {
  alert( 'Canceled' );
>>>>>>> 29216730a877be28d0a75a459676db6e7f5c4834
} else {
  alert( "Aš jūsų nepažįstu" );
}
```

Atkreipkite dėmesį į vertikalius įgilėjimus viduje `if` rinkinio. Techniškai jie nėra būtini, bet jie paverčia kodą lengviau skaitomu.
