
# Vadovai ir specifikacija

Ši knyga yra *pamokų formato*. Jos tikslas - padėti palaipsniui išmokti kalbą. Tačiau kuomet išmoksti pagrindus, prireikia kitų resursų.

## Specifikacija

[The ECMA-262 specification](https://www.ecma-international.org/publications/standards/Ecma-262.htm) turi pačią nuodugniausią, detalią ir formalią informaciją apie JavaScript. Iš esmės, ši specifikacija apibrėžia pačią kalbą.

Tačiau iš šios specifikacijos mokytis iš pat pradžių yra gana sunku, nes informacija labai formali. Jeigu reikia pačios tiksliausios informacijos apie kalbą, specifikacija yra puikus šaltinis. Tačiau vargu, ar to prireiks kiekvieną dieną.

Kasmet yra išleidžiama nauja specifikacijos versija. Tarp šitų išleidimų, galima rasti juodraštį (ang. "draft") čia <https://tc39.es/ecma262/>.

Galite perskaityti apie naujausias savybes, įskaitant ir tas, kurios yra "beveik standartas" (dar vadinamas "stage 3") galima rasti <https://github.com/tc39/proposals>.

<<<<<<< HEAD
Taip pat, jeigu norite programuoti naršyklei, tam yra kita specifikacija, kurią gali rasti [antroje](info:browser-environment) pamokų dalyje.
=======
Also, if you're developing for the browser, then there are other specifications covered in the [second part](info:browser-environment) of the tutorial.
>>>>>>> 246c600f11b4e6c52b4ae14f83e65319671f998f

## Vadovai
- **MDN (Mozilla) JavaScript Reference** yra vadovas su pavyzdžiais ir kita informacija. Tinka, jeigu reikia detalios informacijos apie konkrečias kalbos funkcijas, metodus, ir pan.

<<<<<<< HEAD
	Vadovą galima rasti <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference>.
=======
- **MDN (Mozilla) JavaScript Reference** is the main manual with examples and other information. It's great to get in-depth information about individual language functions, methods etc.
>>>>>>> 246c600f11b4e6c52b4ae14f83e65319671f998f

	Tačiau, dažniausiai geriausia tiesiog ieškoti informacijos internete. Verta tiesiog naudoti "MDN [apibrėžimas]" užklausoje, pavyzdžiui <https://google.com/search?q=MDN+parseInt> tam, kad rastumėte informacijos apie `parseInt` funkciją.

<<<<<<< HEAD

- **MSDN** - Microsoft vadovas, turintis daug informacijos, įskaitant JavaScript (dažnai vadinamas JScript). Jeigu reikia kažko konkretaus skirto Internet Explorer, geriau eiti čia: <http://msdn.microsoft.com/>.

	Taip pat, galima naudoti paiešką internete su frazėmis, tokiomis kaip "RegExp MSDN" arba "RegExp MSDN jscript".

## Suderinamumo (ang "compatibility") lentelės
=======
Although, it's often best to use an internet search instead. Just use "MDN [term]" in the query, e.g. <https://google.com/search?q=MDN+parseInt> to search for `parseInt` function.
>>>>>>> 246c600f11b4e6c52b4ae14f83e65319671f998f

JavaScript yra nuolatos tobulinama kalba, todėl naujos savybės atsiranda reguliariai.

Pamatyti, ar šias savybes palaiko konkrečios naršyklės ar kiti varikliai, galima čia:

- <http://caniuse.com> - kiekvienos savybės suderinamumo lentelės. T.y. kad pamatyti kurie varikliai palaiko modernias kriptografijos funkcijas: <http://caniuse.com/#feat=cryptography>.
- <https://kangax.github.io/compat-table> - lentelė su kalbos savybe ir varikliais, kurie palaiko/nepalaiko šias savybes.

Visi šie šaltiniai yra naudingi realiame pasaulyje, nes jie turi svarbios informacijos apie kalbą, suderinamumą ir pan.

Prisimink juos tiems atvejams, kai reikės detalios informacijos apie konkrečią savybę.
