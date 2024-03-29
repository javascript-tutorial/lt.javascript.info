# Labas, pasauli!

Šioje pamokoje perskaitysite apie JavaScript esmę ir apie pačią kalbą.

Tam reikia darbinės aplinkos, kad galėtume paleisti skriptus (script - nurodymai kompiuteriui teksto pavidalu), kadangi ši knyga yra interaktyvi, naršyklė puikiai atitiks mūsų poreikius. Pasistengsime naršyklės komandas (tokias kaip `alert`) naudoti kaip galima rečiau, kad jums nereikėtų su jomis praleisti per daug laiko, ypač jeigu planuojate susikaupti ties kitokia darbine aplinka (pavyzdžiui Node.js). Skirsime daugiau dėmesio JavaScript naršyklėje [kitoje dalyje](/ui) šių pamokų.

Tad visų pirma pabandykime pridėti skriptą prie internetinio puslapio. Aplinkos serveryje (kaip pavyzdžiui Node.js) galite vykdyti skriptą su komanda `"node my.js"`.


## Žyma "script"

JavaScript programa gali būti pridėta prie bet kurios HTML dokumento dalies su `<script>` žymos pagalba.

Pavyzdžiui:

```html run height=100
<!DOCTYPE HTML>
<html>

<body>

  <p>Prieš skriptą...</p>

*!*
  <script>
    alert( 'Labas, pasauli!' );
  </script>
*/!*

  <p>...Po skripto.</p>

</body>

</html>
```

```online
Galite paleisti pavyzdį paspausdami mygtuką “Paleisti” dešiniame virštutiniame pavyzdžio lango kampe.
```

Žymoje `<script>` yra JavaScript kodas, kuris automatiškai įvykdomas kai naršyklė apdoroja žymą.


## Modernus žymėjimas

Žyma `<script>` turi kelis atributus, kurie šiais laikais jau retai naudojami, bet juos dar galite rasti senuose koduose:

Atributas `type`: <code>&lt;script <u>type</u>=...&gt;</code>
: Senas HTML standartas, HTML4, reikalavo, kad skriptas turėtų `type`(tipą). Dažniausiai tau būdavo `type="text/javascript"`. Dabar tai nėra reikalaujama. Dar daugiau, modernus HTML standartas visiškai pakeitė šio atributo reikšmę. Dabar jis gali būti naudojamas JavaScript moduliuose. Bet tai jau pažengusio lygio tema; apie modulius kalbėsime kitoje šių pamokų dalyje.

Atributas `language`: <code>&lt;script <u>language</u>=...&gt;</code>
: Šis atributas turėjo nurodyti skripto kalbą, bet daugiau nebeturi prasmės, nes JavaScript ir yra numatytoji kalba. Nėra reikalo šio atributo naudoti.

Komentarai prieš ir po skriptų.
: Labai senose knygose ir vadovėliuose galime rasti komentarus `<script>` žymose, kaip pavyzdžiui:

    ```html no-beautify
    <script type="text/javascript"><!--
        ...
    //--></script>
    ```

    Ši ypatybė nebenaudojama modernioje JavaScript. Tokie komentarai paslepia JavaScript kodą nuo senų naršyklių, kurios nežinojo kaip įvykdyti `<script>` žymą. Per paskutinius 15 metų išleistos naršyklės nebeturi šios problemos, bet toks komentaras gali jums padėti atpažinti labai senus kodus.


## Išorinis skriptas

Jeigu mūsų JavaScript kodas labai ilgas, galime jį perkelti į atskirą failą.

Skriptų failai yra sujungiami su HTML `src` (šaltinio) atributo pagalba:

```html
<script src="/path/to/script.js"></script>
```

Čia `/path/to/script.js` yra absoliutus kelias iki skripto iš svetainės šaknies. Taip pat galima nurodyti reliatyvų kelią nuo dabartinio puslapio. Pavyzdžiui, `src="script.js"`, kaip ir `src="./script.js"`, reikštų failą `"script.js"` dabartiniame aplanke.

Taip pat galime pateikti pilną adresą (URL). Pavyzdžiui:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/lodash.js/4.17.11/lodash.js"></script>
```

Kad pridėtume kelis skriptus, naudojame kiekvienam atskiras žymas:

```html
<script src="/js/script1.js"></script>
<script src="/js/script2.js"></script>
…
```

```smart
Kaip taisyklė, tik paprasčiausi skriptai yra rašomi į patį HTML failą. Sudėtingesni, daugiau vietos užimantys skriptai būna atskiruose failuose.

Tokio atskiro failo nauda yra tokia, kad naršyklė failą parsisiųs ir laikys savo tam skirtoje talpykloje [cache](https://en.wikipedia.org/wiki/Web_cache).

Kiti puslapiai, kurie bus nukreipti į tą patį skriptą, paims informaciją iš talpyklos (cache) vietoje to, kad dar kartą jį parsisiųstų, tokiu būdu failas parsiunčiąmas tik vieną kartą.

Taip sumažinamas duomenų apsikeitimas (traffic) ir paspartinamas puslapių paleidimo greitis.
```

````warn header="Jeigu šaltinis `src` yra nustatytas, skripto turinys yra ignoruojamas."
Ta pati `<script>` žyma negali turėti ir `src` atributo ir kodo viduje.

Tai nesuveiktų:

```html
<script *!*src*/!*="file.js">
  alert(1); // šis turinys ignoruojamas, nes nustatytas src (išorinis šaltinis)
</script>
```

Turime pasirinkti arba išorinį `<script src="…">` arba vidinį skriptą `<script>` su kodu tarp žymų.

Pavyzdys viršuje gali būti atskirtas į du skriptus, kad suveiktų:

```html
<script src="file.js"></script>
<script>
  alert(1);
</script>
```
````

## Santrauka

- Naudojame žymą `<script>`, kad pridėtume JavaScript kodą prie puslapio.
- Atributai `type` ir `language` nėra privalomi.
- Skriptas išoriniame faile gali būti pidėtas su `<script src="path/to/script.js"></script>` pagalba.


Tai tik pradžia ir yra dar daug informacijos, kurią reikia išmokti apie naršyklės skriptus ir jų bendravimą su tinklapiu. Šios pamokos dalis yra skirta JavaScript kalbai, tad neturėtume blaškyti savęs su naršyklei būdingu šios kalbos atlikimu. Naršyklę naudosime kaip būdą paleisti JavaScript, o tai yra labai patogu skaitant internetinę knygą, bet tai tik vienas būdas iš daugelio.
