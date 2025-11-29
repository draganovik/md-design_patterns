## 🎄 Decorator

- **<span style="color:#A3C2F2">Tip obrasca:</span>**
  Strukturalni obrazac #obrazac-strukture

- **<span style="color:#F7C59F">Namena:</span>**
  Dinamičko dodavanje dodatnih odgovornosti objektu bez menjanja njegove klase; fleksibilna alternativa nasleđivanju.

- **<span style="color:#E8B5D0">Motivacija:</span>**
  Umesto kreiranja kombinacionih podklasa (`ScrollableBorderedTextView`), ponašanje se dodaje slojem oko objekta. Svaki dekorater održava isti interfejs kao komponenta, propušta pozive i dodaje pre/posle logiku – omogućava slaganje.

- **<span style="color:#B8E0D2">Primena:</span>**
  - Opcionalne funkcionalnosti koje treba dinamički uključiti/isključiti
  - Kombinovanje više dodatnih osobina (scroll + border + shadow)
  - Transparentna proširenja (klijent vidi samo bazni interfejs)
  - Kada je hijerarhija eksplodirala zbog mnoštva kombinacija

- **<span style="color:#FFF4B2">Struktura:</span>**
  - `Component` (interfejs)
  - `ConcreteComponent`
  - `Decorator` (apstraktni sloj, drži referencu)
  - `ConcreteDecorator` (dodaje ponašanje)

- **<span style="color:#D8C4F2">Učesnici:</span>**
  - **Component:** definicija baznih operacija
  - **ConcreteComponent:** osnovna implementacija
  - **Decorator:** skladišti komponentu
  - **ConcreteDecorator:** modifikuje rezultat/ponašanje

- **<span style="color:#CCE2CB">Tok operacije:</span>**
  1. Klijent kreira baznu komponentu.
  2. Omotava je jednim ili više dekoratera.
  3. Pozivi se propagiraju lančano do originala.
  4. Svaki sloj doprinosi dodatnu logiku.

- **<span style="color:#F6C6C7">Posledice:</span>**
  - ✅ Eliminacija eksplozije podklasa
  - ✅ Dinamičko sastavljanje ponašanja
  - ✅ Poštovanje otvoren/zatvoren principa
  - ❌ Teže debagovanje (mnogi mali objekti)
  - ❌ Nije pogodno za interfejse gde identitet tipa mora ostati tačan
  - ❌ Poređenje tipova otežano (wrappovan objekat)

- **<span style="color:#D4A5FF">Varijante:</span>**
  - Transparent vs Semitransparent dekorateri (dodaju nove metode)
  - Dinamički (runtime) vs Statički (compile-time, npr. u C++ template-ovima)
  - Stacking ograničen (maks dubina) vs Neograničen

- **<span style="color:#D4A5FF">Decorator vs Proxy vs Adapter:</span>**
  - Decorator dodaje funkcionalnost; Proxy kontroliše pristup; Adapter prilagođava interfejs.
  - Decorator i Proxy imaju isti interfejs kao komponenta, ali motivacija različita.

- **<span style="color:#D4A5FF">Primeri korišćenja:</span>**
  - Java I/O streamovi (`BufferedInputStream`, `DataInputStream`)
  - UI efekti (border, shadow, scroll)
  - Logger koji dodaje timestamp/encryption
  - Dinamičko kompresovanje ili keširanje sadržaja

---

**Povezani obrasci:** [Composite](./5-composite.md) | [Proxy](./18-proxy.md) | [Adapter](./4-adapter.md)

**Prethodni:** [Iterator](./13-iterator.md) | **Sledeći:** [Memento](./15-memento.md) | **[Nazad na početak](./README.md)**