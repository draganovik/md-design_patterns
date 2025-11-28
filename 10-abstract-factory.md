## 🏢 Abstract Factory

- **<span style="color:#A3C2F2">Tip obrasca:</span>**  
  Kreacioni obrazac #obrazac-kreiranja

- **<span style="color:#F7C59F">Namena:</span>**  
  Pruža interfejs za kreiranje porodice međusobno povezanih objekata (proizvoda), bez navođenja konkretnih klasa.

- **<span style="color:#E8B5D0">Motivacija:</span>**  
  Kod UI-a želimo podršku za više „look and feel“ sistema bez menjanja klijentskog koda.  
  `WidgetFactory` interfejs definiše metode za pravljenje `ScrollBar`, `Window`, itd.  
  `MotifWidgetFactory` i `PMWidgetFactory` implementiraju konkretne proizvode. Klijent koristi samo `WidgetFactory`, bez znanja o konkretnim klasama.

- **<span style="color:#B8E0D2">Primena:</span>**  
  - Sistem mora biti nezavistan od konkretnog mehanizma instanciranja  
  - Sistem treba da koristi **porodicu povezanih proizvoda**  
  - Potrebna je konzistentnost među proizvodima  
  - Klijent treba da koristi samo interfejse – ne i konkretne klase

- **<span style="color:#FFF4B2">Struktura:</span>**  
  - **AbstractFactory (WidgetFactory):** Interfejs za kreiranje proizvoda  
  - **ConcreteFactory (MotifFactory, PMFactory):** Pravi konkretne proizvode  
  - **AbstractProduct (ScrollBar, Window):** Interfejsi za proizvode  
  - **ConcreteProduct (MotifScrollBar, PMScrollBar):** Implementacije  
  - **Client:** Koristi samo apstraktne interfejse

- **<span style="color:#D8C4F2">Učesnici:</span>**  
  - **AbstractFactory**  
  - **ConcreteFactory**  
  - **AbstractProduct**  
  - **ConcreteProduct**  
  - **Client**

- **<span style="color:#CCE2CB">Tok operacije:</span>**  
  1. Klijent instancira konkretnu fabriku (npr. `MotifWidgetFactory`)  
  2. Poziva metode za pravljenje proizvoda (`CreateScrollBar`, `CreateWindow`)  
  3. Dobija konkretne proizvode kao apstraktne interfejse  
  4. Klijent ostaje nezavistan od konkretnog look & feel sistema

- **<span style="color:#F6C6C7">Posledice:</span>**  
  - Izoluje konkretne klase proizvoda  
  - Lako se zamenjuje čitava porodica proizvoda  
  - Obezbeđuje konzistentnost među proizvodima  
  - Teško je dodati novi proizvod – zahteva izmene svih fabrika