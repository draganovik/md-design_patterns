## 👁️ Observer

- **<span style="color:#A3C2F2">Tip obrasca:</span>**
  Ponašajni obrazac #obrazac-ponašanja 

- **<span style="color:#F7C59F">Namena:</span>**
  Omogućava da više objekata bude automatski obavešteno o promeni stanja jednog objekta.

- **<span style="color:#E8B5D0">Motivacija:</span>**
  Kada objekti zavise od istih podataka (npr. više prikaza istih vrednosti), potrebno je da se svi sinhronizuju kad podaci promene stanje.
  Da bi izbegli čvrstu povezanost, koristi se mehanizam pretplate — `Subject` obaveštava sve zainteresovane `Observer`-e, ne znajući ništa o njihovoj konkretnoj implementaciji.

- **<span style="color:#B8E0D2">Primena:</span>**

  - Kada promena jednog objekta treba da se odrazi na više drugih.
  - Kada broj zavisnih objekata nije poznat unapred.
  - Kada želimo da objekti budu povezani, ali ne i čvrsto spregnuti.

- **<span style="color:#FFF4B2">Struktura:</span>**

  - `Subject`: vodi listu `Observer`-a i obaveštava ih.
  - `Observer`: definiše metod za ažuriranje.
  - `ConcreteSubject`: implementira logiku promene stanja.
  - `ConcreteObserver`: reaguje na promene subjekta.

- **<span style="color:#D8C4F2">Učesnici:</span>**

  - **Subject:**
    Čuva listu observer-a i nudi metode za njihovu registraciju i odjavu. Kada se njegovo stanje promeni, obaveštava sve pretplaćene observer-e.
  - **Observer:**
    Interfejs koji definiše metod za primanje obaveštenja o promeni (`update()` ili slično).
  - **ConcreteSubject:**
    Sadrži stvarno stanje koje se menja. Kada dođe do promene, poziva obaveštenje za sve observer-e.
  - **ConcreteObserver:**
    Sadrži referencu na ConcreteSubject, i ažurira svoje stanje kada dobije obaveštenje.

- **<span style="color:#CCE2CB">Tok operacije:</span>**

  1. `Observer` se registruje kod `Subject`.
  2. Kada `Subject` promeni stanje, poziva `update()` nad svim `Observer`-ima.
  3. `Observer` preuzima novo stanje ako želi.

- **<span style="color:#F6C6C7">Posledice:</span>**
  - Slaba sprega i fleksibilnost (subject ne zna za konkretne observatore).
  - Laka promena ili dodavanje observera.
  - Mogućnost nepredviđenih kaskadnih ažuriranja.
