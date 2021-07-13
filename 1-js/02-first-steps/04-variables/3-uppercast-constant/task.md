importance: 4

---

# const didžiosiomis raidėmis?

Peržiūrėkite sekantį kodą:

```js
const birthday = '18.04.1982';

const age = someCode(birthday);
```

Mes turime konstantą `birthday` data ir amžius `age` yra paskaičiuojame pagal `birthday` tam tikro kodo pagalba (jis čia nepateiktas dėl glaustumo ir dėl to, kad tai nėra svarbu užduočiai).

Ar būtų gerai naudoti didžiąsias raided `birthday`? O kaip dėl `age`? O galbūt netgi abiems?

```js
const BIRTHDAY = '18.04.1982'; // perrašyti didžiosiomis raidėmis?

const AGE = someCode(BIRTHDAY); // perrašyti didžiosiomis raidėmis?
```

