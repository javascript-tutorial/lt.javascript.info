importance: 4

---

# const didžiosiomis raidėmis?

Peržiūrėkite sekantį kodą:

```js
const birthday = '18.04.1982';

const age = someCode(birthday);
```

<<<<<<< HEAD
Mes turime konstantą `birthday` data ir amžius `age` yra paskaičiuojame pagal `birthday` tam tikro kodo pagalba (jis čia nepateiktas dėl glaustumo ir dėl to, kad tai nėra svarbu užduočiai).
=======
Here we have a constant `birthday` for the date, and also the `age` constant.

The `age` is calculated from `birthday` using `someCode()`, which means a function call that we didn't explain yet (we will soon!), but the details don't matter here, the point is that `age` is calculated somehow based on the `birthday`.
>>>>>>> 6236eb8c3cdde729dab761a1d0967a88a1a6197e

Ar būtų gerai naudoti didžiąsias raides `birthday`? O kaip dėl `age`? O galbūt netgi abiems?

```js
<<<<<<< HEAD
const BIRTHDAY = '18.04.1982'; // perrašyti didžiosiomis raidėmis?

const AGE = someCode(BIRTHDAY); // perrašyti didžiosiomis raidėmis?
=======
const BIRTHDAY = '18.04.1982'; // make birthday uppercase?

const AGE = someCode(BIRTHDAY); // make age uppercase?
>>>>>>> 6236eb8c3cdde729dab761a1d0967a88a1a6197e
```
