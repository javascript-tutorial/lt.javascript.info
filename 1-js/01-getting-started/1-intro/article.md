# JavaScript įvadas

<<<<<<< HEAD
Pažvelkime kuo ypatinga JavaScript kalba, ką mes galime su ja padaryti ir kokios kitos technologijos gali būti naudojamos kartu.
=======
Let's see what's so special about JavaScript, what we can achieve with it, and what other technologies play well with it.
>>>>>>> a6fdfda09570a8ce47bb0b83cd7a32a33869cfad

## Kas yra JavaScript?

<<<<<<< HEAD
Iš pat pradžių *JavaScript* buvo sukurta tam, kad *"padarytų tinklalapius gyvus"*.
=======
*JavaScript* was initially created to "make web pages alive".
>>>>>>> a6fdfda09570a8ce47bb0b83cd7a32a33869cfad

Programos, parašytos šia kalba yra vadinamos *skriptais* (and. scripts). Jos gali būti parašytos tinklalapio HTML ir suveikti automatiškai, kuomet tinklalapis kraunamas.

Skriptai yra rašomi ir vykdomi paprastu (ang. "plain") tekstu. Jiems nereikia kompiliavimo fazės.

Šiuo aspektu JavaScript labai skiriasi nuo [Java](https://en.wikipedia.org/wiki/Java_(programming_language)).

```smart header="Iš kur kilo pavadinimas JavaScript?"
Iš pat pradžių JavaScript turėjo kitą pavadinimą: "LiveScript". Tačiau Java buvo itin populiari, todėl buvo nuspręsta pateikti naują kalbą kaip Java "jaunesnį brolį".

Tačiau ilgainiui JavaScript tapo nepriklausoma kalba, turinti atskirą specifikaciją, kuri vadinama [ECMAScript](http://en.wikipedia.org/wiki/ECMAScript). Šiuo metu JavaScript ir Java neturi nieko bendro. 
```

Dabar JavaScript gali būti vykdomas ne tik naršyklėje, bet taip pat ir serveryje arba praktiškai bet kokiame įrenginyje, kuris turi specialią programą, vadinamą JavaScript varikliu [(JavaScript engine)](https://en.wikipedia.org/wiki/JavaScript_engine).

Naršyklės turi savo vidinį variklį, kuris kartais vadinamas "JavaScript virtuali mašina"

Skirtingi varikliai turi skirtingus slapyvardžius (ang. "nicknames"). Pavyzdžiui:

<<<<<<< HEAD
- [V8](https://en.wikipedia.org/wiki/V8_(JavaScript_engine)) -- Chrome ir Opera.
- [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey) -- Firefox.
- Egzistuoja kiti slapyvardžiai, tokie kaip "Trident", "Chakra" skirtingoms IE versijom, "ChakraCore" Microsoft Edge naršklėje, "Nitro" ir "SquirellFish" Safari ir t.t.

Šias sąvokas verta atsiminti, nes jos naudojamos straipsniuose, skirtuose programuotojams. Mes taip pat jas naudosime. Pavyzdžiui, jeigu "feature X yra palaikoma V8", reiškias jinai ko gero veikia Chrome ir Opera naršklėse.
=======
- [V8](https://en.wikipedia.org/wiki/V8_(JavaScript_engine)) -- in Chrome, Opera and Edge.
- [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey) -- in Firefox.
- ...There are other codenames like "Chakra" for IE, "JavaScriptCore", "Nitro" and "SquirrelFish" for Safari, etc.

The terms above are good to remember because they are used in developer articles on the internet. We'll use them too. For instance, if "a feature X is supported by V8", then it probably works in Chrome, Opera and Edge.
>>>>>>> a6fdfda09570a8ce47bb0b83cd7a32a33869cfad

```smart header="Kaip veikia varikliai?"

Varikliai yra sudėtingi, bet pagrindai yra paprasti.

1. Variklis (vidinis, jei jis yra naršyklėje) skaito (ang. "parsing") skriptą.
2. Konvertuoja (dar kitaip - kompiliuoja) skriptą į mašininį kodą.
3. Įvykdomas mašininis kodas.

Varikliai optimizuoja kodą kiekviename žingsnyje. Jie netgi stebi sukompiliuotą skriptą, kuomet jis vykdomas, bei analizuoja duomenis, kurie jame naudojami, ir pagal tai taiko papildomas optimizacijas. Po viso šio procesio, skriptai yra vykdomi gan greitai.
```

## Ką gali JavaScript padaryti naršyklėje?

Modernus JavaScript yra "saugi" programavimo kalba. Ji neleidžia programuotojui pasiekti atminties arba CPU, nes iš pat pradžių ji buvo sukurta naršyklėms, kurioms to nereikia.

JavaScript galimybės stipriai priklauso nuo aplinkos, kurioje ji vykdomas. Pavyzdžiui, [Node.js](https://wikipedia.org/wiki/Node.js) palaiko funkcijas, kurios leidžia Javascript skaityti/rašyti failus, vykdyti kompiuterių tinklų užklausas ir pan.

Naršyklėje JavaScript gali daryti bet ką, tame tarpe tinklalapio manipuliacijas, sąveikas (ang. "interaction") su vartotojais ir web serveriu.

Pavyzdžiui, JavaScript naršyklėje gali:

- Pridėti naują HTML į tinklalapį, pakeisti jau esamą turinį, pakeisti stilius.
- Reaguoti į vartotojo veiksmus, pelės, klaviatūros paspaudimus.
- Siųsti užklausas į nuotolinius (ang. "remote") serverius, atsisiųsti ir įkelti (ang. "upload") failus ([AJAX](https://en.wikipedia.org/wiki/Ajax_(programming)) ir [COMET](https://en.wikipedia.org/wiki/Comet_(programming)) technologijos).
- Gauti ir nustatyti slapukus (ang. "cookies"), užduoti klausimus vartotojo ir parodyti žinutes.
- Išsaugoti duomenis kliento pusėje (ang. "local storage").

## Ko NEGALI PADARYTI JavaScript naršyklėje?

<<<<<<< HEAD
JavaScript galimybės naryklėje yra ribojamos dėl vartotojų saugumo. Tikslas - neleisti tinklalapiams pasiekti privačius duomenis arba žaloti vartotojo duomenis.
=======
JavaScript's abilities in the browser are limited for the sake of a user's safety. The aim is to prevent an evil webpage from accessing private information or harming the user's data.
>>>>>>> a6fdfda09570a8ce47bb0b83cd7a32a33869cfad

Ribojimų pavyzdžiai:
- JavaScript tinklalapyje negali skaityti/rašyti failus esančius kietajame diske, juos kopijuoti arba vykdyti programas. JavaScript neturi tiesioginės prieigos prie operacinės sistemos funkcijų. 

<<<<<<< HEAD
	Modernios naršklės leidžia dirbti su failais, bet prieiga ribojama ir tai leidžiama tik jeigu vartotojas įvykdo kažką konkretaus. Pavyzdžiui, perkelia failą į naršyklę arba pažymi failą naudodamas `<input>` žymą.
=======
- JavaScript on a webpage may not read/write arbitrary files on the hard disk, copy them or execute programs. It has no direct access to OS functions.
>>>>>>> a6fdfda09570a8ce47bb0b83cd7a32a33869cfad

Yra būdų komunikuoti su kamera/mikrofonu ir kitais įrenginiais, bet tai reikalauja išreikštinio vartotojo leidimo. Taigi, JavaScript tinklalapis negali suktai įjungti web kameros, stebėti aplinkos ir siųsti informaciją į [NSA](https://en.wikipedia.org/wiki/National_Security_Agency).
- Atskiros naršyklės kortelės (ang. "tabs") dažniausiai nežino viena apie kitą. Tačiau kartais viena kortelė naudoja JavaScript tam, kad atidarytų kitą kortelę, bet netgi tokiu atveju, JavaScript vienoje kortelėje negali pasiekti kitos, jeigu jie ateina iš skirtingų tinklalapių (skirtingas domenas, protokolas arba portas).
	Tai vadinama "Same Origin Policy". Tam, kad tai apeiti, *abudu tinklalapiai* turi sutikti apsikeisti duomenimis ir turėti specialų JavaScript kodą, kuris tai tvarkytų. Mes apie tai kalbėsime vienoje iš pamokų.
	Šis ribojimas yra, vėlgi, dėl vartotojų saugmo. Tinklapis `http://anysite.com`, kurį vartotojas atidarė, neturėtų pasiekti kitos naršklės kortelės su URL `http://gmail.com` ir vogti informaciją.
- JavaScript gali lengvai komunikuoti internetu su serveriu, iš kurio atėjo tinklalapis. Bet tinklalapio galimybės gauti duomenis iš kitų tinklapių/duomenų yra kiek sudėtingesnės. Nors ir įmanoma, tai reikalauja išreikštinio susitarimo (per HTTP antraštes) iš nuotolinio serverio pusės. Vėlgi, dėl saugumo priežasčių.

![](limitations.svg)

Šių ribojimų nėra, jeigu JavaScript vykdomas ne naršyklėje, bet, pavyzdžiui, serveryje. Šiuolaikinės naršyklės taip pat turi papildinius ir plėtinius(ang. "plugins/extensions"), kurie gali prašyti vartotojų leidimo.

## Kuo ypatinga JavaScript?

JavaScript turi bent *tris* nuostabius dalykus:

```compare
<<<<<<< HEAD
+ Pilna integracija su HTML/CSS
+ Paprastus dalykus padaryti yra nesudėtinga
+ Palaikoma visose populiariausiose naršyklėse
=======
+ Full integration with HTML/CSS.
+ Simple things are done simply.
+ Supported by all major browsers and enabled by default.
>>>>>>> a6fdfda09570a8ce47bb0b83cd7a32a33869cfad
```
JavaScript yra vienintelė naršyklės technologija, kuri turi šiuos tris dalykus.

Štai kuo ypatinga JavaScript. Tai yra viena labiausiai išplitusių technologijų, kalbant apie naršyklės sąsajos (ang. "interface") kūrimą.

Tačiau su JavaScript galima rašyti serverines, mobilias programas (ang. "applications") ir pan.

## Alternatyvos

JavaScript sintaksė, be abejo, tinka ne visiem ir ne visada. Skirtingi žmonės nori skirtingų savybių.

Nieko nuostabaus, nes kiekvienas projektas yra skirtingas ir gali turėti labai skirtingų reikalavimų.

Dėl šių priežasčių atsirado daug kalbų, kurios yra konvertuojamos (dar kitaip - perrašomos, ang. "*transpiling*") į JavaScript ir tik tada vykdomos naršyklėje.

Modernūs įrankiai atlieka perrašymą labai greitai, tad programuotojai gali programuoti šiomis kalbomis nesigilindami į patį konvertavimo procesą.

Tokių kalbų pavyzdžiai:

<<<<<<< HEAD
- [CoffeeScript](http://coffeescript.org/) yra "syntactic sugar" JavaScript. Trumpesnė sintaksė, su kuria galima rašyti aiškesnį ir konkretesnį kodą. Tai dažniausiai patinka Ruby programuotojams.
- [TypeScript](http://www.typescriptlang.org/) pagrindinis tikslas yra įvesti statinį tipizavimą. Tai palengvina sudėtingų sistemų programavimą. Sukurtas Microsoft.
- [Flow](http://flow.org/) taip pat turi statinį tipizavimą, bet kiek kitokiu būdu. Sukurtas Facebook.
- [Dart](https://www.dartlang.org/) yra atskira kalba, kuri turi savo paties variklį, kuris veikia ne naršyklėse (pvz. mobiliose aplikacijose), bet taip pat gali būti transpiliuotas į Javascriptą. Sukurtas Google.
=======
- [CoffeeScript](http://coffeescript.org/) is a "syntactic sugar" for JavaScript. It introduces shorter syntax, allowing us to write clearer and more precise code. Usually, Ruby devs like it.
- [TypeScript](http://www.typescriptlang.org/) is concentrated on adding "strict data typing" to simplify the development and support of complex systems. It is developed by Microsoft.
- [Flow](http://flow.org/) also adds data typing, but in a different way. Developed by Facebook.
- [Dart](https://www.dartlang.org/) is a standalone language that has its own engine that runs in non-browser environments (like mobile apps), but also can be transpiled to JavaScript. Developed by Google.
- [Brython](https://brython.info/) is a Python transpiler to JavaScript that enables the writing of applications in pure Python without JavaScript.
- [Kotlin](https://kotlinlang.org/docs/reference/js-overview.html) is a modern, concise and safe programming language that can target the browser or Node.
>>>>>>> a6fdfda09570a8ce47bb0b83cd7a32a33869cfad

Yra ir daugiau pavyzdžių. Tačiau, netgi jeigu mes naudojame kažkurią iš transpiliuojamų kalbų, suprasti JavaScript yra ne mažiau svarbu.

## Santrauka

<<<<<<< HEAD
- JavaScript iš pat pradžių buvo sukurtas kaip kalba, veikianti naršyklėje, bet dabar turi ir daugiau aplinkų, kuriose gali būti vykdoma.
- Šią dieną JavaScript yra unikali tuo, kad tai labiausiai paplitusi kalba naršyklei, turinti pilną integraciją su HTML/CSS.
- Yra daug kalbų, kurios gali būti konvertuojamos į JavaScript ir turi papildomų funkcijų. Rekomenduojame į jas bent jau trumpai pažvelgti po to, kaip išmoksite JavaScript.
=======
- JavaScript was initially created as a browser-only language, but it is now used in many other environments as well.
- Today, JavaScript has a unique position as the most widely-adopted browser language, fully integrated with HTML/CSS.
- There are many languages that get "transpiled" to JavaScript and provide certain features. It is recommended to take a look at them, at least briefly, after mastering JavaScript.
>>>>>>> a6fdfda09570a8ce47bb0b83cd7a32a33869cfad
