# 🧬 Singleton

- **<span style="color:#A3C2F2">Tip obrasca:</span>**
  Kreacioni obrazac #obrazac-kreiranja

- **<span style="color:#F7C59F">Namena:</span>**
  Obezbeđuje da klasa ima samo jednu instancu i omogućava globalnu pristupnu tačku toj instanci.

- **<span style="color:#E8B5D0">Motivacija:</span>**
  Potrebno je da neke komponente sistema (npr. konekcija ka bazi, upravljanje fajl sistemom, logger, konfiguracioni menadžeri) budu jedinstvene u okviru aplikacije. Više instanci bi dovelo do nekonzistentnosti stanja, konflikta resursa ili nepotrebne potrošnje memorije.

- **<span style="color:#B8E0D2">Primena:</span>**
  - Mora postojati tačno jedna instanca klase
  - Instanca mora biti globalno dostupna
  - Klijenti ne treba da brinu o tome da li je instanca već kreirana
  - Potrebna je kontrola nad inicijalizacijom (npr. lazy loading)
  - Koordinacija pristupa deljenom resursu (thread pool, cache)

- **<span style="color:#FFF4B2">Struktura:</span>**
  - **Privatni konstruktor:** sprečava direktnu instanciranje
  - **Privatna statička promenljiva:** čuva jedinstvenu instancu
  - **Javna statička metoda `getInstance()`:** vraća jedinstvenu instancu

- **<span style="color:#D8C4F2">Učesnici:</span>**
  - **Singleton:** Definiše `getInstance()` metodu za pristup instanci i kreira je prilikom prvog poziva (lazy initialization) ili pri učitavanju klase (eager initialization).

- **<span style="color:#CCE2CB">Tok operacije:</span>**
  1. Klijent poziva `Singleton.getInstance()`
  2. Ako instanca ne postoji, kreira se (lazy) ili je već kreirana (eager)
  3. Vraća se postojeća instanca
  4. Svi sledeći pozivi vraćaju istu instancu

- **<span style="color:#F6C6C7">Posledice:</span>**
  - ✅ **Kontrolisana instanca:** samo jedna instanca u celoj aplikaciji
  - ✅ **Globalni pristup:** dostupnost iz bilo kog dela koda
  - ✅ **Lazy inicijalizacija:** instanca se kreira samo kada je potrebna
  - ✅ **Fleksibilnost:** može se proširiti podklasama uz pažljiv dizajn
  - ❌ **Globalno stanje:** može otežati testiranje i dovesti do skrivenih zavisnosti
  - ❌ **Multithreading:** zahteva sinhronizaciju (double-checked locking)
  - ❌ **Serialization/Reflection:** može narušiti jedinstvost instance
  - ❌ **Classloaders:** u složenim okruženjima može doći do više instanci

- **<span style="color:#D4A5FF">Implementacione varijante:</span>**
  - **Eager initialization:** instanca se kreira pri učitavanju klase
  - **Lazy initialization:** instanca se kreira pri prvom pozivu
  - **Thread-safe lazy:** koristi sinhronizaciju ili double-checked locking
  - **Bill Pugh (inner static class):** elegantno rešenje bez sinhronizacije
  - **Enum Singleton:** najsigurnija implementacija (zaštita od refleksije i serijalizacije)

---

**Povezani obrasci:** [Abstract Factory](./10-abstract-factory.md) | [Builder](./9-builder.md) | [Prototype](./7-prototype.md)

**Prethodni:** [MVC](./1-mvc.md) | **Sledeći:** [Command](./3-command.md) | **[Nazad na početak](./README.md)**


