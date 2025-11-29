## 🧳 Visitor

- **<span style="color:#A3C2F2">Tip obrasca:</span>**
  Ponašajni obrazac #obrazac-ponasanja

- **<span style="color:#F7C59F">Namena:</span>**
  Dodavanje novih operacija nad stabilnom hijerarhijom elemenata bez menjanja njihovog koda.

- **<span style="color:#E8B5D0">Motivacija:</span>**
  AST u kompajleru: čvorovi stabilni, operacije rastu (type-check, optimizacija, generisanje koda). Visitor grupiše operacije spolja i koristi double-dispatch (`element.accept(visitor)` → `visitor.visitConcrete(element)`).

- **<span style="color:#B8E0D2">Primena:</span>**
  - Stabilna struktura + česte nove operacije
  - Analize, validacije, transformacije
  - Odvajanje različitih faza obrade
  - Akumulacija podataka tokom obilaska (statistike)

- **<span style="color:#FFF4B2">Struktura:</span>**
  - `Visitor`
  - `ConcreteVisitorA/B`
  - `Element` (interfejs sa `accept`)
  - `ConcreteElement`
  - `ObjectStructure`

- **<span style="color:#D8C4F2">Učesnici:</span>**
  - **Element:** poziva `visitor.visit(this)`
  - **Visitor:** definicija `visitX` metoda
  - **ConcreteVisitor:** implementacije operacija
  - **ObjectStructure:** omogućava iteraciju nad elementima

- **<span style="color:#CCE2CB">Tok operacije:</span>**
  1. Klijent kreira posetioca.
  2. Poziva `accept` nad svakim elementom.
  3. Element poziva odgovarajući `visit`.
  4. Visitor sakuplja ili proizvodi rezultat.

- **<span style="color:#F6C6C7">Posledice:</span>**
  - ✅ Jednostavno dodavanje novih operacija
  - ✅ Grupisanje logike
  - ✅ Akumulacija stanja bez globalnog skladišta
  - ❌ Dodavanje novih tipova elemenata teško (menja sve visitore)
  - ❌ Moguće otkrivanje internih detalja (narušavanje enkapsulacije)

- **<span style="color:#D4A5FF">Varijante:</span>**
  - Acyclic Visitor (bez potrebe da svaki visitor zna sve concrete tipove)
  - Reflective visitor (reflection umesto overload)
  - Composite + Visitor (klasična AST)
  - Inline visitor (lambda poseta)

- **<span style="color:#D4A5FF">Visitor vs Iterator vs Strategy:</span>**
  - Iterator: traversal; Visitor: operacija po tipu; Strategy: zamena algoritma bez double-dispatch.
  - Visitor + Iterator: odvojen traversal + dinamička operacija.

- **<span style="color:#D4A5FF">Primeri korišćenja:</span>**
  - Kompajleri (semantička analiza)
  - Document/scene processing
  - Validacija modela
  - Generisanje različitih izlaza (HTML, PDF, JSON)

---

**Povezani obrasci:** [Composite](./5-composite.md) | [Iterator](./13-iterator.md) | [Strategy](./8-strategy.md)

**Prethodni:** [Proxy](./18-proxy.md) | **Sledeći:** — kraj liste | **[Nazad na početak](./README.md)**