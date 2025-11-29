## 🏭 Factory Method

- **<span style="color:#A3C2F2">Tip obrasca:</span>**
  Kreacioni obrazac #obrazac-kreiranja

- **<span style="color:#F7C59F">Namena:</span>**
  Definiše interfejs za kreiranje objekata, dopuštajući podklasama da odluče koju konkretnu klasu će instancirati. Zove se još i "virtualni konstruktor".

- **<span style="color:#E8B5D0">Motivacija:</span>**
  Okvir (framework) želi da pozove kreiranje objekta, ali ne zna koji tip treba da nastane – to određuje aplikacija/klijent. Izbegava se hardkodiranje tipova i postiže proširivost kroz nasleđivanje.

- **<span style="color:#B8E0D2">Primena:</span>**
  - Kada klasa ne može da predvidi konkretan tip objekta
  - Kada se kreiranje delegira podklasama
  - Kada se želi proširivost bez modifikacije bazne klase
  - Kada se instanciranje razlikuje po kontekstu (dokument, konekcija)
  - Kada želite lazy instanciranje putem override-a

- **<span style="color:#FFF4B2">Struktura:</span>**
  - `Creator` – deklariše Factory Method
  - `ConcreteCreator` – override-uje i vraća konkretan `Product`
  - `Product` – interfejs proizvoda
  - `ConcreteProduct` – implementacija proizvoda

- **<span style="color:#D8C4F2">Učesnici:</span>**
  - **Creator:** može sadržati podrazumevanu implementaciju
  - **ConcreteCreator:** bira konkretan tip
  - **Product:** zajednički interfejs
  - **ConcreteProduct:** specifični tip

- **<span style="color:#CCE2CB">Tok operacije:</span>**
  1. Klijent radi sa `Creator` referencom.
  2. Poziva operaciju koja koristi Factory Method.
  3. Factory Method kreira (ili prosleđuje) konkretan `Product`.
  4. Klijent koristi `Product` preko interfejsa.

- **<span style="color:#F6C6C7">Posledice:</span>**
  - ✅ Odvajanje kreiranja od upotrebe
  - ✅ Lako dodavanje novih tipova kroz podklase
  - ✅ Poštovanje Open/Closed principa
  - ❌ Povećava broj klasa (svaki tip zahteva podklasu)
  - ❌ Nasleđivanje može biti zlorabljeno za jednostavne slučajeve

- **<span style="color:#D4A5FF">Varijante:</span>**
  - Apstraktna metoda (bez default implementacije)
  - Metoda sa default implementacijom (opciono override)
  - Parametrizovana factory metoda (npr. tip preko enum)
  - Interni cache (flyweight kombinacija)

- **<span style="color:#D4A5FF">Factory Method vs Abstract Factory:</span>**
  - Factory Method → jedan proizvod
  - Abstract Factory → porodica proizvoda
  - Abstract Factory često implementiran nizom Factory Method-a.

- **<span style="color:#D4A5FF">Primeri korišćenja:</span>**
  - Okviri za dokumente (različiti tipovi)
  - Logger sistemi (FileLogger, DbLogger)
  - Parseri formata (JSON, XML, YAML)
  - Konekcije (SQL vs NoSQL)
  - UI kontrole specifične po platformi

---

**Povezani obrasci:** [Abstract Factory](./10-abstract-factory.md) | [Prototype](./7-prototype.md) | [Template Method](https://en.wikipedia.org/wiki/Template_method_pattern)

**Prethodni:** [Abstract Factory](./10-abstract-factory.md) | **Sledeći:** [Bridge](./12-bridge.md) | **[Nazad na početak](./README.md)**