# 🧭 Model–View–Controller
#obrazac-arhitekture

- **<span style="color:#A3C2F2">Tip obrasca:</span>**
  Arhitektonski obrazac #obrazac-arhitekture

- **<span style="color:#F7C59F">Namena:</span>**
  MVC je arhitektonski obrazac koji se koristi za organizaciju aplikacija sa korisničkim interfejsom. Uveden je kako bi se smanjila međuzavisnost između različitih delova sistema i omogućila nezavisna izmena istih.

- **<span style="color:#E8B5D0">Motivacija:</span>**
  Kada aplikacije postanu složene, potrebno je razdvojiti poslovnu logiku od korisničkog interfejsa i kontrole unosa. Bez jasne separacije, svaka promena u prikazu zahteva modifikaciju poslovne logike i obrnuto, što vodi ka rigidnom i teško održivom kodu.

- **<span style="color:#B8E0D2">Primena:</span>**
  - Kada se gradi aplikacija sa korisničkim interfejsom
  - Kada se zahteva više različitih prikaza istih podataka
  - Kada je potrebno nezavisno testiranje poslovne logike
  - Kada timovi rade paralelno na UI-u i backend logici

- **<span style="color:#FFF4B2">Struktura:</span>**
  - **Model:**
    - Sadrži podatke i poslovnu logiku aplikacije.
    - Odgovoran je za čuvanje stanja i izvršavanje operacija nad podacima.
    - Ne zna ništa o prikazu (View) ni o korisničkom unosu (Controller).
    - Obaveštava View o promenama (često kroz [Observer](./6-observer.md) obrazac).

  - **View:**
    - Vizuelni sloj koji prikazuje podatke korisniku.
    - Prati promene u Modelu i osvežava prikaz u skladu sa njima.
    - Ne komunicira direktno sa Modelom, već kroz posmatranje ili posredovanje.
    - Može koristiti [Composite](./5-composite.md) za hijerarhijske prikaze.

  - **Controller:**
    - Prima korisničke događaje (klikovi, unos teksta...).
    - Prepoznaje korisničku nameru i ažurira Model.
    - Može uticati na to koji View će se prikazati korisniku.
    - Često koristi [Command](./3-command.md) obrazac za enkapsulaciju akcija.

- **<span style="color:#D8C4F2">Učesnici:</span>**
  - **Model:** Upravlja podacima i poslovnom logikom
  - **View:** Prikazuje podatke korisniku
  - **Controller:** Procesira korisničke akcije

- **<span style="color:#CCE2CB">Tok operacije:</span>**
  1. Korisnik interaguje sa View-om (npr. klik na dugme)
  2. View prosleđuje događaj Controller-u
  3. Controller interpretira akciju i ažurira Model
  4. Model obaveštava sve registrovane View-eve o promeni
  5. View-evi se osvežavaju sa novim podacima iz Modela

- **<span style="color:#F6C6C7">Posledice:</span>**
  - ✅ **Odvajanje odgovornosti:** logika, prikaz i interakcija su jasno razdvojeni
  - ✅ **Olakšano testiranje:** omogućava izolovano testiranje poslovne logike
  - ✅ **Fleksibilnost UI-ja:** korisnički interfejs se može menjati bez izmene Modela
  - ✅ **Višestruki prikazi:** moguće je imati više View-eva nad istim Modelom
  - ✅ **Paralelni razvoj:** timovi mogu raditi na različitim slojevima istovremeno
  - ❌ **Kompleksnost:** može biti previše složen za male aplikacije
  - ❌ **Indirekcija:** povećava broj komunikacionih putanja

---

**Povezani obrasci:** [Observer](./6-observer.md) | [Command](./3-command.md) | [Composite](./5-composite.md) | [Strategy](./8-strategy.md)

**Sledeći:** [Singleton](./2-singleton.md) | **[Nazad na početak](./README.md)**
