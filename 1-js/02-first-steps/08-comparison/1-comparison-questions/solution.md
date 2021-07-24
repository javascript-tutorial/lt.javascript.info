

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

1. Akivaizdžiai tiesa.
2. Žodynėlio palyginimas, tad netiesa.
3. Vėlgi, žodynėlio palyginimas, tad pirmasis ženklas eilutėje `"2"` yra didenis nei pirmasis ženklas eilutėje `"1"`.
4. Vertės `null` ir `undefined` yra lygios viena kitai.
5. Griežta lygybė yra griežta. Skirtingi tipai abiejose pusėse atveda prie netiesos.
6. Panašiai į `(4)`, `null` yra lygus tik `undefined`.
7. Griežta skirtingų tipų lygybė.
