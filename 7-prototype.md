## 🤖 Prototype

- **<span style="color:#A3C2F2">Tip obrasca:</span>**
  Kreacioni obrazac #obrazac-kreiranja 

- **<span style="color:#F7C59F">Namena:</span>**
  Omogućava kreiranje novih objekata kloniranjem postojećih (prototipova), bez potrebe za pozivanjem konstruktora.

- **<span style="color:#E8B5D0">Motivacija:</span>**
  Kada želimo da fleksibilno kreiramo nove objekte bez nasleđivanja, možemo jednostavno klonirati već pripremljene instance sa zadatim stanjem.
  To smanjuje potrebu za mnogobrojnim podklasama i omogućava korisniku da sam definiše "šablon" koji treba da se klonira.

- **<span style="color:#B8E0D2">Primena:</span>**

  - Kada tip objekta nije poznat do runtime-a.
  - Kada bi nasleđivanje stvorilo previše klasa koje se razlikuju samo po konfiguraciji.
  - Kada postoji ograničen broj kombinacija stanja objekta.

- **<span style="color:#FFF4B2">Struktura:</span>**

  - `Prototype`: interfejs sa metodom `clone()`
  - `ConcretePrototype`: implementira `clone()`
  - `Client`: klonira objekat preko prototipa

- **<span style="color:#D8C4F2">Učesnici:</span>**

  - **Prototype:**
    Definiše interfejs za kloniranje objekta (npr. metod `clone()` ili `copy()`).
  - **ConcretePrototype:**
    Implementira operaciju kloniranja. Svaka konkretna klasa zna kako da napravi svoju kopiju.
  - **Client:**
    Ne kreira objekte direktno, već traži od prototipa da se klonira. Time je nezavistan od konkretnih klasa proizvoda.

- **<span style="color:#CCE2CB">Tok operacije:</span>**

  1. Klijent poziva `clone()` nad prototipom.
  2. Novi objekat se stvara kopiranjem postojećeg.
  3. Objekat se koristi ili dodaje u strukturu.

- **<span style="color:#F6C6C7">Posledice:</span>**
  - Omogućava dodavanje novih tipova objekata u sistem u runtime-u.
  - Fleksibilno kreiranje objekata bez čvrstog povezivanja sa njihovim klasama.
  - Klonirani objekti zadržavaju stanje prototipa (potrebna pažnja kod dubokih kopija).
