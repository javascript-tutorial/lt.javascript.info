# Programuotojo konsolė

Kodėl lengva palikti klaidų. Ko gero, tau teks sukelti klaidų... Juokauju, tau *tikrai* teks sukelti klaidų, nebent esi [robotas](https://en.wikipedia.org/wiki/Bender_(Futurama)).

Tačiau naršyklėje, vartotojai nemato klaidų. Todėl jeigu skripte kažkas veikia ne taip, kaip turėtų, mes to nepamatysime ir negalėsime pataisyt.

Tam, kad rastume klaidas ir gautume daug kitos naudingos informacijos apie skriptus, naudojame programuotojų įrankius (ang. "developer tools") integruotus pačiose naršyklėse.

Dauguma programuotojų naudojasi Chrome arba Firefox, nes šios naršyklės turi geriausius įrankius. Kitos naršklės taip pat turi programuotojų įrankius, kartais su įdomiomis savybėmis, tačiau jie dažniausiai tik bando "pasivyti" Chrome arba Firefox. Todėl dauguma programuotojų turi "mėgstamiausią" naršyklę ir naudoja kitą, tik tada kai problema yra specifinė kažkokiai konkrečiai naršyklei.

Programuotojų įrankiai turi daug savybių. Pradžiai, mes išmoksime juos atidaryti, pažvelgti į klaidas ir paleisti JavaScript komandas.

## Google Chrome

Atidaryk puslapį [bug.html](bug.html).

Šio puslapio JavaScript kode yra klaida. Ji paslėpta nuo paprastų lankytojų. Atidarykime programuotojų įrankius.

Spausk `key:F12` arba, jeigu naudoji Mac, `key:Cmd+Opt+I`.

Programuotojų įrankiai standartiškai atidarys konsolės langą.

Turėtų atrodyt panašiai į tai:

![chrome](chrome.png)

Konkretus vaizdas priklauso nuo Chrome versijos, kurią naudoji. Kartais atsiranda pakeitimų, bet visgi vaizdas turėtų būti panašus.

- Čia mes galim pamatyti raudoną klaidos žinutę. Šiuo atveju skriptas turi nežinomą "lalala" komandą.
- Dešinėje yra aktyvi nuoroda į `bug.html:12` su skaičiumi eilutės, kurioje yra klaida.

<<<<<<< HEAD
Žemiau klaidos žinutės yra mėlynas `>` simbolis. Jis parodo komandų eilutę (ang. "command line"), kurioje mes galime rašyti JavaScript komandas. Spausk `key:Enter` kad jas paleisti (`key:Shift+Enter` kad rašyti komandas per daugiau nei vieną eilutę).
=======
Below the error message, there is a blue `>` symbol. It marks a "command line" where we can type JavaScript commands. Press `key:Enter` to run them.
>>>>>>> 193319c963b9ba86ac7d9590f7261a36ecdcc4d2

Dabar mes galime matyti klaidas. Pradžiai, to pakanka. Vėliau mes grįšime į programuotojų įrankius ir kalbėsime apie klaidų taisymą skyriuje <info:debugging-chrome>.

```smart header="Multi-line input"
Usually, when we put a line of code into the console, and then press `key:Enter`, it executes.

To insert multiple lines, press `key:Shift+Enter`. This way one can enter long fragments of JavaScript code.
```

## Firefox, Edge ir kiti

Dauguma kitų naršyklių naudoja `key:F12` programuotojo įrankių atidarymui.

Jų išvaizda gana panaši. Kai išmoksti vieną (gali pradėti nuo Chrome), gali greitai pradėti naudotis kitais.

## Safari

Safari (Mac naršyklė, neveikia Windows/Linux) yra šiek tiek unikali. Iš pradžių mums reikia įgalinti "Programuotojo Meniu" (ang. "Developer menu").

Atidaryk Nuostatas (ang. "Preferences") ir eik į "Pažangi" (ang. "Advanced"). Apačioj bus langelis (ang. "checkbox"):

![safari](safari.png)

Dabar `key:Cmd+Opt+C` įjungs konsolę. Taip pat turėk omeny, kad naujas pasirinkimas "Programuoti" (ang. "Develop") atsirado viršutiniame meniu. Jame yra daug komandų ir nustatymų.

<<<<<<< HEAD
```smart header="Kelių eilučių komandos"
Dažniausiai, jeigu konsolėje parašome vieną eilutę kodo ir paspaudžiame `key:Enter`, ji suveikia.

Tam, kad parašyti kelias eilutes, spausk `key:Shift+Enter`. Tokiu būdu mes galime parašyti ilgesnius fragmentus JavaScript kodo.
```

## Reziumė
=======
## Summary
>>>>>>> 193319c963b9ba86ac7d9590f7261a36ecdcc4d2

- Programuotojo įrankiai leidžia mums pamatyti klaidas, paleisti komandas, analizuoti kintamuosiuos ir daugiau.
- Juos paleisti galime su `key:F12` dauguma naršklių per Windows. Chrome, jeigu naudojame Mac, reikalauja `key:Cmd+Opt+J`, Safari: `key:Cmd+Opt+C` (iš pradžių reikia aktyvuoti).

Dabar jau turime paruoštą aplinką. Kitoj pamokoj paragausime JavaScript.
