# JavaScript įvadas

Pažvelkime kuo ypatinga JavaScript kalba, ką mes galime su ja padaryti ir kokios kitos technologijos gali būti naudojamos kartu.

## Kas yra JavaScript?

Iš pat pradžių *JavaScript* buvo sukurta tam, kad *“padarytų tinklalapius gyvus”*.

Programos, parašytos šia kalba yra vadinamos *skriptais* (and. *scripts*). Jos gali būti parašytos tinklalapio HTML ir suveikti automatiškai, kuomet tinklalapis kraunamas.

Skriptai yra rašomi ir vykdomi paprastu tekstu. Jiems nereikia kompiliavimo fazės.

Šiuo aspektu JavaScript labai skiriasi nuo [Java](https://en.wikipedia.org/wiki/Java_(programming_language)).

```smart header="Iš kur kilo pavadinimas JavaScript?"
Iš pat pradžių JavaScript turėjo kitą pavadinimą: “LiveScript”. Tačiau Java buvo itin populiari, todėl buvo nuspręsta pateikti naują kalbą kaip Java “jaunesnį brolį”.

Tačiau ilgainiui JavaScript tapo nepriklausoma kalba, turinti atskirą specifikaciją, kuri vadinama [ECMAScript](http://en.wikipedia.org/wiki/ECMAScript). Šiuo metu JavaScript ir Java neturi nieko bendro. 
```

Dabar JavaScript gali būti vykdomas ne tik naršyklėje, bet taip pat ir serveryje arba praktiškai bet kokiame įrenginyje, kuris turi specialią programą, vadinamą JavaScript varikliu [(JavaScript engine)](https://en.wikipedia.org/wiki/JavaScript_engine).

Naršyklės turi savo vidinį variklį, kuris kartais vadinamas “JavaScript virtuali mašina”.

Skirtingi varikliai turi skirtingus slapyvardžius. Pavyzdžiui:

- [V8](https://en.wikipedia.org/wiki/V8_(JavaScript_engine)) -- Chrome, Opera ir Edge.
- [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey) -- Firefox.
- ...Egzistuoja ir kiti slapyvardžiai, tokie kaip “Chakra” skirtingoms IE versijom, “JavaScriptCore”, “Nitro”, “SquirellFish” skirta Safari ir t.t.

Šias sąvokas verta atsiminti, nes jos naudojamos straipsniuose, skirtuose programuotojams. Mes taip pat jas naudosime. Pavyzdžiui, jeigu “feature X yra palaikoma V8”, reiškias jinai ko gero veikia Chrome, Opera ir Edge naršyklėse.

```smart header="Kaip veikia varikliai?"

Varikliai yra sudėtingi, bet pagrindai yra paprasti.

<<<<<<< HEAD
1. Variklis (vidinis, jei jis yra naršyklėje) skaito skriptą.
2. Konvertuoja (dar kitaip - kompiliuoja) skriptą į mašininį kodą.
3. Įvykdomas mašininis kodas.
=======
1. The engine (embedded if it's a browser) reads ("parses") the script.
2. Then it converts ("compiles") the script to machine code.
3. And then the machine code runs, pretty fast.
>>>>>>> 6236eb8c3cdde729dab761a1d0967a88a1a6197e

Varikliai optimizuoja kodą kiekviename žingsnyje. Jie netgi stebi sukompiliuotą skriptą, kuomet jis vykdomas, bei analizuoja duomenis, kurie jame naudojami, ir pagal tai taiko papildomas optimizacijas. Po viso šio procesio, skriptai yra vykdomi gan greitai.
```

## Ką gali JavaScript padaryti naršyklėje?

<<<<<<< HEAD
Modernus JavaScript yra “saugi” programavimo kalba. Ji neleidžia programuotojui pasiekti atminties arba CPU, nes iš pat pradžių ji buvo sukurta naršyklėms, kurioms to nereikia.
=======
Modern JavaScript is a "safe" programming language. It does not provide low-level access to memory or the CPU, because it was initially created for browsers which do not require it.
>>>>>>> 6236eb8c3cdde729dab761a1d0967a88a1a6197e

JavaScript galimybės stipriai priklauso nuo aplinkos, kurioje ji vykdomas. Pavyzdžiui, [Node.js](https://wikipedia.org/wiki/Node.js) palaiko funkcijas, kurios leidžia Javascript skaityti/rašyti failus, vykdyti kompiuterių tinklų užklausas ir pan.

Naršyklėje JavaScript gali daryti bet ką, tame tarpe tinklalapio manipuliacijas, sąveikas (ang. *interaction*) su vartotojais ir web serveriu.

Pavyzdžiui, JavaScript naršyklėje gali:

- Pridėti naują HTML į tinklalapį, pakeisti jau esamą turinį, pakeisti stilius.
- Reaguoti į vartotojo veiksmus, pelės, klaviatūros paspaudimus.
- Siųsti užklausas į nuotolinius serverius, atsisiųsti ir įkelti failus ([AJAX](https://en.wikipedia.org/wiki/Ajax_(programming)) ir [COMET](https://en.wikipedia.org/wiki/Comet_(programming)) technologijos).
- Gauti ir nustatyti slapukus (ang. *cookies*), užduoti klausimus vartotojo ir parodyti žinutes.
- Išsaugoti duomenis kliento pusėje (ang. *local storage*).

## Ko NEGALI padaryti JavaScript naršyklėje?

<<<<<<< HEAD
JavaScript galimybės naryklėje yra ribojamos dėl vartotojų saugumo. Tikslas - neleisti tinklalapiams pasiekti privačius duomenis arba žaloti vartotojo duomenis.
=======
JavaScript's abilities in the browser are limited to protect the user's safety. The aim is to prevent an evil webpage from accessing private information or harming the user's data.
>>>>>>> 6236eb8c3cdde729dab761a1d0967a88a1a6197e

Ribojimų pavyzdžiai:
- JavaScript tinklalapyje negali skaityti/rašyti failus esančius kietajame diske, juos kopijuoti arba vykdyti programas. JavaScript neturi tiesioginės prieigos prie operacinės sistemos funkcijų.
	
	Modernios naršklės leidžia dirbti su failais, bet prieiga ribojama ir tai leidžiama tik jeigu vartotojas įvykdo kažką konkretaus. Pavyzdžiui, perkelia failą į naršyklę arba pažymi failą naudodamas `<input>` žymą.

	Yra būdų komunikuoti su kamera/mikrofonu ir kitais įrenginiais, bet tai reikalauja išreikštinio vartotojo leidimo. Taigi, JavaScript tinklalapis negali suktai įjungti web kameros, stebėti aplinkos ir siųsti informaciją į [NSA](https://en.wikipedia.org/wiki/National_Security_Agency).
- Atskiros naršyklės kortelės (ang. *tabs*) arba langai (ang. *windows*) paprastai nežino vienas apie kitą. Kartais jie žino, pavyzdžiui, kai vienas langas naudoja JavaScript, kad atidarytų kitą langą. Tačiau net ir tokiu atveju JavaScript iš vieno puslapio negali pasiekti kito puslapio, jei jie yra iš skirtingų svetainių (iš skirtingų domenų, protokolų ar prievadų).

	Tai vadinama “Same Origin Policy”. Norint tai apeiti, *abu tinklalapiai* turi susitarti dėl keitimosi duomenimis ir juose turi būti specialus JavaScript kodas, kuris tai tvarko. Apie tai kalbėsime vienoje iš pamokų.

<<<<<<< HEAD
	Šis ribojimas yra, vėlgi, dėl vartotojų saugmo. Tinklapis `http://anysite.com`, kurį vartotojas atidarė, neturėtų pasiekti kitos naršyklės kortelės su URL `http://gmail.com` ir vogti informaciją.
- JavaScript gali lengvai komunikuoti internetu su serveriu, iš kurio atėjo tinklalapis. Bet tinklalapio galimybės gauti duomenis iš kitų tinklapių/duomenų yra kiek sudėtingesnės. Nors ir įmanoma, tai reikalauja išreikštinio susitarimo (per HTTP antraštes) iš nuotolinio serverio pusės. Vėlgi, dėl saugumo priežasčių.

![](limitations.svg)

Šių ribojimų nėra, jeigu JavaScript vykdomas ne naršyklėje, bet, pavyzdžiui, serveryje. Šiuolaikinės naršyklės taip pat turi papildinius ir plėtinius (ang. *plugins/extensions*), kurie gali prašyti vartotojų leidimo.
=======
    There are ways to interact with the camera/microphone and other devices, but they require a user's explicit permission. So a JavaScript-enabled page may not sneakily enable a web-camera, observe the surroundings and send the information to the [NSA](https://en.wikipedia.org/wiki/National_Security_Agency).
- Different tabs/windows generally do not know about each other. Sometimes they do, for example when one window uses JavaScript to open the other one. But even in this case, JavaScript from one page may not access the other page if they come from different sites (from a different domain, protocol or port).

    This is called the "Same Origin Policy". To work around that, *both pages* must agree for data exchange and must contain special JavaScript code that handles it. We'll cover that in the tutorial.

    This limitation is, again, for the user's safety. A page from `http://anysite.com` which a user has opened must not be able to access another browser tab with the URL `http://gmail.com`, for example, and steal information from there.
- JavaScript can easily communicate over the net to the server where the current page came from. But its ability to receive data from other sites/domains is crippled. Though possible, it requires explicit agreement (expressed in HTTP headers) from the remote side. Once again, that's a safety limitation.

![](limitations.svg)

Such limitations do not exist if JavaScript is used outside of the browser, for example on a server. Modern browsers also allow plugins/extensions which may ask for extended permissions.
>>>>>>> 6236eb8c3cdde729dab761a1d0967a88a1a6197e

## Kuo ypatinga JavaScript?

JavaScript turi bent *tris* nuostabius dalykus:
```compare
+ Pilna integracija su HTML/CSS
+ Paprastus dalykus padaryti yra nesudėtinga
+ Palaikoma visose pagrindinėse naršyklėse ir įjungta pagal numatytuosius nustatymus.
```
JavaScript yra vienintelė naršyklės technologija, kuri turi šiuos tris dalykus.

Štai kuo ypatinga JavaScript. Tai yra viena labiausiai išplitusių technologijų, kalbant apie naršyklės sąsajos (ang. *interface*) kūrimą.

<<<<<<< HEAD
Tačiau su JavaScript galima rašyti serverines, mobilias programas (ang. *applications*) ir pan.
=======
That said, JavaScript can be used to create servers, mobile applications, etc.
>>>>>>> 6236eb8c3cdde729dab761a1d0967a88a1a6197e

## Kalbos “virš” JavaScript

JavaScript sintaksė, be abejo, tinka ne visiem ir ne visada. Skirtingi žmonės nori skirtingų savybių.

Nieko nuostabaus, nes kiekvienas projektas yra skirtingas ir gali turėti labai skirtingų reikalavimų.

<<<<<<< HEAD
Dėl šių priežasčių atsirado daug kalbų, kurios yra konvertuojamos (ang. *transpiling*) į JavaScript ir tik tada vykdomos naršyklėje.
=======
So, recently a plethora of new languages appeared, which are *transpiled* (converted) to JavaScript before they run in the browser.
>>>>>>> 6236eb8c3cdde729dab761a1d0967a88a1a6197e

Modernūs įrankiai atlieka konvertaciją labai greitai, tad programuotojai gali programuoti šiomis kalbomis nesigilindami į patį konvertavimo procesą.

Tokių kalbų pavyzdžiai:

<<<<<<< HEAD
- [CoffeeScript](http://coffeescript.org/) yra “syntactic sugar” JavaScript. Trumpesnė sintaksė, su kuria galima rašyti aiškesnį ir konkretesnį kodą. Tai dažniausiai patinka Ruby programuotojams.
- [TypeScript](http://www.typescriptlang.org/) pagrindinis tikslas yra įvesti statinį tipizavimą. Tai palengvina sudėtingų sistemų programavimą. Sukurtas Microsoft.
- [Flow](http://flow.org/) taip pat turi statinį tipizavimą, bet kiek kitokiu būdu. Sukurtas Facebook.
- [Dart](https://www.dartlang.org/) yra atskira kalba, kuri turi savo paties variklį, kuris veikia ne naršyklėse (pvz. mobiliose aplikacijose), bet taip pat gali būti transpiliuotas į Javascriptą. Sukurtas Google.
- [Brython](https://brython.info/) yra Python transpileris į JavaScript, leidžiantis rašyti programas grynuoju Python be JavaScript.
- [Kotlin](https://kotlinlang.org/docs/reference/js-overview.html) yra moderni, glausta ir saugi programavimo kalba, kuri gali būti skirta naršyklei arba Node

Yra ir daugiau pavyzdžių. Tačiau, netgi jeigu mes naudojame kažkurią iš transpiliuojamų kalbų, suprasti JavaScript yra ne mažiau svarbu.
=======
- [CoffeeScript](https://coffeescript.org/) is "syntactic sugar" for JavaScript. It introduces shorter syntax, allowing us to write clearer and more precise code. Usually, Ruby devs like it.
- [TypeScript](https://www.typescriptlang.org/) is concentrated on adding "strict data typing" to simplify the development and support of complex systems. It is developed by Microsoft.
- [Flow](https://flow.org/) also adds data typing, but in a different way. Developed by Facebook.
- [Dart](https://www.dartlang.org/) is a standalone language that has its own engine that runs in non-browser environments (like mobile apps), but also can be transpiled to JavaScript. Developed by Google.
- [Brython](https://brython.info/) is a Python transpiler to JavaScript that enables the writing of applications in pure Python without JavaScript.
- [Kotlin](https://kotlinlang.org/docs/reference/js-overview.html) is a modern, concise and safe programming language that can target the browser or Node.

There are more. Of course, even if we use one of these transpiled languages, we should also know JavaScript to really understand what we're doing.
>>>>>>> 6236eb8c3cdde729dab761a1d0967a88a1a6197e

## Santrauka

- JavaScript iš pat pradžių buvo sukurtas kaip kalba, veikianti tik naršyklėje, bet dabar turi ir daugiau aplinkų, kuriose gali būti vykdoma.
- Šią dieną JavaScript yra unikali tuo, kad tai labiausiai paplitusi kalba naršyklei, turinti pilną integraciją su HTML/CSS.
- Yra daug kalbų, kurios gali būti konvertuojamos į JavaScript ir turi papildomų funkcijų. Rekomenduojame į jas bent jau trumpai pažvelgti po to, kaip išmoksite JavaScript.
