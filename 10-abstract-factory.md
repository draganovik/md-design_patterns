# 🏢 Abstract Factory

- **<span style="color:#A3C2F2">Tip obrasca:</span>**
  Kreacioni obrazac #obrazac-kreiranja

- **<span style="color:#F7C59F">Namena:</span>**
  Pruža interfejs za kreiranje PORODICE međusobno povezanih ili međusobno kompatibilnih objekata bez navođenja njihovih konkretnih klasa.

- **<span style="color:#E8B5D0">Motivacija:</span>**
  UI okruženja ili platforme (Motif, Windows, Mac, Web) zahtevaju konzistentan izgled komponenti. Umesto da klijent zna konkretne klase za svaki stil, dobija apstraktnu fabriku koja generiše sve potrebne proizvode iz iste porodice. Zamena teme postaje promena jedne fabrike.

- **<span style="color:#B8E0D2">Primena:</span>**
  - Konzistentan skup UI komponenti (dugme, prozor, scrollbar)
  - Porodice konektora ka različitim bazama
  - Set servisnih objekata za određeno okruženje (cloud vendor)
  - Test stub vs real implementation porodice
  - Multi-tenant aplikacije sa različitim brendingom

- **<span style="color:#FFF4B2">Struktura:</span>**
  - `AbstractFactory` – deklaracija metoda (npr. `createButton()`)
  - `ConcreteFactory` – proizvodi konkretne varijante
  - `AbstractProduct` – interfejs svakog tipa proizvoda
  - `ConcreteProduct` – konkretna realizacija
  - `Client` – koristi isključivo apstraktne interfejse

- **<span style="color:#D8C4F2">Učesnici:</span>**
  - **AbstractFactory:** skup fabričkih metoda
  - **ConcreteFactory:** implementacije za stil/platformu
  - **AbstractProduct:** zajednički interfejs proizvoda
  - **ConcreteProduct:** specifična implementacija porodice
  - **Client:** ostaje neznalica konkretnih klasa

- **<span style="color:#CCE2CB">Tok operacije:</span>**
  1. Klijent bira konkretnu fabriku (npr. `WindowsWidgetFactory`).
  2. Poziva fabričke metode za kreiranje potrebnih elemenata.
  3. Dobija proizvode kroz apstraktne interfejse.
  4. Svi proizvodi međusobno konzistentni.
  5. Zamena teme = zamena fabrike.

- **<span style="color:#F6C6C7">Posledice:</span>**
  - ✅ Izoluje konkretne klase
  - ✅ Jednostavna zamena čitave porodice
  - ✅ Garantuje konzistentnost
  - ✅ Centralizovano instanciranje
  - ❌ Dodavanje novog tipa proizvoda menja sve fabrike
  - ❌ Veći broj interfejsa/klasa
  - ❌ Potencijal over-engineering za male sisteme

- **<span style="color:#D4A5FF">Abstract Factory vs Factory Method:</span>**
  - Abstract Factory koristi više Factory Method-a.
  - Factory Method rešava kreiranje jednog proizvoda; Abstract Factory grupe proizvoda.
  - Factory Method oslanja se na nasleđivanje, Abstract Factory na kompoziciju.

- **<span style="color:#D4A5FF">Varijante:</span>**
  - Implementacija preko **Factory Method**
  - Implementacija preko **Prototype** (kloniranje umesto konstrukcije)
  - **Registry konfiguracija** (učitavanje porodica iz konfiguracije)
  - Kombinacija sa **Singleton** za jedinstvenu fabriku po procesu.

- **<span style="color:#D4A5FF">Primeri korišćenja:</span>**
  - UI toolkiti (Swing Look & Feel, Android themes)
  - Cloud provider adapteri (AWSFactory, AzureFactory)
  - Database driver setovi
  - PDF/HTML/Markdown generator porodice elemenata
  - Game engine: različiti skin paketi.

---

**Povezani obrasci:** [Factory Method](./11-factory-method.md) | [Builder](./9-builder.md) | [Prototype](./7-prototype.md)

**Prethodni:** [Builder](./9-builder.md) | **Sledeći:** [Factory Method](./11-factory-method.md) | **[Nazad na početak](./README.md)**