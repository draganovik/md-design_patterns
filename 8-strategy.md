## 🧠 Strategy

- **<span style="color:#A3C2F2">Tip obrasca:</span>**
  Ponašajni (behavioral) obrazac #obrazac-ponašanja

- **<span style="color:#F7C59F">Namena:</span>**
  Definiše porodicu algoritama, enkapsulira svaki od njih i omogućava njihovu zamenu u toku rada. Algoritam se može menjati nezavisno od konteksta koji ga koristi.

- **<span style="color:#E8B5D0">Motivacija:</span>**
  Kada klasa (npr. `Composition`) koristi više varijanti algoritma (npr. različiti načini prelamanja teksta), bilo bi teško održavati sve unutar jedne klase. Koristi se veliki `if-else` ili `switch` blok, kod postaje rigidan i težak za testiranje. Strategy obrazac omogućava da se algoritmi (npr. `TeXCompositor`, `SimpleCompositor`) odvoje u posebne klase koje se mogu lako zameniti, testirati nezavisno i dodavati bez menjanja `Composition` klase.

- **<span style="color:#B8E0D2">Primena:</span>**
  - Kada postoji više varijanti istog ponašanja ili algoritma
  - Kada se želi izbeći ugradnja algoritma direktno u klasu
  - Kada se algoritmi međusobno razlikuju po vremensko-prostornim zahtevima
  - Kada klijent ne treba da zna detalje implementacije algoritma
  - Zamena za više uslovnih iskaza koji biraju ponašanje

- **<span style="color:#FFF4B2">Struktura:</span>**
  - **Strategy:** Interfejs (npr. `Compositor`)
  - **ConcreteStrategy:** Implementacija strategija (`TeXCompositor`, `SimpleCompositor`, `ArrayCompositor`)
  - **Context:** Klasa koja koristi strategiju (`Composition`)

- **<span style="color:#D8C4F2">Učesnici:</span>**
  - **Strategy:** Definiše zajednički interfejs za sve algoritme
  - **ConcreteStrategy:** Implementira konkretne algoritme koristeći Strategy interfejsa
  - **Context:** Referencira Strategy objekat i poziva algoritme, može proslediti podatke strategiji

- **<span style="color:#CCE2CB">Tok operacije:</span>**
  1. Klijent bira i instancira `ConcreteStrategy`
  2. Prosleđuje je `Context`-u (kroz konstruktor ili setter)
  3. `Context` koristi strategiju za obradu podataka pozivom njene metode
  4. Strategija može pozvati nazad `Context` ako joj trebaju dodatni podaci
  5. Strategija se može zameniti u runtime-u bez menjanja Context koda

- **<span style="color:#F6C6C7">Posledice:</span>**
  - ✅ **Eliminacija uslovnih iskaza:** Zamena `if/else` ili `switch` blokova
  - ✅ **Fleksibilno menjanje algoritma:** U toku izvršavanja, čak i na nivou objekta
  - ✅ **Bolja testabilnost:** Svaka strategija se testira nezavisno
  - ✅ **Open/Closed princip:** Nove strategije bez menjanja postojećeg koda
  - ❌ **Povećan broj klasa:** Svaki algoritam je posebna klasa
  - ❌ **Komunikacioni troškovi:** Context može proslediti više podataka nego što strategija treba
  - ❌ **Klijent mora poznavati razlike:** Kako bi odabrao odgovarajuću strategiju

- **<span style="color:#D4A5FF">Strategy vs State:</span>**
  - **Strategy:** Klijent bira strategiju, fokus na algoritmu
  - **State:** Objekat menja stanje interno, fokus na ponašanju zavisnom od stanja
  - Strukturno slični, ali različita namera i upotreba

- **<span style="color:#D4A5FF">Strategy vs Template Method:</span>**
  - **Strategy:** Koristi kompoziciju (has-a), menja ceo algoritam
  - **Template Method:** Koristi nasleđivanje (is-a), menja korake algoritma
  - Strategy je fleksibilniji, Template Method jednostavniji

- **<span style="color:#D4A5FF">Primeri korišćenja:</span>**
  - **Sortiranje:** Različiti algoritmi sortiranja (QuickSort, MergeSort, BubbleSort)
  - **Kompresija:** Različiti formati (ZIP, RAR, 7z)
  - **Payment processing:** Različite metode plaćanja (CreditCard, PayPal, Bitcoin)
  - **Validacija:** Različita pravila validacije
  - **Routing:** Različiti algoritmi traženja puta (Dijkstra, A*, BFS)

---

**Povezani obrasci:** [State](./17-state.md) | [Template Method](https://en.wikipedia.org/wiki/Template_method_pattern) | [Flyweight](https://en.wikipedia.org/wiki/Flyweight_pattern)

**Prethodni:** [Prototype](./7-prototype.md) | **Sledeći:** [Builder](./9-builder.md) | **[Nazad na početak](./README.md)**