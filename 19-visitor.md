## 🧳 **Visitor**

- **<span style="color:#A3C2F2">Tip obrasca:</span>**  
  Ponašajni #obrazac-ponašanja 

- **<span style="color:#F7C59F">Namena:</span>**  
  Omogućava dodavanje novih operacija nad strukturom objekata bez menjanja njihovih klasa.

- **<span style="color:#E8B5D0">Motivacija:</span>**  
  Koristi se kada imamo stabilnu strukturu objekata (npr. čvorove AST-a u kompajleru), ali često menjamo ili dodajemo nove operacije nad njima.  
  Omogućava izolaciju logike kao posebnog posetioca koji se "ubacuje" u strukturu kada je potreban.

- **<span style="color:#B8E0D2">Primena:</span>**  
  - Kada je struktura objekata složena i sadrži mnoge klase  
  - Kada različite operacije treba izvesti nad istim elementima  
  - Kada se operacije često menjaju, ali struktura ostaje stabilna

- **<span style="color:#FFF4B2">Struktura:</span>**  
  Visitor definiše operacije za svaku konkretnu klasu elemenata.  
  Elementi implementiraju `accept()` koji poziva odgovarajući `visit()` metod.

- **<span style="color:#D8C4F2">Učesnici:</span>**  
  - `Visitor`: interfejs za sve operacije  
  - `ConcreteVisitor`: konkretna implementacija posetioca (npr. `TypeCheckingVisitor`)  
  - `Element`: definicija `accept(visitor)` metode  
  - `ConcreteElement`: čvorovi koji implementiraju `accept()`  
  - `ObjectStructure`: omogućava posetiocima obilazak

- **<span style="color:#CCE2CB">Tok operacije:</span>**  
  Posetilac se prosleđuje svakom elementu kroz `accept()` metod, koji poziva odgovarajući `visit()` metod posetioca.

- **<span style="color:#F6C6C7">Posledice:</span>**  
  - ✅ Lako dodavanje novih operacija  
  - ✅ Grupisanje povezanih operacija  
  - ❌ Teže dodavanje novih elemenata (potrebno menjati sve posetioce)  
  - ❌ Potencijalno narušavanje enkapsulacije zbog pristupa stanjima  
  - ✅ Posetioci mogu akumulirati stanje (bez globalnih promenljivih)