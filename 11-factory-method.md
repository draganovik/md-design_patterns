## 🏭 Factory Method

- **<span style="color:#A3C2F2">Tip obrasca:</span>**  
  Kreacioni obrazac #obrazac-kreiranja

- **<span style="color:#F7C59F">Namena:</span>**  
  Definiše interfejs za kreiranje objekata, ali konkretna klasa koja će biti instancirana je delegirana podklasama.

- **<span style="color:#E8B5D0">Motivacija:</span>**  
  Radni okvir zna kada treba da napravi objekat, ali ne zna koji konkretan tip.  
  Npr. `Application` zna kada da kreira `Document`, ali ne zna da li je to `DrawingDocument` ili neki drugi — to zna samo klijent (`MyApplication`) koji implementira `CreateDocument` metod.

- **<span style="color:#B8E0D2">Primena:</span>**  
  - Klasa ne može da predvidi koji objekat treba da kreira  
  - Klasa želi da njene podklase specificiraju koji objekti se kreiraju  
  - Klasa delegira odgovornost za instanciranje pomoćnim klasama

- **<span style="color:#FFF4B2">Struktura:</span>**  
  - **Product (Document):** Interfejs za objekat koji se kreira  
  - **ConcreteProduct (MyDocument):** Implementacija `Product` interfejsa  
  - **Creator (Application):** Deklariše `Factory Method` koji vraća `Product`  
  - **ConcreteCreator (MyApplication):** Implementira `Factory Method`

- **<span style="color:#D8C4F2">Učesnici:</span>**  
  - **Product**  
  - **ConcreteProduct**  
  - **Creator**  
  - **ConcreteCreator**

- **<span style="color:#CCE2CB">Tok operacije:</span>**  
  1. Klijent poziva metod `CreateDocument()` u `Application`  
  2. `Application` poziva `Factory Method`  
  3. `Factory Method` implementirana u `MyApplication` vraća konkretnu instancu  
  4. `Application` koristi objekat bez poznavanja njegove konkretne klase

- **<span style="color:#F6C6C7">Posledice:</span>**  
  - Olakšava dodavanje novih proizvoda bez menjanja radnog okvira  
  - Klijent koristi samo interfejs `Product` – niska sprega  
  - Nedostatak: klijent mora naslediti `Creator` klasu da bi mogao definisati svoj `Factory Method`