Užduotis parodo kaip priešdėlinė/podėlinė formos gali atvesti prie skirtingų rezultatų kai naudojamos palyginimui.

1. **Nuo 1 iki 4**

    ```js run
    let i = 0;
    while (++i < 5) alert( i );
    ```

    Pirmoji vertė yra `i = 1`, nes `++i`  pirma padidina `i` ir tada sugrąžina naują vertę. Tad pirmasis palyginimas yra `1 < 5` ir `alert` parodo `1`.

    Tada seka `2, 3, 4…` -- vertės pasirodo viena po kitos. Palyginimui visada naudojama jau padidinta vertė, nes `++` yra prieš kintamąjį.

    Galų gale, `i = 4` yra padidinamas iki `5`, tad palyginimas `while(5 < 5)` yra netiesa ir ciklas sustoja. Tad `5` nėra parodomas.
2. **Nuo 1 iki 5**

    ```js run
    let i = 0;
    while (i++ < 5) alert( i );
    ```

    Pirmoji vertė vėlgi yra `i = 1`. Podėlinė `i++` forma padidina `i` ir tada sugrąžina *senąją* vertę, tad palyginimas `i++ < 5` naudos `i = 0` (priešingai nei `++i < 5`).

    Bet šaukimas `alert` yra atskiras, Tai yra kitas teiginys, kuris yra įvykdomas po padidinimo ir palyginimo. Tad jis gauna esamą `i = 1`.

    Toliau seka `2, 3, 4…`

    Sustokime prie `i = 4`. Priešdėlinė forma `++i` padidintų jį ir naudotų `5` palyginime. Bet čia mes turime podėlinę formą `i++`. Tad ji padidina `i` iki `5`, bet grąžina senąją vertę. Dėl to palyginimas yra iš tikrųjų `while(4 < 5)` -- tiesa, ir controlė pereina prie `alert`.

    Vertė `i = 5` yra paskutinė, nes sekančiame žingsnyje `while(5 < 5)` būtų netiesa.
