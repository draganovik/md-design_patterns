## 💾 Memento

- **<span style="color:#A3C2F2">Tip obrasca:</span>**
  Ponašajni obrazac #obrazac-ponasanja

- **<span style="color:#F7C59F">Namena:</span>**
  Čuvanje i kasnije obnavljanje prethodnog stanja objekta bez narušavanja enkapsulacije.

- **<span style="color:#E8B5D0">Motivacija:</span>**
  Undo/redo zahteva da se prethodno stanje vrati, ali bez izlaganja privatnih polja. `Originator` kreira `Memento` koji kapsulira stanje; `Caretaker` ga skladišti bez uvida. Povratkom `Memento`-a originator se vraća na staru konfiguraciju.

- **<span style="color:#B8E0D2">Primena:</span>**
  - Editor undo stack
  - Checkpoint sistema (igre, transakcije)
  - Rollback u konfiguracionim sistemima
  - Transakcioni snapshot pre rizičnih operacija

- **<span style="color:#FFF4B2">Struktura:</span>**
  - `Originator`
  - `Memento` (može imati vidljivi i skriveni deo)
  - `Caretaker`

- **<span style="color:#D8C4F2">Učesnici:</span>**
  - **Originator:** kreira i restaurira stanje
  - **Memento:** pasivan snimak
  - **Caretaker:** upravlja kolekcijom mementa

- **<span style="color:#CCE2CB">Tok operacije:</span>**
  1. `Originator` kreira novi `Memento`.
  2. `Caretaker` skladišti ga (stack/lista).
  3. Na undo – `Caretaker` daje poslednji `Memento`.
  4. `Originator` restaurira stanje.

- **<span style="color:#F6C6C7">Posledice:</span>**
  - ✅ Očuvana enkapsulacija
  - ✅ Jednostavno dodavanje undo
  - ✅ Separation of concerns (čuvanje izmešteno)
  - ❌ Memorijska potrošnja kod velikih mementa
  - ❌ Kompleksnost upravljanja velikim historijatom

- **<span style="color:#D4A5FF">Varijante:</span>**
  - Potpuni vs Diferencijalni snapshot (čuva samo razlike)
  - Ograničeni history (max N) vs Neograničen
  - Kompresovani mementi (serijalizacija)
  - Mementi sa verzionisanjem

- **<span style="color:#D4A5FF">Memento vs Command vs Prototype:</span>**
  - Memento čuva stanje; Command čuva akciju za undo; Prototype kopira objekat (alternativa snapshotu).
  - Memento idealan kada stanje kompleksno i encapsulated.

- **<span style="color:#D4A5FF">Primeri korišćenja:</span>**
  - Tekst editor undo
  - Igra (save game)
  - Transakcioni sistemi (rollback)
  - Konfiguracioni menadžeri

---

**Povezani obrasci:** [Command](./3-command.md) | [Prototype](./7-prototype.md) | [State](./17-state.md)

**Prethodni:** [Decorator](./14-decorator.md) | **Sledeći:** [Facade](./16-facade.md) | **[Nazad na početak](./README.md)**