# 🔁 Command

- **<span style="color:#A3C2F2">Tip obrasca:</span>**
  Ponašajni (behavioral) obrazac #obrazac-ponašanja

- **<span style="color:#F7C59F">Namena:</span>**
  Omogućava enkapsulaciju zahteva kao objekta, čime se podržava parametrizacija, logovanje, poništavanje i redosled izvršavanja operacija.

- **<span style="color:#E8B5D0">Motivacija:</span>**
  Kada korisnički interfejs (npr. dugme ili meni stavka) treba da izvrši akciju, ali bez direktnog znanja o implementaciji te akcije. Zahtev se pretvara u objekat (komandu), koji se može skladištiti, proslediti ili poništiti. Na ovaj način, GUI komponente postaju potpuno nezavisne od poslovne logike.

- **<span style="color:#B8E0D2">Primena:</span>**
  - Parametrizacija objekata akcijama (npr. različita dugmad dele isti interfejs)
  - Redosledno izvršavanje i odlaganje izvršavanja komandi
  - Undo/Redo mehanizmi (`execute()` i `unexecute()`)
  - Logovanje i replikacija (npr. sistemska transakcija)
  - Izgradnja sistema sa transakcijama visokog nivoa
  - Makro komande (kompozit više komandi)

- **<span style="color:#FFF4B2">Struktura:</span>**
  - **Command:** Interfejs sa metodom `execute()` i opcionalno `unexecute()`
  - **ConcreteCommand:** Implementira `execute()` i referencira Receiver
  - **Invoker:** Poziva `execute()` bez znanja o konkretnoj komandi
  - **Receiver:** Zna kako da izvrši operaciju (pravi rad)
  - **Client:** Inicijalizuje komandu i dodeljuje joj Receiver-a

- **<span style="color:#D8C4F2">Učesnici:</span>**
  - **Command:** Definicija interfejsa (`execute()`, `unexecute()`)
  - **ConcreteCommand:** Konkretna implementacija (`PasteCommand`, `OpenCommand`)
  - **Invoker:** Poziva komandu (`MenuItem`, `Button`)
  - **Receiver:** Izvršava pravu akciju (`Document`, `Application`)
  - **Client:** Povezuje sve delove (`User`)

- **<span style="color:#CCE2CB">Tok operacije:</span>**
  1. Klijent kreira `ConcreteCommand` i postavlja `Receiver`
  2. `Invoker` čuva komandu
  3. `Invoker` poziva `execute()` (npr. na klik dugmeta)
  4. `ConcreteCommand` poziva akciju na `Receiver`-u
  5. (Opcionalno) čuva staro stanje za `unexecute()`

- **<span style="color:#F6C6C7">Posledice:</span>**
  - ✅ **Razdvajanje zahteva od izvršenja:** Invoker ne zna šta komanda radi
  - ✅ **Jednostavno dodavanje novih komandi:** bez menjanja postojećeg koda
  - ✅ **Undo/Redo mehanizmi:** čuvanjem istorije komandi
  - ✅ **Makro-komande:** Kompozicija više komandi u jednu
  - ✅ **Logovanje i oporavak:** Mogu se serijalizovati i ponovo izvršiti
  - ✅ **Fleksibilna arhitektura:** Lako se komande mogu zameniti ili proširiti
  - ❌ **Povećan broj klasa:** Svaka akcija zahteva novu klasu
  - ❌ **Indirekcija:** Dodatni sloj između zahteva i izvršenja

- **<span style="color:#D4A5FF">Primeri korišćenja:</span>**
  - **Text editori:** Copy, Paste, Cut, Undo, Redo operacije
  - **Transakcioni sistemi:** Atomske operacije sa rollback mogućnošću
  - **Task schedulers:** Odloženo izvršavanje zadataka
  - **GUI frameworki:** Event handling (dugmad, meniji, prečice)
  - **Home automation:** Programiranje sekvenci akcija

---

**Povezani obrasci:** [Composite](./5-composite.md) | [Memento](./15-memento.md) | [Prototype](./7-prototype.md)

**Prethodni:** [Singleton](./2-singleton.md) | **Sledeći:** [Adapter](./4-adapter.md) | **[Nazad na početak](./README.md)**
