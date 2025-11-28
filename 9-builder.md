## 🏗️ Builder

- **<span style="color:#A3C2F2">Tip obrasca:</span>**  
  Kreacioni obrazac #obrazac-kreiranja

- **<span style="color:#F7C59F">Namena:</span>**  
  Razdvaja konstrukciju kompleksnog objekta od njegove reprezentacije, tako da isti proces građenja može kreirati različite reprezentacije.

- **<span style="color:#E8B5D0">Motivacija:</span>**  
  Klasa `RTFReader` mora moći da parsira RTF i konvertuje u različite formate (ASCII, TeX, Widget). Umesto da `RTFReader` zna kako da pravi svaki format, koristi objekat `TextConverter` (builder), koji gradi rezultat dok `RTFReader` prolazi kroz dokument. Na taj način je lako dodati nove reprezentacije.

- **<span style="color:#B8E0D2">Primena:</span>**  
  - Kada se konstrukcija kompleksnog objekta mora odvijati nezavisno od njegove strukture i komponenti.  
  - Kada treba kreirati više različitih verzija istog objekta.  
  - Kada se objekat gradi postepeno i ima varijacije u konfiguraciji.

- **<span style="color:#FFF4B2">Struktura:</span>**  
  - **Builder:** Apstraktni interfejs za kreiranje delova  
  - **ConcreteBuilder:** Konkretnu implementaciju građenja (npr. `TextWidgetConverter`)  
  - **Director:** Kontroliše redosled građenja (`RTFReader`)  
  - **Product:** Rezultujući kompleksan objekat (npr. `TeXText`, `ASCIIText`)

- **<span style="color:#D8C4F2">Učesnici:</span>**  
  - **Builder:** Definiše metode za građenje delova  
  - **ConcreteBuilder:** Sklapa delove u celinu  
  - **Director:** Upravlja procesom građenja  
  - **Product:** Gotov objekat koji se dobija kao rezultat

- **<span style="color:#CCE2CB">Tok operacije:</span>**  
  1. Klijent instancira `ConcreteBuilder`  
  2. Prosleđuje ga `Director`-u  
  3. `Director` poziva metode u tačnom redosledu  
  4. `ConcreteBuilder` gradi i vraća `Product`

- **<span style="color:#F6C6C7">Posledice:</span>**  
  - Omogućava promenu unutrašnje strukture proizvoda bez promene građenja.  
  - Povećava modularnost i fleksibilnost sistema.  
  - Daje finu kontrolu nad redosledom i načinom građenja.  
  - Odvaja konstrukciju od reprezentacije – olakšava promene i testiranje.