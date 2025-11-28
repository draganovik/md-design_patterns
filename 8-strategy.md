## 🧠 Strategy

- **<span style="color:#A3C2F2">Tip obrasca:</span>**  
  Ponašajni (behavioral) obrazac #obrazac-ponašanja 

- **<span style="color:#F7C59F">Namena:</span>**  
  Definiše porodicu algoritama, enkapsulira svaki od njih i omogućava njihovu zamenu u toku rada. Algoritam se može menjati nezavisno od konteksta koji ga koristi.

- **<span style="color:#E8B5D0">Motivacija:</span>**  
  Kada klasa (npr. `Composition`) koristi više varijanti algoritma (npr. različiti načini prelamanja teksta), bilo bi teško održavati sve unutar jedne klase. Strategy obrazac omogućava da se algoritmi (npr. `TeXCompositor`, `SimpleCompositor`) odvoje u posebne klase koje se mogu lako zameniti.

- **<span style="color:#B8E0D2">Primena:</span>**  
  - Kada postoji više varijanti istog ponašanja.  
  - Kada se želi izbeći ugradnja algoritma direktno u klasu.  
  - Kada se algoritmi međusobno razlikuju po vremensko-prostornim zahtevima.  
  - Kada klijent ne treba da zna detalje implementacije algoritma.

- **<span style="color:#FFF4B2">Struktura:</span>**  
  - **Strategy:** Interfejs (npr. `Compositor`)  
  - **ConcreteStrategy:** Implementacija strategija (`TeXCompositor`, `SimpleCompositor`)  
  - **Context:** Klasa koja koristi strategiju (`Composition`)

- **<span style="color:#D8C4F2">Učesnici:</span>**  
  - **Strategy:** Definiše interfejs za algoritme  
  - **ConcreteStrategy:** Implementira konkretne algoritme  
  - **Context:** Referencira Strategy i poziva algoritme

- **<span style="color:#CCE2CB">Tok operacije:</span>**  
  1. Klijent instancira `ConcreteStrategy`  
  2. Prosleđuje je `Context`-u  
  3. `Context` koristi strategiju za obradu podataka  
  4. Strategija može pozvati nazad `Context` ako je potrebno

- **<span style="color:#F6C6C7">Posledice:</span>**  
  - Eliminacija uslova (if/else) u kodu  
  - Fleksibilno menjanje algoritma u toku izvršavanja  
  - Povećava broj klasa i objekata  
  - Klijent mora znati razliku između strategija  
  - Mogući komunikacioni troškovi (ako kontekst prosleđuje nepotrebne podatke)