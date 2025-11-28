## 🔌  Adapter

- **<span style="color:#A3C2F2">Tip obrasca:</span>**
  Strukturalni obrazac #obrazac-strukture

- **<span style="color:#F7C59F">Namena:</span>**
  Prilagođava interfejs postojeće klase tako da odgovara interfejsu koji klijent očekuje. Omogućava saradnju klasa koje inače ne bi bile kompatibilne.

- **<span style="color:#E8B5D0">Motivacija:</span>**
  Postojeće klase (npr. `TextView`) nisu dizajnirane za konkretan domen (npr. `Shape`). Kako bi se omogućila ponovna upotreba takvih klasa bez izmene izvornog koda, koristi se Adapter da ih prilagodi traženom interfejsu (`TextShape` postaje most između `TextView` i `Shape`).

- **<span style="color:#B8E0D2">Primena:</span>**

  - Kada postojeća klasa ne odgovara traženom interfejsu.
  - Kada se želi omogućiti upotreba budućih nepoznatih klasa.
  - Kada treba napraviti jedan Adapter za celu hijerarhiju (objektna verzija).

- **<span style="color:#FFF4B2">Struktura:</span>**

  - **Klasa-verzija:** koristi višestruko nasleđivanje (nasleđuje i `Adaptee` i `Target`).
  - **Objekat-verzija:** koristi kompoziciju – `Adapter` sadrži instancu `Adaptee`.

- **<span style="color:#D8C4F2">Učesnici:</span>**

  - **Target:** očekivani interfejs (`Shape`)
  - **Client:** koristi `Target` interfejs (`DrawingEditor`)
  - **Adaptee:** postojeći interfejs (`TextView`)
  - **Adapter:** prevodi pozive sa `Target` na `Adaptee` (`TextShape`)

- **<span style="color:#CCE2CB">Tok operacije:</span>**

  1. Klijent poziva metodu na Adapter objektu.
  2. Adapter prevodi zahtev i prosleđuje ga `Adaptee` objektu.
  3. Adaptee izvršava stvarnu logiku.

- **<span style="color:#F6C6C7">Posledice:</span>**
  - **Klasa-verzija:** ne radi sa podklasama `Adaptee`, ali omogućava override ponašanja i ne koristi dodatne objekte.
  - **Objekat-verzija:** radi sa celom hijerarhijom `Adaptee` klasa, ali je teže menjati ponašanje (npr. potrebno dodatno naslediti `Adapter`).
