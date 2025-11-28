## 🔁 Command

- **<span style="color:#A3C2F2">Tip obrasca:</span>**
  Ponašajni (behavioral) obrazac #obrazac-ponašanja

- **<span style="color:#F7C59F">Namena:</span>**
  Omogućava enkapsulaciju zahteva kao objekta, čime se podržava parametrizacija, logovanje, poništavanje i redosled izvršavanja operacija.

- **<span style="color:#E8B5D0">Motivacija:</span>**
  Kada korisnički interfejs (npr. dugme ili meni stavka) treba da izvrši akciju, ali bez direktnog znanja o implementaciji te akcije.
  Zahtev se pretvara u objekat (komandu), koji se može skladištiti, proslediti ili poništiti.

- **<span style="color:#B8E0D2">Primena:</span>**

  - Parametrizacija objekata akcijama.
  - Redosledno izvršavanje i odlaganje izvršavanja komandi.
  - Undo/Redo mehanizmi (`execute()` i `unexecute()`).
  - Logovanje i replikacija (npr. sistemska transakcija).
  - Izgradnja sistema sa transakcijama visokog nivoa.

- **<span style="color:#FFF4B2">Struktura:</span>**

  - **Command:** Interfejs sa metodom `execute()`
  - **ConcreteCommand:** Implementira `execute()` i referencira Receiver
  - **Invoker:** Poziva `execute()`
  - **Receiver:** Zna kako da izvrši operaciju
  - **Client:** Inicijalizuje komandu i dodeljuje joj Receiver-a

- **<span style="color:#D8C4F2">Učesnici:</span>**

  - **Command** – definicija interfejsa
  - **ConcreteCommand** – implementacija `execute`
  - **Invoker** – poziva komandu
  - **Receiver** – izvršava pravu akciju
  - **Client** – povezuje sve delove

- **<span style="color:#CCE2CB">Tok operacije:</span>**

  1. Klijent kreira `ConcreteCommand` i postavlja `Receiver`.
  2. `Invoker` čuva komandu.
  3. `Invoker` poziva `execute()`.
  4. `ConcreteCommand` poziva akciju na `Receiver`-u.
  5. (Opcionalno) čuva staro stanje za `unexecute()`.

- **<span style="color:#F6C6C7">Posledice:</span>**
  - Razdvajanje zahteva od izvršenja.
  - Jednostavno dodavanje novih komandi.
  - Undo/redo mehanizmi.
  - Podrška za makro-komande i logovanje.
  - Fleksibilna i proširiva arhitektura.
