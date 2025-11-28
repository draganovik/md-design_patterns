## 🎄 Decorator

- **<span style="color:#A3C2F2">Tip obrasca:</span>**  
  Strukturalni (structural) #obrazac-strukture 

- **<span style="color:#F7C59F">Namena:</span>**  
  Dinamičko dodavanje odgovornosti objektu. Nudi fleksibilnu alternativu nasleđivanju radi proširenja funkcionalnosti.

- **<span style="color:#E8B5D0">Motivacija:</span>**  
  Kada je potrebno dodati osobinu samo jednom objektu, a ne celoj klasi.  
  Npr. `TextView` može biti obogaćen `ScrollDecorator`-om i `BorderDecorator`-om bez menjanja osnovne klase.  
  Dekorater se ugnežđuje oko komponente, propušta pozive, i izvršava dodatne radnje pre/posle njih.  

- **<span style="color:#B8E0D2">Primena:</span>**  
  - Dinamičko i transparentno dodavanje odgovornosti pojedinačnim objektima  
  - Proširenja koja je moguće ukloniti (undo)  
  - Kada je nasleđivanje nepraktično ili previše rigidno

- **<span style="color:#FFF4B2">Struktura:</span>**  
  - **Component:** Interfejs (`VisualComponent`)  
  - **ConcreteComponent:** Osnovni objekat (`TextView`)  
  - **Decorator:** Ima referencu na `Component` i isti interfejs  
  - **ConcreteDecorator:** Dodaje funkcionalnost (`ScrollDecorator`, `BorderDecorator`)

- **<span style="color:#D8C4F2">Učesnici:</span>**  
  - `VisualComponent` (interfejs)  
  - `TextView` (ConcreteComponent)  
  - `Decorator` (apstraktni dekorater)  
  - `ScrollDecorator`, `BorderDecorator` (ConcreteDecorator)

- **<span style="color:#CCE2CB">Tok operacije:</span>**  
  1. Klijent koristi komponentu kao `VisualComponent`  
  2. Omotava je dekoraterima  
  3. Dekorateri pozivaju `Draw()` komponente i dodaju ponašanje  
  4. Moguće više dekoratera u slojevima (rekurzivno)

- **<span style="color:#F6C6C7">Posledice:</span>**  
  - Fleksibilnije od nasleđivanja – moguće je menjati ponašanje u toku izvršavanja  
  - Omogućava kombinovanje odgovornosti  
  - Smanjuje potrebu za mnoštvom podklasa (`BorderedScrollableTextView`)  
  - Sistemi s dekoraterima imaju više malih objekata koji mogu otežati debagovanje  
  - Dekorisani objekat i original nisu identični po tipu (što može uticati na poređenje)