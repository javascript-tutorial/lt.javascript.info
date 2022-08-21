# Nulinio susiliejimo operatorius '??'

[recent browser="new"]

Nulinio susiliejimo operatorius užrašomas dviem klausiamaisiais ženklais `??`.

Kadangi jis apdoroja `null` ir `undefined` vienodai, šiame straipsnyje įvesime specialų terminą. Trumpai sakysime, kad vertė yra “apibrėžta”, jei ji nėra lygi nei `null`, nei `undefined`.

Rezultatas `a ?? b` yra:
- jei `a` yra apibrėžta, tada `a`,
- jei `a` yra neapibrėžta, tada `b`.

Kitaip tariant, `??` grąžina pirmąjį argumentą, jei jis nėra `null/undefined`. Priešingu atveju - antrąjį.

Nulinio susiliejimo operatorius nėra visiškai naujas. Tai tik graži sintaksė, leidžianti gauti pirmąją “apibrėžtą” vertę iš dviejų.

Mes galime perrašyti `result = a ?? b`, naudodami jau mums žinomus operatorius, pavyzdžiui, taip:

```js
result = (a !== null && a !== undefined) ? a : b;
```

Dabar turėtų būti visiškai aišku, ką daro `??`. Pažiūrėkime, kur jis padeda.

Paprastai operatorius `??` reikalingas norint nustatyti numatytoją vertę potencialiai neapibrėžtam kintamajam.

Pavyzdžiui, čia mes atvaizduojame `user`, jei jo vertė nėra `null/undefined`, priešingu atveju - `Anonimas`:

```js run
let user;

alert(user ?? "Anonimas"); // Anonimas (user yra neapibrėžtas)
```

O štai pavyzdys, kai `user` priskirta vertė:

```js run
let user = "Jonas";

alert(user ?? "Anonimas"); // Jonas (user yra apibrėžtas)
```

Mes taip pat galime naudoti `??` seką, norėdami iš sąrašo išrinkti pirmąją vertę, kuri nėra `null/undefined`.

Tarkime, kad turime naudotojo duomenis kintamuosiuose `firstName`, `lastName` arba `nickName`. Visi jie gali būti neapibrėžti, jei naudotojas nusprendė neįvesti vertės.

Mes norėtume, kad naudotojo vardas būtų atvaizduojamas naudojant vieną iš šių kintamųjų arba rodomas "Anonimas", jei visi jie neapibrėžti.

Panaudokime operatorių `??`:

```js run
let firstName = null;
let lastName = null;
let nickName = "Supercoder";

// parodo pirmąją apibrėžtą vertę:
*!*
alert(firstName ?? lastName ?? nickName ?? "Anonimas"); // Supercoder
*/!*
```

## Palyginimas su ||

Operatorius ARBA `||` gali būti naudojamas taip pat kaip ir `??`, kaip aprašyta [ankstesniame skyriuje](info:logical-operators#or-finds-the-first-truthy-value).

Pavyzdžiui, aukščiau pateiktame kode galėtume pakeisti `??` į `||` ir vis tiek gautume tą patį rezultatą:

```js run
let firstName = null;
let lastName = null;
let nickName = "Supercoder";

// parodo pirmąją truthy vertę:
*!*
alert(firstName || lastName || nickName || "Anonimas"); // Supercoder
*/!*
```

Istoriškai ARBA `||` operatorius buvo pirmasis. Jis egzistuoja nuo pat JavaScript atsiradimo pradžios, todėl programišiai jau seniai jį naudojo tokiems tikslams.

Kita vertus, nulinio susiliejimo operatorius `??` į JavaScript buvo pridėtas visai neseniai, o priežastis buvo ta, kad žmonės nebuvo patenkinti `||`.

Svarbus skirtumas tarp jų yra tas, kad:
- `||` grąžina pirmąją *truthy* vertę.
- `??` grąžina pirmąją *apibrėžtą* vertę

Kitaip tariant, `||` neskiria `false`, `0`, tuščios eilutės `""` ir `null/undefined`. Jos visos yra vienodos -- falsy vertės. Jei bet kuri iš jų yra pirmasis `||` argumentas, kaip rezultatą gausime antrąjį argumentą.

Tačiau praktikoje numatytąją vertę galime norėti naudoti tik tada, kai kintamasis yra `null/undefined`. T. y. kai vertė iš tikrųjų nežinoma/nenustatyta.

Pavyzdžiui, panagrinėkite štai ką:

```js run
let height = 0;

alert(height || 100); // 100
alert(height ?? 100); // 0
```

- Naudojant `height || 100` patikrinama, ar `height` nėra falsy vertė, ir ji yra `0`, taigi tikrai falsy.
    - taigi `||` rezultatas yra antrasis argumentas, `100`.
- Naudojant `height ?? 100` patikrinama, ar `height` nėra `null/undefined`, bet taip nėra,
    - taigi rezultatas yra pats kintamasis `height`, t. y. `0`

Praktikoje nulinis aukštis dažnai yra tinkama vertė, kurios nereikėtų keisti numatytąja. Taigi `??` daro teisingą dalyką.

## Pirmenybė

Operatoriaus `??` pirmenybė yra tokia pati kaip ir `||`. Abu jie [MDN lentelėje](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence#Table) yra lygūs `3`.

Tai reiškia, kad, kaip ir `||`, nulinio susiliejimo operatorius `??` vertinamas prieš `=` ir `?`, bet po daugumos kitų operacijų, tokių kaip `+`, `*`.

Taigi, jei norime pasirinkti vertę su `??` išraiškoje su kitais operatoriais, pridėkite skliaustelius:

```js run
let height = null;
let width = null;

// svarbu: naudokite skliaustelius
let area = (height ?? 100) * (width ?? 50);

alert(area); // 5000
```

Priešingu atveju, jei praleisime skliaustelius, kadangi `*` turi didesnę pirmenybę nei `??`, jis bus vykdomas pirmas, todėl rezultatai bus neteisingi.

```js
// be skliaustelių
let area = height ?? 100 * width ?? 50;

// ...veikia taip pat, kaip ir čia (tikriausiai ne tai, ko norime):
let area = height ?? (100 * width) ?? 50;
```

### Naudojimas ?? kartu su && arba ||

Dėl saugumo priežasčių JavaScript draudžia naudoti `??` kartu su `&&` ir `||` operatoriais, nebent pirmenybė būtų aiškiai nurodyta skliaustuose.

Toliau pateiktas kodas sukelia sintaksės klaidą:

```js run
let x = 1 && 2 ?? 3; // Sintaksės klaida
```

Šis apribojimas tikrai yra ginčytinas, jis buvo pridėtas į kalbos specifikaciją siekiant išvengti programavimo klaidų, kai žmonės pradeda pereiti nuo `||` prie `??`.

Norėdami tai apeiti, naudokite aiškius skliaustelius:

```js run
*!*
let x = (1 && 2) ?? 3; // Veikia
*/!*

alert(x); // 2
```

## Santrauka

- Nulinio susiliejimo operatorius `??` yra trumpas būdas pasirinkti pirmąją “apibrėžtą” vertę iš sąrašo.

    Jis naudojamas kintamiesiems priskirti numatytąsias vertes:

    ```js
    // nustatyti height=100, jei height lygus null arba undefined
    height = height ?? 100;
    ```

- Operatoriaus `??` pirmenybė yra labai maža, tik šiek tiek didesnė nei `?` ir `=`, todėl, naudodami jį išraiškoje, pridėkite skliaustelius.
- Draudžiama naudoti `??` su `||` arba `&&` be aiškių skliaustelių.
