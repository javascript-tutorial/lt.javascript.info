
# Manualai ir specifikacijos

Ši knyga yra *tutorialas*. Jo tikslas - padėti palaipsniui išmokti kalbą. Tačiau kuomet išmoksti basic'us, prireikia kitų resursų.

## Specifikacija

[The ECMA-262 specification](https://www.ecma-international.org/publications/standards/Ecma-262.htm) turi pačią nuodugniausią, detalią ir formalią informaciją apie JavaScript'ą. Iš esmės, ši specifikacija apibrėžia pačią kalbą.

Tačiau iš šios specifikacijos mokytis iš pat pradžių yra ganėtinai sunku, nes informacija yra labai formali. Taip, kad jeigu reikia pačios tiksliausios informacijos apie kalbą, specifikacija yra puikus resursas. Tačiau vargu, ar to prireiks kiekvieną dieną.

Nauja specifikacijos versija yra išleidžiama kasmet. Tarp šitų releas'ų, juodraštį (draft'ą) galima rasti <https://tc39.es/ecma262/>.

Perskaityti apie naujausius features, įskaitant ir tuos, kurie yra "beveik standartas" (dar vadinama "stage 3") galima rasti <https://github.com/tc39/proposals>.

<<<<<<< HEAD
Taip pat, jeigu norima programuoti naršyklei, tam yra kita specifikacija, kurią gali rasti [antroje](info:browser-environment) tutorial'o dalyje.
=======
Also, if you're in developing for the browser, then there are other specifications covered in the [second part](info:browser-environment) of the tutorial.
>>>>>>> 97ef86242f9f236b13152e1baf52a55c4db8728a

## Manualai
- **MDN (Mozilla) JavaScript Reference** yra manualas su pavyzdžiais ir kita informacija. Tinka, jeigu reikia detalios informacijos apie konkrečias kalbos funkcijas, metodus, ir pan.

<<<<<<< HEAD
	Manualą galima rasti <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference>.
=======
- **MDN (Mozilla) JavaScript Reference** is the main manual with examples and other information. It's great to get in-depth information about individual language functions, methods etc.
>>>>>>> 97ef86242f9f236b13152e1baf52a55c4db8728a

	Tačiau, dažniausiai geriausia tiesiog ieškoti informacijos internete. Verta tiesiog naudoti "MDN [apibrėžimas]" užklausoje, pavyzdžiui <https://google.com/search?q=MDN+parseInt> tam, kad rasti informacijos apie `parseInt` funkciją.

<<<<<<< HEAD

- **MSDN** - Microsoft'o manualas, turintis daug informacijos, įskaitant JavaScript'ą (dažnai vadinamas JScript). Jeigu reikia kažko konkretaus Internet Explorer'iui, geriau eiti čia: <http://msdn.microsoft.com/>.

	Taip pat, galima naudoti paiešką internete su frazėmis, tokiomis kaip "RegExp MSDN" arba "RegExp MSDN jscript".

## Suderinamumo (compatibility) lentelės
=======
Although, it's often best to use an internet search instead. Just use "MDN [term]" in the query, e.g. <https://google.com/search?q=MDN+parseInt> to search for `parseInt` function.
>>>>>>> 97ef86242f9f236b13152e1baf52a55c4db8728a

JavaScript yra nuolatos tobulinama kalba, todėl nauji features atsiranda reguliariai.

Pamatyti, ar šiuos features palaiko konkrečios naršyklės ar kiti varikliai, galima čia:

- <http://caniuse.com> - kiekvieno feature suderinamumo lentelės. T.y. kad pamatyti kurie varikliai palaiko modernias kriptografijos funkcijas: <http://caniuse.com/#feat=cryptography>.
- <https://kangax.github.io/compat-table> - lentelė su kalbos features ir varikliais, kurie palaiko/nepalaiko šiuos features

Visi šie resursai yra naudingi realiam pasaulyje, nes jie turi svarbios informacijos apie kalbą, suderinamumą ir pan

Prisimink juos tiems atvejams, kai reikės detalios informacijos apie konkretų feature.
