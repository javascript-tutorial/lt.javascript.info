Atsakymas: `3`.

```js run
alert( null || 2 && 3 || 4 );
```

IR `&&` pirmenybė yra aukštesnė už `||`, tad jis įvykdomas pirmiau.

Rezultatas yra `2 && 3 = 3`, tad išraiška tampa:

```
null || 3 || 4
```

Dabar rezultatas yra pirmoji truthy vertė: `3`.

