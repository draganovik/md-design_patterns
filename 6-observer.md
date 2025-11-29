## 👁️ Observer

- **<span style="color:#A3C2F2">Tip obrasca:</span>**
  Ponašajni obrazac #obrazac-ponašanja

- **<span style="color:#F7C59F">Namena:</span>**
  Omogućava da više objekata bude automatski obavešteno o promeni stanja jednog objekta. Definiše zavisnost "jedan-prema-više" između objekata.

- **<span style="color:#E8B5D0">Motivacija:</span>**
  Kada objekti zavise od istih podataka (npr. više prikaza istih vrednosti: grafikon, tabela, brojevi), potrebno je da se svi sinhronizuju kad podaci promene stanje. Da bi izbegli čvrstu povezanost između subjekta i posmatrača, koristi se mehanizam pretplate — `Subject` obaveštava sve zainteresovane `Observer`-e, ne znajući ništa o njihovoj konkretnoj implementaciji. Ovo omogućava dodavanje ili uklanjanje posmatrača u runtime-u.

- **<span style="color:#B8E0D2">Primena:</span>**
  - Kada promena jednog objekta treba da se odrazi na više drugih
  - Kada broj zavisnih objekata nije poznat unapred
  - Kada želimo da objekti budu povezani, ali ne i čvrsto spregnuti
  - Event-driven sistemi i reactive programming
  - Model-View arhitekture (kao u [MVC](./1-mvc.md))

- **<span style="color:#FFF4B2">Struktura:</span>**
  - **Subject:** Vodi listu `Observer`-a i obaveštava ih o promenama
  - **Observer:** Definiše metod za ažuriranje (`update()`)
  - **ConcreteSubject:** Implementira logiku promene stanja
  - **ConcreteObserver:** Reaguje na promene subjekta

- **<span style="color:#D8C4F2">Učesnici:</span>**
  - **Subject:**
    Čuva listu observer-a i nudi metode za njihovu registraciju (`attach()`) i odjavu (`detach()`). Kada se njegovo stanje promeni, poziva `notify()` da obavesti sve pretplaćene observer-e.
  - **Observer:**
  Interfejs koji definiše metod za primanje obaveštenja o promeni (`update()` ili slično).
  - **ConcreteSubject:**
    Sadrži stvarno stanje koje se menja. Kada dođe do promene, poziva obaveštenje za sve observer-e. Može implementirati `getState()` da omogući observer-ima pristup stanju.
  - **ConcreteObserver:**
    Sadrži referencu na ConcreteSubject, i ažurira svoje stanje kada dobije obaveštenje.

- **<span style="color:#CCE2CB">Tok operacije:</span>**
  1. `Observer` se registruje kod `Subject` pozivom `attach()`
  2. Kada `Subject` promeni stanje, poziva `notify()`
  3. `notify()` prolazi kroz listu i poziva `update()` nad svim `Observer`-ima
  4. Svaki `Observer` može povući novo stanje (pull) ili ga dobiti kao parametar (push)
  5. `Observer` se može odjaviti pozivom `detach()`

- **<span style="color:#F6C6C7">Posledice:</span>**
  - ✅ **Slaba sprega:** Subject ne zna za konkretne observere, samo za interfejs
  - ✅ **Fleksibilnost:** Lako dodavanje ili uklanjanje observera u runtime-u
  - ✅ **Broadcast komunikacija:** Jedan poziv obaveštava sve zainteresovane
  - ✅ **Podrška za event-driven sisteme:** Prirodno modelovanje događaja
  - ❌ **Nepredvidivi redosled ažuriranja:** Ako observer-i zavise jedni od drugih
  - ❌ **Mogućnost curenja memorije:** Ako se observeri ne odjave pravilno
  - ❌ **Kaskadna ažuriranja:** Mogu biti skupa ako su česta

- **<span style="color:#D4A5FF">Push vs Pull model:</span>**
  - **Push:** Subject šalje detaljne informacije observer-ima (mogu dobiti nepotrebne podatke)
  - **Pull:** Subject šalje minimalno obaveštenje, observer-i povlače šta im treba (dodatni pozivi)

- **<span style="color:#D4A5FF">Primeri korišćenja:</span>**
  - **MVC arhitekture:** Model obaveštava View o promenama
  - **Event listeneri:** GUI komponente (dugmad, text field-ovi)
  - **Reactive programiranje:** RxJS, RxJava streams
  - **Publish-Subscribe sistemi:** Message brokers, notification servisi

---

**Povezani obrasci:** [MVC](./1-mvc.md) | [Mediator](https://en.wikipedia.org/wiki/Mediator_pattern) | [Singleton](./2-singleton.md)

**Prethodni:** [Composite](./5-composite.md) | **Sledeći:** [Prototype](./7-prototype.md) | **[Nazad na početak](./README.md)**
