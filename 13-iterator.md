## 1️⃣ Iterator

- **<span style="color:#A3C2F2">Tip obrasca:</span>**  
  Ponašajni (behavioral) #obrazac-ponašanja 

- **<span style="color:#F7C59F">Namena:</span>**  
  Omogućava sekvencijalni pristup elementima agregata (kolekcije) bez otkrivanja njegove unutrašnje strukture.

- **<span style="color:#E8B5D0">Motivacija:</span>**  
  Kolekcije (npr. liste) često zahtevaju različite načine prolaska, ali nije praktično ubacivati sve u interfejs kolekcije.  
  Iterator delegira odgovornost za kretanje kroz kolekciju na zaseban objekat (`Iterator`), koji zna trenutnu poziciju i pruža standardne metode (`First()`, `Next()`, `IsDone()`, `CurrentItem()`).

- **<span style="color:#B8E0D2">Primena:</span>**  
  - Pristup elementima kolekcije bez otkrivanja strukture  
  - Višestruki načini prolaska kroz agregat  
  - Standardizovan interfejs za iteraciju raznih struktura

- **<span style="color:#FFF4B2">Struktura:</span>**  
  - **Iterator:** Interfejs za iteraciju  
  - **ConcreteIterator:** Implementira `Iterator` interfejs  
  - **Aggregate:** Interfejs kolekcije koji omogućava kreiranje iteratora  
  - **ConcreteAggregate:** Implementira `Aggregate` i vraća konkretan `Iterator`

- **<span style="color:#D8C4F2">Učesnici:</span>**  
  - `Iterator`  
  - `ConcreteIterator`  
  - `Aggregate`  
  - `ConcreteAggregate`

- **<span style="color:#CCE2CB">Tok operacije:</span>**  
  1. Klijent traži `Iterator` iz `Aggregate` preko `CreateIterator()`  
  2. Koristi `Iterator` da pristupi elementima (`First()`, `Next()`, `IsDone()`)  
  3. `Iterator` čuva stanje i poziciju  
  4. Moguće je imati više paralelnih iteratora

- **<span style="color:#F6C6C7">Posledice:</span>**  
  - Jednostavan i standardizovan pristup kolekcijama  
  - Omogućava više istovremenih prolazaka kroz istu kolekciju  
  - Ne menja klasu kolekcije – interfejs ostaje čist  
  - Podržava različite politike i stilove iteracije (npr. filtriranje)