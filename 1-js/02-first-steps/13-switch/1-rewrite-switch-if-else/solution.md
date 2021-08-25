Tam, kad būtų palaikomas `switch` funkcionalumas `if` turi naudoti griežtą lygybę `'==='`.

Bet duotoms eilutėms, paprasta lygybė `'=='` taip pat veikia.

```js no-beautify
if(browser == 'Edge') {
  alert("Jūs turite Edge!");
} else if (browser == 'Chrome'
 || browser == 'Firefox'
 || browser == 'Safari'
 || browser == 'Opera') {
  alert( 'Gerai, palaikome ir tokias naršykles' );
} else {
  alert( 'Mes tikimės, kad šis puslapis veikia gerai!' );
}
```

Atkreipkite dėmesį: konstruktas `browser == 'Chrome' || browser == 'Firefox' …` yra atskirtas į naujas eiles dėl geresnio skaitomumo.

Tačiau `switch` vis tiek yra švaresnis ir labiau apibūdinantis konstruktas.
