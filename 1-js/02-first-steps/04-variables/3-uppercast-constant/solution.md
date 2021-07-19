Mes dažniausiai naudojame didžiąsias raides konstantoms, kurios yra iš anksto užprogramuotos (angliškai vadinamos "hard-coded"). Arba kitaip sakant kai vertė yra žinoma prieš įvykdymą ir yra tiesiai įrašyta į kodą.

Šis kodas, `birthday` yra būtent toks. Tad mes galime jam naudoti didžiąsias raides.

Tačiau priešingai yra su `age`, kuris yra įvertinamas vykdymo metu. Šiandien mes turime vienokį amžių, bet po metų jis jau bus kitoks. Jis yra konstanta tik dėl to, kad jis nesikeičia įvykdant kodą. Bet jis yra kiek "mažiau pastovus" negu `birthday`: jis yra suskaičiuojamas, dėl tos priežasties turėtume jam palikti mažąsias raides.
