##  🎭 **Proxy**

- **<span style="color:#A3C2F2">Tip obrasca:</span>**  
  Strukturni #obrazac-strukture 

- **<span style="color:#F7C59F">Namena:</span>**  
  Kreira zamenu (surrogat) za pristup drugom objektu.

- **<span style="color:#E8B5D0">Motivacija:</span>**  
  Omogućava kontrolu pristupa skupim objektima ili onima koji zahtevaju dodatne operacije.  
  Na primer, umesto učitavanja velikih slika pri otvaranju dokumenta, koristi se `ImageProxy` koji kreira sliku samo kada je zaista potrebna.

- **<span style="color:#B8E0D2">Primena:</span>**  
  - Virtual proxy – odlaže kreiranje skupih objekata  
  - Protection proxy – kontroliše prava pristupa  
  - Smart reference – omogućava dodatne akcije pri pristupu objektu (brojanje referenci, učitavanje iz memorije, itd.)

- **<span style="color:#FFF4B2">Struktura:</span>**  
  Proxy implementira isti interfejs kao i RealSubject, omogućava zamenu i kontrolu pristupa.

- **<span style="color:#D8C4F2">Učesnici:</span>**  
  - `Proxy`: čuva referencu ka stvarnom objektu, kontroliše pristup  
  - `RealSubject`: stvarni objekat kojem se pristupa  
  - `Subject`: zajednički interfejs za proxy i realni objekat

- **<span style="color:#CCE2CB">Tok operacije:</span>**  
  Klijent koristi proxy kao da je pravi objekat. Proxy po potrebi kreira stvarni objekat i delegira operacije.

- **<span style="color:#F6C6C7">Posledice:</span>**  
  - ✅ Ubrzava inicijalizaciju sistema  
  - ✅ Omogućava kontrolu pristupa i dodatne operacije  
  - ❌ Može dodati složenost i narušiti transparentnost