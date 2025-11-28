## 🧬 Singleton

- **<span style="color:#A3C2F2">Tip obrasca:</span>**
  Kreacioni obrazac #obrazac-kreiranja 

- **<span style="color:#F7C59F">Namena:</span>**
  Obezbeđuje da klasa ima samo jednu instancu i omogućava globalnu pristupnu tačku toj instanci.

- **<span style="color:#E8B5D0">Motivacija:</span>**
  Potrebno je da neke komponente sistema (npr. konekcija ka bazi, upravljanje fajl sistemom, video menadžeri) budu jedinstvene u okviru aplikacije — tj. da postoji samo jedan objekat te klase.

- **<span style="color:#B8E0D2">Primena:</span>**
  Kada:

  - Mora postojati tačno jedna instanca klase.
  - Mora biti dostupna globalno.
  - Klijenti treba da koriste i eventualno prošire tu instancu bez promene svog koda.

- **<span style="color:#FFF4B2">Struktura:</span>**
  Klasa ima:

  - Privatni konstruktor.
  - Privatnu statičku promenljivu koja čuva instancu.
  - Staticku metodu `getInstance()` koja vraća jedinstveni objekat.

- **<span style="color:#D8C4F2">Učesnici:</span>**

  - **Singleton:** Definiše `Instance()` metodu za pristup instanci, i kreira je ako već ne postoji.

- **<span style="color:#CCE2CB">Tok operacije:</span>**

  1. Klijent poziva `Singleton.getInstance()`
  2. Ako instanca ne postoji, kreira se.
  3. Ako postoji, vraća se postojeća instanca.

- **<span style="color:#F6C6C7">Posledice:</span>**
  
  - Centralizovana i kontrolisana instanca.
  
  - Može se kontrolisati način pristupa i kreiranja instance.
  
  - Potrebno voditi računa o: **multithreadingu**, **serialization**, **reflection**, **multiple classloaders**.
  
    [Link](./4-adapter.md)
  
    
