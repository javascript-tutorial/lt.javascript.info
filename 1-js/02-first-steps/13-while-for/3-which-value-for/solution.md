**Atsakymas: nuo `0` iki `4` abiem atvejais.**

```js run
for (let i = 0; i < 5; ++i) alert( i );

for (let i = 0; i < 5; i++) alert( i );
```

Tai galima labai lengvai nustatyti iš `for` algoritmo:

1. Įvykdyti vieną kartą `i = 0` prieš visa kita (pradžia).
2. Patikrinti sąlygą `i < 5`
3. Jeigu `true` -- įvykdyti ciklo korpusą `alert(i)`, o tada `i++`

Padidėjimas `i++` yra atskirtas nuo sąlygos patikrinimo (2). Tai tik dar vienas teiginys.

Vertė grąžinta padidėjimo nėra čia naudojama, tad nėra jokio skirtumo tarp `i++` ir `++i`.
