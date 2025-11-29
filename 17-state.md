# 🚦 State

- **<span style="color:#A3C2F2">Tip obrasca:</span>**
  Ponašajni obrazac #obrazac-ponasanja

- **<span style="color:#F7C59F">Namena:</span>**
  Dinamička promena ponašanja objekta u zavisnosti od internog stanja – objekt se spolja ponaša kao da mu se menja klasa.

- **<span style="color:#E8B5D0">Motivacija:</span>**
  `TCPConnection` menja reakcije metoda u zavisnosti od stanja (`Closed`, `Listen`, `Established`). Umesto `switch` masiva, stanje postaje objekat sa svojim implementacijama – podela odgovornosti i jasnoća tranzicija.

- **<span style="color:#B8E0D2">Primena:</span>**
  - Kompleksne mašine stanja (protokoli, UI wizard)
  - Eliminacija uslovnih grana
  - Ponašanje koje evoluira kroz faze ciklusa
  - Logika tranzicija koja treba biti enkapsulirana

- **<span style="color:#FFF4B2">Struktura:</span>**
  - `Context`
  - `State` (interfejs)
  - `ConcreteStateA/B/...`

- **<span style="color:#D8C4F2">Učesnici:</span>**
  - **Context:** održava trenutno stanje
  - **State:** definicija operacija
  - **ConcreteState:** implementacija i eventualna tranzicija

- **<span style="color:#CCE2CB">Tok operacije:</span>**
  1. Klijent poziva metod na `Context`.
  2. `Context` delegira na aktivno stanje.
  3. Stanje može promeniti `Context` postavljanjem novog stanja.

- **<span style="color:#F6C6C7">Posledice:</span>**
  - ✅ Eliminacija `switch/if` kompleksnosti
  - ✅ Lako dodavanje novih stanja
  - ✅ Lokalizacija odgovornosti
  - ✅ Poboljšana testabilnost po stanju
  - ❌ Veći broj klasa
  - ❌ Tranzicije mogu postati netransparentne ako su rasute

- **<span style="color:#D4A5FF">Varijante:</span>**
  - Table-driven (matrica tranzicija)
  - State objects kao singletons (deljenje)
  - Hierarchical state (superstanja)
  - Transition Strategy (odvojena logika tranzicija)

- **<span style="color:#D4A5FF">State vs Strategy vs Memento:</span>**
  - State: promena ponašanja kroz stanja. Strategy: izbor algoritma, nema istorije. Memento: vraćanje prethodnog stanja.
  - State integrisan sa tranzicijama; Strategy pasivan kao plug-in.

- **<span style="color:#D4A5FF">Primeri korišćenja:</span>**
  - UI komponenta (enabled/disabled/loading)
  - Protokol konekcije
  - Workflow engine koraci
  - Game AI (aggressive/defensive/patrol)

---

**Povezani obrasci:** [Strategy](./8-strategy.md) | [Memento](./15-memento.md) | [Observer](./6-observer.md)

**Prethodni:** [Facade](./16-facade.md) | **Sledeći:** [Proxy](./18-proxy.md) | **[Nazad na početak](./README.md)**