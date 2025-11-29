## 🔁 Iterator

- **<span style="color:#A3C2F2">Tip obrasca:</span>**
  Ponašajni (behavioral) obrazac #obrazac-ponasanja

- **<span style="color:#F7C59F">Namena:</span>**
  Obezbeđuje sekvencijalni pristup elementima agregata bez izlaganja unutrašnje strukture. Standardizuje kretanje kroz različite kolekcije.

- **<span style="color:#E8B5D0">Motivacija:</span>**
  Kolekcije (lista, skup, stablo, graf) zahtevaju različite načine obilaska. Umetanje svih traversal metoda u samu kolekciju komplikuje interfejs. Iterator izmešta logiku obilaska u zaseban objekat koji čuva stanje i podržava više stilova iteracije, omogućavajući paralelne prolaze.

- **<span style="color:#B8E0D2">Primena:</span>**
  - Potrebni različiti traversal obrasci (inorder, reverse, filtrirani)
  - Višestruki aktivni prolazi kroz istu kolekciju
  - Skrivanje kompleksne interne strukture (npr. kompozit)
  - Stream-like lenja evaluacija
  - Odvajanje algoritma obilaska od kolekcije

- **<span style="color:#FFF4B2">Struktura:</span>**
  - `Iterator` (interfejs)
  - `ConcreteIterator` (čuva indeks/pointer)
  - `Aggregate` (fabrika za iterator)
  - `ConcreteAggregate` (konkretna kolekcija)

- **<span style="color:#D8C4F2">Učesnici:</span>**
  - **Iterator:** definiše operacije `hasNext()`, `next()`
  - **ConcreteIterator:** implementira logiku kretanja
  - **Aggregate:** metod za kreiranje iteratora
  - **ConcreteAggregate:** vraća odgovarajući iterator

- **<span style="color:#CCE2CB">Tok operacije:</span>**
  1. Klijent traži iterator od agregata.
  2. Poziva `hasNext()` / `next()`.
  3. Iterator ažurira interno stanje pozicije.
  4. Više iteratora može koegzistirati nezavisno.

- **<span style="color:#F6C6C7">Posledice:</span>**
  - ✅ Jedinstven API za obilazak
  - ✅ Paralelne iteracije
  - ✅ Enkapsulacija strukture agregata
  - ✅ Dodavanje novih traversal strategija bez izmene kolekcije
  - ❌ Dodatna klasa / objekat
  - ❌ Komplikacije kod modifikacije kolekcije tokom iteracije

- **<span style="color:#D4A5FF">Varijante:</span>**
  - External vs Internal iterator
  - Jednosmerni vs Dvosmerni
  - Fail-fast vs Weakly-consistent
  - Filter / Predicate iterator
  - Lazy generator (yield stil)

- **<span style="color:#D4A5FF">Iterator vs Visitor:</span>**
  - Iterator fokus na sekvencijalnom pristupu; Visitor na dodavanju novih operacija nad elementima.
  - Visitor olakšava dodavanje ponašanja, Iterator dodavanje traversal stilova.

- **<span style="color:#D4A5FF">Primeri korišćenja:</span>**
  - Java `Iterator`, `ListIterator`
  - Python generatori (`yield`)
  - C# `IEnumerator` / `IEnumerable`
  - Stream API (filter/map/reduce obrasci)

---

**Povezani obrasci:** [Composite](./5-composite.md) | [Visitor](./19-visitor.md) | [Strategy](./8-strategy.md)

**Prethodni:** [Bridge](./12-bridge.md) | **Sledeći:** [Decorator](./14-decorator.md) | **[Nazad na početak](./README.md)**