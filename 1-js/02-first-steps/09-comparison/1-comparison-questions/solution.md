

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

<<<<<<< HEAD:1-js/02-first-steps/08-comparison/1-comparison-questions/solution.md
1. Akivaizdžiai tiesa.
2. Žodynėlio palyginimas, tad netiesa.
3. Vėlgi, žodynėlio palyginimas, tad pirmasis ženklas eilutėje `"2"` yra didenis nei pirmasis ženklas eilutėje `"1"`.
4. Vertės `null` ir `undefined` yra lygios viena kitai.
5. Griežta lygybė yra griežta. Skirtingi tipai abiejose pusėse atveda prie netiesos.
6. Panašiai į `(4)`, `null` yra lygus tik `undefined`.
7. Griežta skirtingų tipų lygybė.
=======
1. Obviously, true.
2. Dictionary comparison, hence false. `"a"` is smaller than `"p"`.
3. Again, dictionary comparison, first char `"2"` is greater than the first char `"1"`.
4. Values `null` and `undefined` equal each other only.
5. Strict equality is strict. Different types from both sides lead to false.
6. Similar to `(4)`, `null` only equals `undefined`.
7. Strict equality of different types.
>>>>>>> 71da17e5960f1c76aad0d04d21f10bc65318d3f6:1-js/02-first-steps/09-comparison/1-comparison-questions/solution.md
