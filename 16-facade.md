# 🧱 Facade

- **<span style="color:#A3C2F2">Tip obrasca:</span>**
  Strukturalni obrazac #obrazac-strukture

- **<span style="color:#F7C59F">Namena:</span>**
  Pruža jednostavan, ujedinjen interfejs ka kompleksnom podsistemu; smanjuje spregu između klijenta i internih klasa.

- **<span style="color:#E8B5D0">Motivacija:</span>**
  Podsistem kompajlera ima `Scanner`, `Parser`, `CodeGenerator`, `Optimizer`. Umesto da klijent orkestrira njih, pozove `CompilerFacade.compile(source)` i dobije rezultat. Pojednostavljenje podiže čitljivost i stabilnost.

- **<span style="color:#B8E0D2">Primena:</span>**
  - Kompleksni API postaje preopširan za klijenta
  - Stabilan spoljašnji interfejs + promenljiv unutrašnji kod
  - Izolacija podsistema radi testiranja
  - Enkapsulacija legacy podsistema
  - Bezbednosno ograničavanje pristupa naprednim funkcijama

- **<span style="color:#FFF4B2">Struktura:</span>**
  - `Facade` (koordinator)
  - `SubsystemClassA/B/...`
  - `Client`

- **<span style="color:#D8C4F2">Učesnici:</span>**
  - **Facade:** delegira koordinaciju
  - **Subsystem classes:** implementacije
  - **Client:** koristi samo facade

- **<span style="color:#CCE2CB">Tok operacije:</span>**
  1. Klijent poziva metodu Facade-a.
  2. Facade orkestrira pozive ka podsistemu.
  3. Vraća zbirni rezultat.

- **<span style="color:#F6C6C7">Posledice:</span>**
  - ✅ Smanjena kompleksnost za klijenta
  - ✅ Labava sprega
  - ✅ Jednostavnije testiranje klijenta
  - ✅ Zaštita unutrašnjih detalja
  - ❌ Rizik od prevelike centralizacije
  - ❌ Može sakriti napredne mogućnosti

- **<span style="color:#D4A5FF">Varijante:</span>**
  - Više fasada za različite kontekste (AdminFacade vs UserFacade)
  - Layered facade (fasada iznad fasade)
  - Mikrofasade (male fokusirane jedinice)

- **<span style="color:#D4A5FF">Facade vs Mediator vs Adapter:</span>**
  - Facade pojednostavljuje; Mediator koordinira među objektima; Adapter menja interfejs.
  - Facade ne uvodi nove interakcije – samo agregira postojeće.

- **<span style="color:#D4A5FF">Primeri korišćenja:</span>**
  - Web API gateway
  - SDK wrapper preko složenog REST/GraphQL skupa
  - Kompajler front-end
  - Orkestracija cloud servisa

---

**Povezani obrasci:** [Adapter](./4-adapter.md) | [Mediator](./6-observer.md) | [Proxy](./18-proxy.md)

**Prethodni:** [Memento](./15-memento.md) | **Sledeći:** [State](./17-state.md) | **[Nazad na početak](./README.md)**