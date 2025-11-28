## 🚦 State

- **<span style="color:#A3C2F2">Tip obrasca:</span>**  
  Ponašajni (behavioral) #obrazac-ponašanja 

- **<span style="color:#F7C59F">Namena:</span>**  
  Omogućava objektu da promeni ponašanje kada mu se promeni unutrašnje stanje — kao da je promenio klasu.

- **<span style="color:#E8B5D0">Motivacija:</span>**  
  Umesto da koristi "if/else" ili "switch" za menjanje ponašanja objekta u zavisnosti od stanja, ponašanje se razdvaja u zasebne klase.  
  Npr. `TCPConnection` koristi stanje `Established`, `Listen`, `Closed`, gde svako stanje određuje ponašanje metoda `Open()`, `Close()`, `Transmit()`, itd.

- **<span style="color:#B8E0D2">Primena:</span>**  
  - Kada objekat ima kompleksna ponašanja u zavisnosti od stanja  
  - Kada kod sadrži više uslovnih grana povezanih sa stanjima  
  - Kada se stanja često menjaju i dele ponašanje

- **<span style="color:#FFF4B2">Struktura:</span>**  
  - **Context (TCPConnection):** Drži referencu na trenutno stanje  
  - **State (TCPState):** Interfejs za stanja  
  - **ConcreteState:** Implementacije konkretnih stanja (`EstablishedState`, `ClosedState`, itd.)

- **<span style="color:#D8C4F2">Učesnici:</span>**  
  - `Context`: delegira ponašanja na `State`  
  - `State`: definiše interfejs ponašanja  
  - `ConcreteState`: implementira ponašanje za konkretno stanje

- **<span style="color:#CCE2CB">Tok operacije:</span>**  
  1. `Context` sadrži referencu na trenutno `State`  
  2. `Context` delegira sve pozive na trenutno stanje  
  3. Stanje može izmeniti `Context` tako da pređe u drugo stanje

- **<span style="color:#F6C6C7">Posledice:</span>**  
  - ✅ Eliminacija velikih `switch`/`if` blokova  
  - ✅ Dodavanje novih stanja bez menjanja `Context` klase  
  - ✅ Bolja organizacija koda  
  - ❌ Povećava broj klasa  
  - ❌ Teža integracija sa istorijskim pristupom ako je logika ranije bila unutar jedne klase