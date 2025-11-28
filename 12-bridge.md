## 🌉 Bridge

- **<span style="color:#A3C2F2">Tip obrasca:</span>**  
  Strukturalni (structural) #obrazac-strukture 

- **<span style="color:#F7C59F">Namena:</span>**  
  Razdvaja apstrakciju od implementacije kako bi mogli da se razvijaju nezavisno jedan od drugog.

- **<span style="color:#E8B5D0">Motivacija:</span>**  
  Kada apstrakcija (npr. `Window`) može imati više implementacija (npr. `XWindows`, `MSWindows`), korišćenje nasleđivanja vodi do eksplozije klasa (npr. `XIconWindow`, `MSIconWindow`).  
  Osim toga, klijent postaje zavistan od konkretne implementacije. Bridge omogućava da se apstraktna klasa (`Window`) i konkretna implementacija (`WindowImp`) razvijaju nezavisno i povežu u toku izvršavanja.

- **<span style="color:#B8E0D2">Primena:</span>**  
  - Kada se želi izbeći čvrsta veza između apstrakcije i implementacije  
  - Kada obe hijerarhije (apstraktna i implementaciona) treba da budu proširive  
  - Kada klijenti ne treba da znaju detalje implementacije

- **<span style="color:#FFF4B2">Struktura:</span>**  
  - **Abstraction (Window):** Definiše interfejs i čuva referencu na `Implementor`  
  - **RefinedAbstraction (IconWindow):** Dodaje dodatne operacije  
  - **Implementor (WindowImp):** Definiše osnovne operacije  
  - **ConcreteImplementor (XWindowImp, MSWindowImp):** Platformski zavisne implementacije

- **<span style="color:#D8C4F2">Učesnici:</span>**  
  - `Window` (Abstraction)  
  - `IconWindow` (RefinedAbstraction)  
  - `WindowImp` (Implementor)  
  - `XWindowImp`, `MSWindowImp` (ConcreteImplementor)

- **<span style="color:#CCE2CB">Tok operacije:</span>**  
  1. Klijent koristi `Window` (apstrakciju)  
  2. `Window` koristi `WindowImp` za osnovne funkcije  
  3. Implementacija može da se zameni bez menjanja apstrakcije  
  4. Platformska logika izolovana u `ConcreteImplementor`

- **<span style="color:#F6C6C7">Posledice:</span>**  
  - Fleksibilnost – nezavisno razvijanje apstrakcije i implementacije  
  - Smanjenje broja klasa (nema eksplozije kombinacija)  
  - Klijent ne mora da zna implementacione detalje  
  - Promena implementacije moguća u toku rada aplikacije