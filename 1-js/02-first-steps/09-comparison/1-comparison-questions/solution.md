

```js no-beautify
5 > 4 → true
"apple" > "pineapple" → false
"2" > "12" → true
undefined == null → true
undefined === null → false
null == "\n0\n" → false
null === +"\n0\n" → false
```

Kai kurios priežastys:

1. Akivaizdu, kad tai yra true.
2. Žodyno palyginimas, todėl false. `"a"` yra mažesnis už `"p"`.
3. Vėlgi, žodyno palyginimas, pirmasis simbolis `"2"` yra didesnis už pirmąjį simbolį `"1"`.
4. Vertės `null` ir `undefined` yra lygios viena kitai.
5. Griežta lygybė yra griežta. Skirtingi abiejų pusių tipai lemia false.
6. Panašiai į `(4)`, `null` yra lygus tik `undefined`.
7. Griežta skirtingų tipų lygybė.
