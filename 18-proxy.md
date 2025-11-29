## 🎭 Proxy

- **<span style="color:#A3C2F2">Tip obrasca:</span>**
  Strukturalni obrazac #obrazac-strukture

- **<span style="color:#F7C59F">Namena:</span>**
  Zamenski objekat koji kontroliše pristup pravom subjektu – dodaje odlaganje, zaštitu, mrežnu transparentnost ili dodatne akcije.

- **<span style="color:#E8B5D0">Motivacija:</span>**
  Učitaj sliku tek kada je potrebno (virtual); proveri dozvole pre delegiranja (protection); komunikacija sa udaljenim objektom kroz isti interfejs (remote). Proxy čuva isti interfejs, ali ubacuje kontrolni sloj.

- **<span style="color:#B8E0D2">Primena:</span>**
  - Lazy loading resursa
  - Access kontrola
  - Inter-proces / mrežna komunikacija
  - Keširanje rezultata skupih poziva
  - Logging / metrike oko poziva

- **<span style="color:#FFF4B2">Struktura:</span>**
  - `Subject`
  - `RealSubject`
  - `Proxy` (drži referencu)

- **<span style="color:#D8C4F2">Učesnici:</span>**
  - **Proxy:** kontrolni sloj
  - **RealSubject:** originalna logika
  - **Client:** koristi `Subject` interfejs

- **<span style="color:#CCE2CB">Tok operacije:</span>**
  1. Klijent poziva operaciju na Proxy.
  2. Proxy validira / kešira / odlaže.
  3. Kreira ili koristi `RealSubject` i delegira poziv.

- **<span style="color:#F6C6C7">Posledice:</span>**
  - ✅ Transparentna kontrola pristupa
  - ✅ Odložena inicijalizacija
  - ✅ Dodavanje nefunkcionalnih aspekata (log, metrics)
  - ❌ Složenost i potencijalni skriveni troškovi
  - ❌ Mogući problemi sa identitetom (proxy != realni objekt po referenci)

- **<span style="color:#D4A5FF">Varijante:</span>**
  - Virtual
  - Protection
  - Remote (RMI, gRPC stub)
  - Smart reference (ref counting)
  - Caching proxy
  - Monitoring / Audit proxy

- **<span style="color:#D4A5FF">Proxy vs Decorator vs Adapter:</span>**
  - Proxy fokus na kontroli pristupa i lifecycle-u; Decorator dodaje funkcionalnost; Adapter menja interfejs.
  - Proxy često menja semantiku inicijalizacije ili lokacije.

- **<span style="color:#D4A5FF">Primeri korišćenja:</span>**
  - ORM lazy loading
  - API rate limiter
  - Remote stub klase
  - Keširanje rezultata (memoization sloj)

---

**Povezani obrasci:** [Decorator](./14-decorator.md) | [Adapter](./4-adapter.md) | [Facade](./16-facade.md)

**Prethodni:** [State](./17-state.md) | **Sledeći:** [Visitor](./19-visitor.md) | **[Nazad na početak](./README.md)**