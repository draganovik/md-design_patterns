# 🔌 Adapter

- **<span style="color:#A3C2F2">Tip obrasca:</span>**
  Strukturalni obrazac #obrazac-strukture

- **<span style="color:#F7C59F">Namena:</span>**
  Prilagođava interfejs postojeće klase tako da odgovara interfejsu koji klijent očekuje. Omogućava saradnju klasa koje inače ne bi bile kompatibilne.

- **<span style="color:#E8B5D0">Motivacija:</span>**
  Postojeće klase (npr. `TextView`) nisu dizajnirane za konkretan domen (npr. `Shape`). Kako bi se omogućila ponovna upotreba takvih klasa bez izmene izvornog koda, koristi se Adapter da ih prilagodi traženom interfejsu. Na primer, `TextShape` postaje most između `TextView` i `Shape`, omogućavajući da se text komponenta koristi kao grafički objekat.

- **<span style="color:#B8E0D2">Primena:</span>**
  - Kada postojeća klasa ne odgovara traženom interfejsu
  - Kada se želi omogućiti upotreba budućih nepoznatih klasa
  - Kada treba napraviti jedan Adapter za celu hijerarhiju (objektna verzija)
  - Integracija biblioteka trećih strana
  - Legacy kod sa novim sistemima

- **<span style="color:#FFF4B2">Struktura:</span>**
  - **Klasa-verzija:** koristi višestruko nasleđivanje (nasleđuje i `Adaptee` i `Target`)
  - **Objekat-verzija:** koristi kompoziciju – `Adapter` sadrži instancu `Adaptee`

- **<span style="color:#D8C4F2">Učesnici:</span>**
  - **Target:** Očekivani interfejs (`Shape`)
  - **Client:** Koristi `Target` interfejs (`DrawingEditor`)
  - **Adaptee:** Postojeći interfejs (`TextView`)
  - **Adapter:** Prevodi pozive sa `Target` na `Adaptee` (`TextShape`)

- **<span style="color:#CCE2CB">Tok operacije:</span>**
  1. Klijent poziva metodu na Adapter objektu kroz `Target` interfejs
  2. Adapter prevodi zahtev i prosleđuje ga `Adaptee` objektu
  3. `Adaptee` izvršava stvarnu logiku
  4. Rezultat se vraća klijentu kroz Adapter

- **<span style="color:#F6C6C7">Posledice:</span>**
  **Klasa-verzija:**
  - ✅ Omogućava override ponašanja `Adaptee` klase
  - ✅ Ne koristi dodatne objekte (jedna instanca)
  - ❌ Ne radi sa podklasama `Adaptee`
  - ❌ Zahteva višestruko nasleđivanje (nije dostupno u svim jezicima)

  **Objekat-verzija:**
  - ✅ Radi sa celom hijerarhijom `Adaptee` klasa
  - ✅ Može adaptirati više `Adaptee` objekata
  - ✅ Fleksibilnija i lakša za održavanje
  - ❌ Teže je menjati ponašanje `Adaptee` (potrebno dodatno nasleđivanje)
  - ❌ Dodatna indirekcija

- **<span style="color:#D4A5FF">Primeri korišćenja:</span>**
  - **API integracije:** Prilagođavanje eksterne biblioteke vašem interfejsu
  - **Legacy sistemi:** Omogućavanje starog koda da radi sa novim
  - **Cross-platform development:** Apstrakcija platformskih razlika
  - **Data format conversion:** XML ↔ JSON adapteri

---

**Povezani obrasci:** [Bridge](./12-bridge.md) | [Decorator](./14-decorator.md) | [Proxy](./18-proxy.md)

**Prethodni:** [Command](./3-command.md) | **Sledeći:** [Composite](./5-composite.md) | **[Nazad na početak](./README.md)**
