importance: 3

---

# Patikrinti prisijungimą

Parašykite kodą, kuris prašo prisijungimo su `prompt`.

Jeigu lankytojas įveda `"Admin"`, tada `prompt` slaptažodžio, jeigu įvedama tuščia eilė arba paspaudžiamas `key:Esc` -- parodyti “Atšaukta”, jeigu tai kitokia eilutė -- tada parodyti “Aš jūsų nežinau”.

Slaptažodis patikrinamas sekančiais žingsniais:

- Jeigu lygus “TheMaster”, parodyti “Sveiki!”,
- Kitokia eilutė -- parodyti “Neteisingas slaptažodis”,
- Tuščiai eilutei arba jeigu buvo atšauktas, parodyti “Atšauktas”

Diagrama:

![](ifelse_task.svg)

Prašau, naudokite įdėtinius (ang. *“nested”*) `if` rinkinius. Prižiūrėkite skaitomumą viso kodo.

Patarimas: praleidžiant tuščią įvestį per prompt grąžina tuščią eilutę `''`. Paspaudžiant `key:ESC` per prompt grąžina `null`.

[demo]
