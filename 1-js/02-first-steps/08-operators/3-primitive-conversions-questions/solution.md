
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
"  -9  " + 5 = "  -9  5" // (3)
"  -9  " - 5 = -14 // (4)
null + 1 = 1 // (5)
undefined + 1 = NaN // (6)
" \t \n" - 2 = -2 // (7)
```

<<<<<<< HEAD
1. Sudėtis su eilute `"" + 1` paverčia `1` į eilutę: `"" + 1 = "1"`, o tada mes turime `"1" + 0`, taikoma ta pati taisyklė.
2. Atimtis `-` (kaip ir didžioji dalis matematinių operacijų) veikia tik su skaičiais, tad tuščią eilutę `""` paverčia į `0`.
3. Sudėtis su eilute prijungia skaičių `5` prie eilutės.
4. Atimtis visada paverčia į numerius, tad `"  -9  "` tampa numeriu `-9` (ignoruoja tarpus aplink).
5. `null` tampa `0` po skaičių konversijos.
6. `undefined` tampa `NaN` po skaičių konversijos.
7. Tarpų ženklai yra nukerpami nuo eilutės pradžios ir pabaigos kai eilutė paverčiama į skaičių. Čia visa eilutė susideda iš tarpo ženklų kaip `\t`, `\n` ir “įprastinių” tarpų esančių tarp jų. Tad panašiai kaip ir tuščia eilutė, ji tampa `0`.
=======
1. The addition with a string `"" + 1` converts `1` to a string: `"" + 1 = "1"`, and then we have `"1" + 0`, the same rule is applied.
2. The subtraction `-` (like most math operations) only works with numbers, it converts an empty string `""` to `0`.
3. The addition with a string appends the number `5` to the string.
4. The subtraction always converts to numbers, so it makes `"  -9  "` a number `-9` (ignoring spaces around it).
5. `null` becomes `0` after the numeric conversion.
6. `undefined` becomes `NaN` after the numeric conversion.
7. Space characters are trimmed off string start and end when a string is converted to a number. Here the whole string consists of space characters, such as `\t`, `\n` and a "regular" space between them. So, similarly to an empty string, it becomes `0`.
>>>>>>> 51bc6d3cdc16b6eb79cb88820a58c4f037f3bf19
