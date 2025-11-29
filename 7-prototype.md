# 🤖 Prototype

- **<span style="color:#A3C2F2">Tip obrasca:</span>**
  Kreacioni obrazac #obrazac-kreiranja

- **<span style="color:#F7C59F">Namena:</span>**
  Omogućava kreiranje novih objekata kloniranjem postojećih (prototipova), bez potrebe za pozivanjem konstruktora ili poznavanjem konkretnih klasa.

- **<span style="color:#E8B5D0">Motivacija:</span>**
  Kada želimo da fleksibilno kreiramo nove objekte bez nasleđivanja, možemo jednostavno klonirati već pripremljene instance sa zadatim stanjem. Na primer, graficki editor može imati paletu prototipova (krug, pravougaonik, linija) koje korisnik klonira i prilagodava, umesto da svaki put kreira nove objekte konstruktorom. To smanjuje potrebu za mnogobrojnim podklasama i omogućava korisniku da sam definiše "šablon" koji treba da se klonira.

- **<span style="color:#B8E0D2">Primena:</span>**
  - Kada tip objekta nije poznat do runtime-a
  - Kada bi nasleđivanje stvorilo previše klasa koje se razlikuju samo po konfiguraciji
  - Kada postoji ograničen broj kombinacija stanja objekta
  - Kada je kreiranje objekta skupo (kompleksna inicijalizacija, I/O operacije)
  - Kada se objekti mogu konfigurisati dinamiki i koristiti kao šabloni

- **<span style="color:#FFF4B2">Struktura:</span>**
  - **Prototype:** Interfejs sa metodom `clone()`
  - **ConcretePrototype:** Implementira `clone()` i zna kako da napravi kopiju sebe
  - **Client:** Klonira objekat preko prototipa bez poznavanja konkretne klase

- **<span style="color:#D8C4F2">Učesnici:</span>**
  - **Prototype:**
    Definiše interfejs za kloniranje objekta (npr. metod `clone()` ili `copy()`). Može biti interfejs ili apstraktna klasa.
  - **ConcretePrototype:**
    Implementira operaciju kloniranja. Svaka konkretna klasa zna kako da napravi svoju kopiju (shallow ili deep copy).
  - **Client:**
    Ne kreira objekte direktno, već traži od prototipa da se klonira. Time je nezavistan od konkretnih klasa proizvoda.

- **<span style="color:#CCE2CB">Tok operacije:</span>**
  1. Klijent drži referencu na prototip objekat
  2. Klijent poziva `clone()` nad prototipom
  3. Novi objekat se stvara kopiranjem postojećeg (shallow ili deep)
  4. Klijent dobija novi objekat sa istim ili sličnim stanjem
  5. Objekat se može dodatno konfigurisati ili koristiti direktno

- **<span style="color:#F6C6C7">Posledice:</span>**
  - ✅ **Dodavanje novih tipova u runtime-u:** Bez menjanja koda
  - ✅ **Fleksibilno kreiranje:** Bez čvrstog povezivanja sa konkretnim klasama
  - ✅ **Smanjenje podklasa:** Umesto hijerarhije, različite konfiguracije
  - ✅ **Performanse:** Može biti brže od konstruktora ako je inicijalizacija skupa
  - ❌ **Kompleksnost kloniranja:** Duboke kopije mogu biti složene (cirkuralne reference)
  - ❌ **Skrivene zavisnosti:** Nije uvek jasno koje stanje se kopira

- **<span style="color:#D4A5FF">Shallow vs Deep Copy:</span>**
  - **Shallow Copy:** Kopiraju se samo reference (deljeno stanje između original-klon)
  - **Deep Copy:** Kopiraju se svi objekti rekurzivno (potpuno nezavisan klon)
  - **Izbor:** Zavisi od prirode podataka i zahteva aplikacije

- **<span style="color:#D4A5FF">Implementacione tehnike:</span>**
  - **Copy constructor:** Eksplicitan konstruktor koji prima instancu istog tipa
  - **Clone metoda:** Standardna metoda (npr. `Object.clone()` u Java)
  - **Serialization:** Serijalizacija i deserijalizacija za duboku kopiju
  - **Prototype Registry:** Centralizovano skladište prototipova (Prototype Manager)

- **<span style="color:#D4A5FF">Primeri korišćenja:</span>**
  - **Grafički editori:** Kopiranje oblika, komponenti
  - **Game development:** Kloniranje entiteta, neprijatelja, predmeta
  - **Konfiguracioni objekti:** Template pattern za podrazumevane postavke
  - **Data processing:** Kreiranje objekata sa već učitanim podacima

---

**Povezani obrasci:** [Abstract Factory](./10-abstract-factory.md) | [Composite](./5-composite.md) | [Decorator](./14-decorator.md)

**Prethodni:** [Observer](./6-observer.md) | **Sledeći:** [Strategy](./8-strategy.md) | **[Nazad na početak](./README.md)**
