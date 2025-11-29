# 🏗️ Builder

- **<span style="color:#A3C2F2">Tip obrasca:</span>**
  Kreacioni obrazac #obrazac-kreiranja

- **<span style="color:#F7C59F">Namena:</span>**
  Razdvaja konstrukciju kompleksnog objekta od njegove reprezentacije, tako da isti proces građenja može kreirati različite reprezentacije.

- **<span style="color:#E8B5D0">Motivacija:</span>**
  Klasa `RTFReader` mora moći da parsira RTF dokument i konvertuje ga u različite formate (ASCII, TeX, Widget). Umesto da `RTFReader` zna kako da pravi svaki format (što bi dovelo do složenog i nefleksibilnog koda), koristi objekat `TextConverter` (builder), koji gradi rezultat dok `RTFReader` prolazi kroz dokument. Na taj način je lako dodati nove reprezentacije — jednostavno se dodaje novi ConcreteBuilder bez menjanja RTFReader klase.

- **<span style="color:#B8E0D2">Primena:</span>**
  - Kada se konstrukcija kompleksnog objekta mora odvijati nezavisno od njegove strukture i komponenti
  - Kada treba kreirati više različitih verzija istog objekta
  - Kada se objekat gradi postepeno i ima varijacije u konfiguraciji
  - Kada konstruktor ima previše parametara (Telescoping Constructor Problem)
  - Kada je potrebna fina kontrola nad procesom konstrukcije

- **<span style="color:#FFF4B2">Struktura:</span>**
  - **Builder:** Apstraktni interfejs za kreiranje delova
  - **ConcreteBuilder:** Konkretna implementacija građenja (npr. `TextWidgetConverter`)
  - **Director:** Kontroliše redosled građenja (`RTFReader`)
  - **Product:** Rezultujući kompleksan objekat (npr. `TeXText`, `ASCIIText`)

- **<span style="color:#D8C4F2">Učesnici:</span>**
  - **Builder:** Definiše metode za građenje delova (`buildPart()`, `getResult()`)
  - **ConcreteBuilder:** Sklapa delove u celinu, drži referencu na Product
  - **Director:** Upravlja procesom građenja, poziva Builder metode u odgovarajućem redosledu
  - **Product:** Gotov objekat koji se dobija kao rezultat

- **<span style="color:#CCE2CB">Tok operacije:</span>**
  1. Klijent instancira `ConcreteBuilder`
  2. Prosleđuje ga `Director`-u (ili direktno poziva metode)
  3. `Director` poziva builder metode u tačnom redosledu
  4. `ConcreteBuilder` postepeno gradi i vraća `Product` kroz `getResult()`

- **<span style="color:#F6C6C7">Posledice:</span>**
  - ✅ **Promena unutrašnje strukture:** Bez promene građenja
  - ✅ **Povećana modularnost:** Jasna separacija konstrukcije i reprezentacije
  - ✅ **Fina kontrola:** Nad redosledom i načinom građenja
  - ✅ **Čitljivost:** Posebno sa Fluent Builder interfejsom
  - ✅ **Testiranje:** Lakše testiranje Builder-a odvojeno od Director-a
  - ❌ **Više koda:** Potrebno je kreirati Builder klasu
  - ❌ **Kompleksnost:** Može biti previše za jednostavne objekte

- **<span style="color:#D4A5FF">Varijante Builder-a:</span>**
  **1. Klasični Builder (Gang of Four):**
  - Ima Director klasu koja kontroliše proces
  - Builder je interfejs, ConcreteBuilder implementira

  **2. Fluent Builder (Method Chaining):**
  - Builder metode vraćaju `this` (omogućava `builder.setX().setY().build()`)
  - Često nema Director, klijent direktno poziva metode
  - Popularan u modernim jezicima (Lombok, Kotlin)

  **3. Telescoping Constructor Replacement:**
  - Rešava problem konstruktora sa previše parametara
  - Builder je static nested class

  **4. Step Builder:**
  - Interfejsi obrađuju redosled poziva
  - Compile-time provera obaveznih polja

- **<span style="color:#D4A5FF">Builder vs Factory:</span>**
  - **Builder:** Fokus na postupnoj konstrukciji, različite reprezentacije
  - **Factory:** Fokus na kreiranje cele instance u jednom koraku
  - Builder je pogodan za složene objekte sa više konfiguracija

- **<span style="color:#D4A5FF">Primeri korišćenja:</span>**
  - **StringBuilder/StringBuffer:** Građenje stringova
  - **SQL Query builders:** Konstruisanje SQL upita
  - **HTTP Request builders:** Građenje HTTP zahteva
  - **Document builders:** HTML, XML, PDF generatori
  - **Configuration objects:** Kompleksni objekti sa mnogo opcija

---

**Povezani obrasci:** [Abstract Factory](./10-abstract-factory.md) | [Composite](./5-composite.md) | [Singleton](./2-singleton.md)

**Prethodni:** [Strategy](./8-strategy.md) | **Sledeći:** [Abstract Factory](./10-abstract-factory.md) | **[Nazad na početak](./README.md)**