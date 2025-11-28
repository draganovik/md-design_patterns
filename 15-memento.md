## 💾 Memento

- **<span style="color:#A3C2F2">Tip obrasca:</span>**  
  Ponašajni (behavioral) #obrazac-ponašanja 

- **<span style="color:#F7C59F">Namena:</span>**  
  Omogućava čuvanje i vraćanje prethodnog stanja objekta bez narušavanja enkapsulacije.

- **<span style="color:#E8B5D0">Motivacija:</span>**  
  Za implementaciju undo mehanizama ili kontrolnih tačaka.  
  Klijent ne sme direktno pristupati unutrašnjem stanju objekta (`Originator`), ali mora postojati način da ga vrati na prethodno stanje.  
  `Memento` objekat čuva snimak stanja, dok `Caretaker` upravlja tim snimcima bez da zna šta je unutra.

- **<span style="color:#B8E0D2">Primena:</span>**  
  - Potrebno je sačuvati stanje objekta bez izlaganja njegove unutrašnje strukture  
  - Undo operacije  
  - Izbegavanje narušavanja enkapsulacije

- **<span style="color:#FFF4B2">Struktura:</span>**  
  - **Originator:** Objekat čije stanje se čuva  
  - **Memento:** Snimak unutrašnjeg stanja  
  - **Caretaker:** Čuva i upravlja `Memento` objektima

- **<span style="color:#D8C4F2">Učesnici:</span>**  
  - `Originator`: Kreira i obnavlja `Memento`  
  - `Memento`: Čuva stanje, pristup dozvoljen samo `Originator`-u  
  - `Caretaker`: Čuva `Memento`, ne zna šta je unutra

- **<span style="color:#CCE2CB">Tok operacije:</span>**  
  1. `Originator` stvara `Memento` objekat sa trenutnim stanjem  
  2. `Caretaker` čuva `Memento`  
  3. Kada je potrebno, `Originator` koristi `Memento` da vrati prethodno stanje  
  4. `Caretaker` ne upravlja sadržajem mementa, samo ga prosleđuje

- **<span style="color:#F6C6C7">Posledice:</span>**  
  - Očuvana enkapsulacija: klijent ne vidi interno stanje  
  - `Originator` je pojednostavljen – skladištenje prepušteno spolja  
  - Može doći do povećane memorijske potrošnje kod čestih mementa  
  - Lako dodavanje undo funkcionalnosti bez invazivne promene postojećih klasa