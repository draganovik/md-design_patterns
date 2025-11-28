## 🧱 Facade

- **<span style="color:#A3C2F2">Tip obrasca:</span>**  
  Strukturalni (structural) #obrazac-strukture 

- **<span style="color:#F7C59F">Namena:</span>**  
  Pruža jedinstven, pojednostavljen interfejs ka kompleksnom podsistemu.

- **<span style="color:#E8B5D0">Motivacija:</span>**  
  Klijent ne treba da zna sve detalje kako podsistem funkcioniše.  
  Na primer, `Compiler` klasa koristi `Scanner`, `Parser`, `CodeGenerator`, itd.  
  Klijent koristi samo metodu `Compile()`, dok `Facade` rukuje celim procesom pozadinski.

- **<span style="color:#B8E0D2">Primena:</span>**  
  - Kada se želi pojednostaviti korišćenje složenog sistema  
  - Kada postoji mnogo klasa koje zahtevaju međusobnu saradnju  
  - Kada je potrebna izolacija podsistema (npr. radi testiranja)

- **<span style="color:#FFF4B2">Struktura:</span>**  
  - **Facade:** Deklariše pojednostavljeni interfejs  
  - **Subsystem classes:** Obavljaju konkretne zadatke, ali ih koristi samo `Facade`

- **<span style="color:#D8C4F2">Učesnici:</span>**  
  - `Facade`: nudi interfejs klijentu  
  - `Subsystem classes`: konkretne funkcionalnosti  
  - `Client`: koristi samo `Facade`

- **<span style="color:#CCE2CB">Tok operacije:</span>**  
  1. Klijent poziva metod na `Facade`  
  2. `Facade` koordinira pozive ka klasa podsistema  
  3. `Client` ne zna ni o postojanju podsistema, niti koristi njegove klase direktno

- **<span style="color:#F6C6C7">Posledice:</span>**  
  - ✅ Pojednostavljuje korišćenje sistema  
  - ✅ Smanjuje spregu između klijenta i podsistema  
  - ✅ Olakšava zamenu i testiranje podsistema  
  - ❌ Može postati "bog objekt" ako se zloupotrebi  
  - ❌ Može sakriti korisne mogućnosti podsistema