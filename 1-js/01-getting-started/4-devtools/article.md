# Programuotojo konsolė

Kodas yra linkęs į klaidas. Labai tikėtina, kad padarysite klaidų... O apie ką aš kalbu? *Visiškai* tikėtina, kad padarysite klaidų, bent jau jei esate žmogus, o ne [robotas](https://en.wikipedia.org/wiki/Bender_(Futurama)).

Tačiau naršyklėje, vartotojai nemato klaidų. Todėl jeigu skripte kažkas veikia ne taip, kaip turėtų, mes to nepamatysime ir negalėsime pataisyt.

Tam, kad rastume klaidas ir gautume daug kitos naudingos informacijos apie skriptus, naudojame programuotojų įrankius (ang. *"developer tools"*) integruotus pačiose naršyklėse.

Dauguma programuotojų naudojasi Chrome arba Firefox, nes šios naršyklės turi geriausius įrankius. Kitos naršklės taip pat turi programuotojų įrankius, kartais su įdomiomis savybėmis, tačiau jie dažniausiai tik bando “pasivyti” Chrome arba Firefox. Todėl dauguma programuotojų turi “mėgstamiausią” naršyklę ir naudoja kitą, tik tada kai problema yra specifinė kažkokiai konkrečiai naršyklei.

Programuotojų įrankiai turi daug savybių. Pradžiai, mes išmoksime juos atidaryti, pažvelgti į klaidas ir paleisti JavaScript komandas.

## Google Chrome

Atidarykite puslapį [bug.html](bug.html).

Šio puslapio JavaScript kode yra klaida. Ji paslėpta nuo paprastų lankytojų. Atidarykime programuotojų įrankius.

Spauskite `key:F12` arba, jeigu naudojate Mac, `key:Cmd+Opt+I`.

Programuotojų įrankiai standartiškai atidarys konsolės langą.

Turėtų atrodyt panašiai į tai:

![chrome](chrome.png)

Konkretus vaizdas priklauso nuo Chrome versijos, kurią naudojate. Kartais atsiranda pakeitimų, bet visgi vaizdas turėtų būti panašus.

- Čia mes galim pamatyti raudoną klaidos žinutę. Šiuo atveju skriptas turi nežinomą "lalala" komandą.
- Dešinėje yra aktyvi nuoroda į `bug.html:12` su skaičiumi eilutės, kurioje yra klaida.

Žemiau klaidos žinutės yra mėlynas `>` simbolis. Jis parodo komandų eilutę (ang. *“command line”*), kurioje mes galime rašyti JavaScript komandas. Spauskite `key:Enter` kad jas paleisti.

Dabar mes galime matyti klaidas. Pradžiai, to pakanka. Vėliau mes grįšime į programuotojų įrankius ir kalbėsime apie klaidų taisymą skyriuje <info:debugging-chrome>.

```smart header="Kelių eilučių įvedimas"
Paprastai, kai mes įrašome kodo eilutę į konsolę ir paspaudžiame `key:Enter`, ji įvykdoma.

Norėdami įvesti kelias eilutes, paspauskite `key:Shift+Enter`. Taip galima įvesti ilgus JavaScript kodo fragmentus.
```

## Firefox, Edge ir kiti

Dauguma kitų naršyklių naudoja `key:F12` programuotojo įrankių atidarymui.

Jų išvaizda gana panaši. Kai išmoksti vieną (gali pradėti nuo Chrome), gali greitai pradėti naudotis kitais.

## Safari

Safari (Mac naršyklė, neveikia Windows/Linux) yra šiek tiek unikali. Iš pradžių mums reikia įjungti “Programuotojo Meniu” (ang. *“developer menu”*).

Atidarykite Nuostatas (ang. “*preferences*”) ir eikite į "Pažangi" (ang. “advanced”). Apačioj bus langelis (ang. *“checkbox”*):

![safari](safari.png)

Dabar `key:Cmd+Opt+C` įjungs konsolę. Taip pat turėkite omeny, kad naujas pasirinkimas “Programuoti” (ang. *"develop"*) atsirado viršutiniame meniu. Jame yra daug komandų ir nustatymų.

## Santrauka

- Programuotojo įrankiai leidžia mums pamatyti klaidas, paleisti komandas, analizuoti kintamuosiuos ir daugiau.
- Juos paleisti galime su `key:F12` dauguma naršklių per Windows. Chrome, jeigu naudojame Mac, reikalauja `key:Cmd+Opt+J`, Safari: `key:Cmd+Opt+C` (iš pradžių reikia aktyvuoti).

Dabar turime paruoštą aplinką. Kitame skyriuje pereisime prie JavaScript.
