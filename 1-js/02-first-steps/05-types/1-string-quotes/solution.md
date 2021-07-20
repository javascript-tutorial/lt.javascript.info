
Atvirkštinės kabutės įterpia išraišką esančią viduje `${...}` į pačią eilutę.

```js run
let name = "Ilya";

// išraiška yra skaičius 1
alert( `labas ${1}` ); // labas 1

// išraiška yra eilutė "name"
alert( `labas ${"name"}` ); // labas name

// išraiška yra kintamasis, jo vertė įterpiama
alert( `labas ${name}` ); // labas Ilya
```
