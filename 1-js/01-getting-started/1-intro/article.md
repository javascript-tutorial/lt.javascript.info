# Įvadas į JavaScript  

<<<<<<< HEAD
Pažvelkime kuo įpatinga JavaScript kalba, ką mes galime su ja padaryti ir kokios kitos technologijos gali būti naudojamos kartu su ja
=======
Let's see what's so special about JavaScript, what we can achieve with it, and what other technologies play well with it.
>>>>>>> e01998baf8f85d9d6cef9f1add6c81b901f16d69

## Kas yra JavaScript?

<<<<<<< HEAD
Iš pat pradžių *JavaScript* buvo sukurtas tam, kad *"padaryti tinklalapius gyvus"*.
=======
*JavaScript* was initially created to "make web pages alive".
>>>>>>> e01998baf8f85d9d6cef9f1add6c81b901f16d69

Programos, parašytos šia kalba yra vadinamos *skriptais*. Jos gali būti parašytos tinklalapio HTML ir veikti automatiškai, kuomet tinklalapis kraunamas.

Skriptai yra rašomi ir vykdomi plain tekstu. Jiem nereikia kompiliavimo fazės.

Šiuo aspektu JavaScript labai skiriasi nuo [Java](https://en.wikipedia.org/wiki/Java_(programming_language)).

```smart header="Iš kur kilo pavadinimas JavaScript?"
Iš pat pradžių JavaScript turėjo kitą pavadinimą: "LiveScript". Tačiau Java buvo itin populiari, todėl buvo nuspręsta pateikti naują kalbą kaip Java "jaunesnį brolį".

Tačiau ilgainiui JavaScript tapo nepriklausoma kalba, turinti atskirą specifikaciją, kuri vadinama [ECMAScript](http://en.wikipedia.org/wiki/ECMAScript). Šiuo metu JavaScript ir Java neturi nieko bendro. 
```

Dabar JavaScript gali būti vykdomas ne tik naršyklėje, bet taip pat ir serveryje arba praktiškai bet kokiame įrenginyje, kuris turi specialią programą, vadinama JavaScript varikliu [(JavaScript engine)](https://en.wikipedia.org/wiki/JavaScript_engine).

Naršyklės turi savo vidinį variklį, kuris kartais vadinamas "JavaScript virtuali mašiną"

Skirtingi varikliai turi skirtingus "nickus". Pavyzdžiui:

<<<<<<< HEAD
- [V8](https://en.wikipedia.org/wiki/V8_(JavaScript_engine)) -- Chrome ir Opera.
- [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey) -- Firefox.
- Egzistuoja kitų nickų, tokių kaip "Trident", "Chakra" skirtingom IE versijom, "ChakraCore" Microsoft Edge naršklėje, "Nitro" ir "SquirellFish" Safari ir t.t.
=======
- [V8](https://en.wikipedia.org/wiki/V8_(JavaScript_engine)) -- in Chrome and Opera.
- [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey) -- in Firefox.
- ...There are other codenames like "Chakra" for IE, "ChakraCore" for Microsoft Edge, "Nitro" and "SquirrelFish" for Safari, etc.
>>>>>>> e01998baf8f85d9d6cef9f1add6c81b901f16d69

Šias sąvokas verta atsiminti, nes jos naudojamos straipsniuose, skirtuose programuotojams. Mes taip pat jas naudosime. Pavyzdžiui, jeigu "feature X yra palaikoma V8", reiškias jinai ko gero veikia Chrome ir Opera naršklėse.

```smart header="Kaip veikia varikliai?"

Varikliai yra sudėtingi daiktai, bet basic'ai yra paprasti.

1. Variklis (vidinis, jei jis yra naršyklėje) skaito ("parsina") skriptą.
2. Konvertuoja ("kompiliuoja") skriptą į mašininį kodą.
3. Vykdomas mašininis kodas.

Varikliai optimizuoja kodą kiekviename žingsnyje. Jie netgi stebi sukompiliuotą skriptą, kuomet jis vykdomas, bei analizuoja duomenis, kurie jame naudojami, ir pagal tai taiko papildomas optimizacijas. Po viso šio procesio, skriptai yra vykdomi gan greitai.
```

## Ką gali JavaScript'as padaryti naršyklėje?

Modernus JavaScript'as yra "saugi" programavimo kalba. Ji neleidžia programuotojui pasiekti atminties arba CPU, nes iš pat pradžių ji buvo sukurta naršklėm, kuriom to nereikia.

JavaScript'o galimybės stipriai priklauso nuo aplinkos, kurioje jis vykdomas. Pavyzdžiui, [Node.js](https://wikipedia.org/wiki/Node.js) palaiko funkcijas, kurios leidžia Javascript'ui skaityti/rašyti failus, vykdyti kompiuterių tinklų užklausas ir pan.

Naršyklėje JavaScript'as gali daryti bet ką, kas liečia tinklalapio manipuliacijas, interakcijas su vartotojais ir web serveriu.

Pavyzdžiui, JavaScript'as naršyklėje gali:

- Pridėti naują HTML į tinklalapį, pakeisti jau esamą turinį, pakeisti stilius.
- Reaguoti į vartotojo veiksmus, pelės, klaviatūros paspaudimus.
- Siųsti užklausas į remote serverius, atsisiųsti ir upload'inti failus ([AJAX](https://en.wikipedia.org/wiki/Ajax_(programming)) ir [COMET](https://en.wikipedia.org/wiki/Comet_(programming)) technologijos).
- Gauti ir nustatyti cookies, klausti vartotojo, parodyti žinutes.
- Išsaugoti duomenis kliento pusėje ("local storage").

## Ko NEGALI JavaScript'as naršyklėje?

JavaScript'o galimybės naryklėje yra ribojamos dėl vartotojų saugumo. Tikslas - neleisti tinklalapiam pasiekti privačius duomenis arba žaloti vartotojo duomenis.

Ribojimų pavyzdžiai:
- JavaScript'as tinklalapyje negali skaityti/rašyti failus kietajame diske, juos kopijuoti arba vykdyti programas. JavaScript'as neturi tiesioginios prieigos prie operacinės sistemos funkcijų. 

<<<<<<< HEAD
	Modernios naršklės leidžia dirbti su failais, bet prieiga ribojama ir tai leidžiama tik jeigu vartotojas įvykdo kažką konkretaus. Pavyzdžiui, dragg'ina failą į naršklę arba pažymi failą per `<input>` tagą.
=======
- JavaScript on a webpage may not read/write arbitrary files on the hard disk, copy them or execute programs. It has no direct access to OS functions.
>>>>>>> e01998baf8f85d9d6cef9f1add6c81b901f16d69

Yra būdų komunikuoti su kamera/mikrofonu ir kitais įrenginiais, bet tai reikalauja išreikštinio vartotojo leidimo. Taigi, JavaScript'inis tinklalapis negali suktai įjungti web kamerą, stebėti aplinką ir siųsti informaciją į [NSA](https://en.wikipedia.org/wiki/National_Security_Agency).
- Skirtingi tabai dažniausiai nežino vienas apie kitą. Tačiau kartais vienas tab'as naudoja JavaScript'ą tam, kad atidarytų kitą tab'ą, bet netgi tokiu atveju, JavaScript'as viename tab'e negali pasiekti kito tab'o, jeigu jie ateina iš skirtingų tinklalapių (skirtingas domenas, protokolas arba portas).
	Tai vadinama "Same Origin Policy". Tam, kad tai apeiti, *abudu tinklalapiai* turi sutikti apsikeisti duomenimis ir turėti specialų JavaScript kodą, kuris tai handlintų. Mes apie tai kalbėsime viename iš tutorialų.
	Šis ribojimas yra, vėlgi, dėl vartotojų saugmo. Tinklapis `http://anysite.com`, kurį vartotojas atidarė, neturėtų pasiekti kito naršklės tabo su URL `http://gmail.com` ir vogti informaciją.
- JavaScript'as gali lengvai komunikuoti internetu su serveriu, iš kurio atėjo tinklalapis. Bet tinklalapio galimybės gauti duomenis iš kitų tinklapių/duomenų yra kiek sudėtingesnės. Nors ir įmanoma, tai reikalauja išreikštinio susitarimo (per HTTP header'ius) iš remote serverio pusės. Vėlgi, dėl saugumo priežasčių.

![](limitations.svg)

Šių ribojimų nėra, jeigu JavaScript'as vykdomas ne naršyklėje, bet, pavyzdžiui, serveryje. Šiuolaikinės naršyklės taip pat turi plugin'us/extension'us, kurie gali prašyti vartotojų leidimo.

## Ko ypatingas JavaScript?

JavaScript turi bent jau *tris* nuostabius dalykus:

```compare
+ Pilna integracija su HTML/CSS
+ Paprastus dalykus padaryti yra nesudėtinga
+ Palaikoma visuose populiariausiuose naršyklėse
```
JavaScript'as yra vienintelė naršyklės technologija, kuri turi šiuos tris dalykus

Štai kuo ypatingas JavaScript'as. Dėl to tai yra viena labiausiai išplitusių technologijų, kalbant apie naršyklės interfeiso kūrimą.

Tačiau su JavaScript'u galima rašyti serverines, mobilias aplikacijas ir pan.

## Alternatyvos

JavaScript'o sintaksė, be abejo, tinka ne visiem ir ne visada. Skirtingi žmonės nori skirtingų pribumbasų.

Tas yra logiška, nes kiekvienas projektas yra skirtingas ir gali turėti labai skirtingų reikalavimų.

Dėl šių priežasčių atsirado daug kalbų, kurios yra *transpiliuojamos* (konvertuojamos) į JavaScript'ą ir tik tada vykdomos naršyklėje.

Modernūs įrankiai atlieką transpiliavimą labai greitai, tad programuotojai gali programuoti šiomis kalbomis nesigilindami į patį transpiliavimo procesą.

Tokių kalbų pavyzdžiai:

<<<<<<< HEAD
- [CoffeeScript](http://coffeescript.org/) yra "syntactic sugar" JavaScript'ui. Trumpesnė sintaksė, su kuria galima rašyti aiškesnį ir konkretesnį kodą. Tas dažniausiai patinka Ruby programuotojams.
- [TypeScript](http://www.typescriptlang.org/) pagrindinis tikslas yra įvesti statinį tipizavimą. Tas palengvina sudėtingų sistemų programavimą. Sukurtas Microsft.
- [Flow](http://flow.org/) taip pat turi statinį tipizavimą, bet kiek kitokiu būdu. Sukurtas Facebook.
- [Dart](https://www.dartlang.org/) yra atskira kalba, kuri turi savo paties variklį, kuris veikia ne naršyklėse (pvz. mobiliose aplikacijose), bet taip pat gali būti transpiliuotas į Javascriptą. Sukurtas Google.
=======
- [CoffeeScript](http://coffeescript.org/) is a "syntactic sugar" for JavaScript. It introduces shorter syntax, allowing us to write clearer and more precise code. Usually, Ruby devs like it.
- [TypeScript](http://www.typescriptlang.org/) is concentrated on adding "strict data typing" to simplify the development and support of complex systems. It is developed by Microsoft.
- [Flow](http://flow.org/) also adds data typing, but in a different way. Developed by Facebook.
- [Dart](https://www.dartlang.org/) is a standalone language that has its own engine that runs in non-browser environments (like mobile apps), but also can be transpiled to JavaScript. Developed by Google.
- [Brython](https://brython.info/) is a Python transpiler to JavaScript that enables the writing of applications in pure Python without JavaScript.
- [Kotlin](https://kotlinlang.org/docs/reference/js-overview.html) is a modern, concise and safe programming language that can target the browser or Node.
>>>>>>> e01998baf8f85d9d6cef9f1add6c81b901f16d69

Yra ir daugiaų pavyzdžių. Tačiau, netgi jeigu mes naudojame kažkurią iš transpiliuojamų kalbų, suprasti JavaScript'ą yra ne mažiau svarbu.

## Reziumė

<<<<<<< HEAD
- JavaScript'as iš pat pradžių buvo sukurtas kaip kalba, veikianti naršyklėje, bet dabar turi ir daugiau aplinkų, kuriose gali būti vykdoma.
- Šią dieną JavaScript'as yra unikalus tuo, kad tai labiausiai paplitusi kalba naršyklei, turinti pilną integraciją su HTML/CSS.
- Yra daug kalbų, kurios gali būti "transipliuotos" į JavaScript'ą ir turi papildomų funkcijų. Rekomenduojama į jas bent jau trumpai pažvelgti po to, kaip išmoksti JavaScript'ą.
=======
- JavaScript was initially created as a browser-only language, but it is now used in many other environments as well.
- Today, JavaScript has a unique position as the most widely-adopted browser language with full integration in HTML/CSS.
- There are many languages that get "transpiled" to JavaScript and provide certain features. It is recommended to take a look at them, at least briefly, after mastering JavaScript.
>>>>>>> e01998baf8f85d9d6cef9f1add6c81b901f16d69
