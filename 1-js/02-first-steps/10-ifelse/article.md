<<<<<<< HEAD
# Sąlyginiai operatoriai: if, '?'
=======
# Conditional branching: if, '?'
>>>>>>> 3699f73b4ccb2a57ac5ef990d2687bf31ccf564c

Kartais mums tenka atlikti skirtingus veiksmus atitinkančius skirtingas sąlygas.

Kad tai padarytume mes naudojame teiginį `if` ir sąlyginį operatorių `?`, arba dar kitaip vadinamą "klaustuko" operatorių.

## Teiginys "if"

Teiginys `if(...)` įvertina sąlygas esančias tarp skliaustelių ir jeigu rezultatas yra `true` tada įvykdo kodų rinkinį.

Pavyzdžiui:

```js run
let year = prompt('Kuriais metais buvo išleista ECMAScript-2015 specifikacija?', '');

*!*
if (year == 2015) alert( 'Jūs teisi(-us)!' );
*/!*
```

Pavyzdyje viršuje, sąlyga yra paprastas lygybės patikrinimas (`year == 2015`), bet jis gali būti daug sudėtingesnis.

Jeigu norime įvykdyti daugiau nei vieną teiginį, turime kodų rinkinį apskliausti riestiniais skliaustais:

```js
if (year == 2015) {
  alert( "Jūs teisi(-us)!" );
  alert( "Jūs protinga(-as)!" );
}
```

Rekomenduojame apskliausti kodų rinkinį su riestiniais skliaustais `{}` kiekvieną kartą kai pamatote `if`, net kai tereikia įvykdyti tik vieną teiginį. Taip darydami palengvinsite skaitomumą.

## Loginės konversijos

Teiginys `if (…)` įvertina išraišką esančią skliaustuose ir paverčia rezultatą į loginę vertę.

Prisiminkime konversijos taisykles iš skyriaus <info:type-conversions>:

- Skaičius `0`, tuščia eilutė `""`, `null`, `undefined` ir `NaN` visi tampa `false`. Nes jos yra vadinamosios "falsy" (neteisingosio) vertės.
- Kitos vertės tampa `true`, tad jos vadinamos "truthy" (teisingosios).

Taigi kodas tokiu atveju niekada nebūtų įvykdytas:

```js
if (0) { // 0 yra falsy
  ...
}
```

...o šios sąlygos viduje -- visada įvykdomas:

```js
if (1) { // 1 yra truthy
  ...
}
```

Mes taip pat galime praleisti iš anksto įvertintą loginę vertę per `if`, štai taip:

```js
let cond = (year == 2015); // lygybė įvertinama į true arba false

if (cond) {
  ...
}
```

## Išlyga "else"

<<<<<<< HEAD
Teiginys `if` gali turėti išlygos "else" rinkinį. Jis įvykdomas kai sąlyga yra false.
=======
The `if` statement may contain an optional "else" block. It executes when the condition is falsy.
>>>>>>> 3699f73b4ccb2a57ac5ef990d2687bf31ccf564c

Pavyzdžiui:
```js run
let year = prompt('Kuriais metais buvo išleista ECMAScript-2015 specifikacija?', '');

if (year == 2015) {
  alert( 'Jūs atspėjote!' );
} else {
  alert( 'Kaip galėjote taip suklysti?' ); // bet kuriai kitai vertei išskyrus 2015
}
```

## Kelios sąlygos: "else if"

Kartais mums gali tekti testuoti kelis sąlygos variantus. Išlyga `else if` leidžia tai padaryti.

Pavyzdžiui:

```js run
let year = prompt('Kuriais metais buvo išleista ECMAScript-2015 specifikacija?', '');

if (year < 2015) {
  alert( 'Per anksti...' );
} else if (year > 2015) {
  alert( 'Per vėlai' );
} else {
  alert( 'Būtent!' );
}
```

JavaScript kode aukščiau visų pirma patikrina `year < 2015`. Jeigu jis yra falsy, ji pereina prie kitos sąlygos `year > 2015`. Jeigu ji yra falsy, parodo paskutinį `alert`.

Gali būti daug `else if` rinkinių. Paskutinis `else` nėra privalomas.

## Sąlyginis operatorius '?'

Kartais mes turime priskirti kintamąjį priklausomai nuo sąlygos. 

Pavyzdžiui:

```js run no-beautify
let accessAllowed;
let age = prompt('Kiek jums metų?', '');

*!*
if (age > 18) {
  accessAllowed = true;
} else {
  accessAllowed = false;
}
*/!*

alert(accessAllowed);
```

Taip vadinamas "sąlyginis" arba "klaustuko" operatorius mums leidžia tai padaryti daug trumpesniu ir paprastesniu būdu.

Operatorių atstovauja klaustukas `?`. Kartais jis vadinamas "ternariniu", nes operatorius turi tris operandus. Iš tikrųjų jis vienas ir vienintelis, kuris JavaScript turi tiek operandų.

Sintaksė yra tokia:
```js
let result = condition ? value1 : value2;
```

Sąlyga `condition` yra įvertinama: jeigu ji yra truthy tada grąžinama vertė `value1`, kitu atveju -- `value2`.

Pavyzdžiui:

```js
let accessAllowed = (age > 18) ? true : false;
```

Techniškai galime nedėti skliaustelių aplink `age > 18`. Klaustukas turi žemą prioritetą, tad jis įvykdomas po palyginimo `>`.

Šis palyginimas darys tą patį kaip aukščiau esantis:

```js
// palyginimo operatorius "age > 18" įvykdomas pirmas
// (nebūtina skliausti lenktiniais skliaustais)
let accessAllowed = age > 18 ? true : false;
```

Tačiau skliaustai daro kodą labiau įskaitomu, tad mes rekomenduojame juos naudoti.

````smart
Pavyzdyje viršuje galite išvengti klaustuko, nes palyginimas bet kokiu atveju grąžina `true/false`:

```js
// tas pats
let accessAllowed = age > 18;
```
````

## Daugkartiniai '?'

Seka klaustukų operatorių `?` gali grąžinti vertę, kuri priklauso nuo daugiau nei vienos sąlygos.

Pavyzdžiui:
```js run
let age = prompt('amžius?', 18);

let message = (age < 3) ? 'Labas, kūdikėli!' :
  (age < 18) ? 'Labas!' :
  (age < 100) ? 'Sveiki!' :
  'Koks neįprastas amžius!';

alert( message );
```

Iš praždių gali būti sunku suprasti kas vyksta. Bet geriau įsižiūrėjus matome, kad tai tik įprastinė testų seka:

1. Pirmas klaustukas patikrina ar `age < 3`.
2. Jeigu true -- grąžina `'Labas, kūdikėli!'`. Kitu atveju, pereina prie išraiškos po dvitaškio '":"' ir tikrina `age < 18`.
3. Jeigu šitas yra true -- grąžina `'Labas!'`. Kitu atveju, pereina prie išraiškos po dvitaškio '":"' ir tikrina `age < 100`.
4. Jeigu tai true -- grąžina `'Sveiki!'`. Kitu atveju, pereina prie išraiškos po paskutinio dvitaškio '":"', grąžina `'Koks neįprastas amžius!'`.

Štai kaip tai atrodytų, jeigu naudotume `if..else`:

```js
if (age < 3) {
  message = 'Labas, kūdikėli!';
} else if (age < 18) {
  message = 'Labas!';
} else if (age < 100) {
  message = 'Sveiki!';
} else {
  message = 'Koks neįprastas amžius!';
}
```

## Netradicinis '?' naudojimas

Kartais klaustukas `?` naudojamas kaip pakaitalas `if`:

```js run no-beautify
let company = prompt('Kuri kompanija sukūrė JavaScript?', '');

*!*
(company == 'Netscape') ?
   alert('Teisingai!') : alert(Neteisingai.');
*/!*
```

Priklausomai nuo sąlygos `company == 'Netscape'`, arba pirma, arba antra išraiška po `?` bus įvykdyta ir parodys alert.

Šiuo atveju rezultatas nėra priskiriamas kintamajam. Vietoje to mes įvykdome atitinkamą kodą priklausomai nuo sąlygos.

**Nerekomenduojama naudoti klaustuko tokiu būdu.**

Toks žymėjimas yra trumpesnė teiginio`if` versija, o tai yra patrauklu kai kuriems programuotojams. Bet ji yra sunkiau perskaitoma.

Štai palyginimui toks pats kodas, bet naudojant `if`:

```js run no-beautify
let company = prompt('Kuri kompanija sukūrė JavaScript?', '');

*!*
if (company == 'Netscape') {
  alert('Teisingai!');
} else {
  alert('Neteisingai.');
}
*/!*
```

Mūsų akys skanuoja kodą vertikaliai. Kodų rinkinius, kurie išsiplečia per kelias eiles, daug lengviau perskaityti negu ilgus horizontalius instrukcijų rinkinius. 

Klaustuko operatoriaus `?` tikslas yra grąžinti vieną arba kitą vertę priklausomai nuo sąlygos. Prašau naudokite jį būtent tam. Naudokite `if` kai jums reikia įvykdyti kodą su skirtingai išsišakojimais.
