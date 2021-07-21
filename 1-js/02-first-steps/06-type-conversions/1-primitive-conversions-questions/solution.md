
```js no-beautify
"" + 1 + 0 = "10" // (1)
"" - 1 + 0 = -1 // (2)
true + false = 1
6 / "3" = 2
"2" * "3" = 6
4 + 5 + "px" = "9px"
"$" + 4 + 5 = "$45"
"4" - 2 = 2
"4px" - 2 = NaN
7 / 0 = Infinity
" -9  " + 5 = " -9  5" // (3)
" -9  " - 5 = -14 // (4)
null + 1 = 1 // (5)
undefined + 1 = NaN // (6)
" \t \n" - 2 = -2 // (7)
```

1. Sudėtis su eilute `"" + 1` paverčia `1` į eilutę: `"" + 1 = "1"`, o tada mes turime `"1" + 0`, taikoma ta pati taisyklė.
2. Atimtis `-` (kaip ir didžioji dalis matematinių operacijų) veikia tik su skaičiais, tad tuščią eilutę `""` paverčia į `0`.
3. Sudėtis su eilute prijungia skaičių `5` prie eilutės.
4. Atimtis visada paverčia į numerius, tad `"  -9  "` tampa numeriu `-9` (ignoruoja tarpus aplink).
5. `null` tampa `0` po skaičių konversijos.
6. `undefined` tampa `NaN` po skaičių konversijos.
7. Tarpų ženklai yra nukerpami nuo eilutės pradžios ir pabaigos kai eilutė paverčiama į skaičių. Čia visa eilutė susideda iš tarpo ženklų kaip `\t`, `\n` ir "įprastinių" tarpų esančių tarp jų. Tad panašiai kaip ir tuščia eilutė, ji tampa `0`.
