## 🌳 Composite

- **<span style="color:#A3C2F2">Tip obrasca:</span>**
  Strukturalni obrazac #obrazac-strukture

- **<span style="color:#F7C59F">Namena:</span>**
  Predstavlja hijerarhiju celina i delova korišćenjem stablastih struktura. Omogućava klijentima da tretiraju pojedinačne objekte i njihove grupe uniformno.

- **<span style="color:#E8B5D0">Motivacija:</span>**
  Kada radimo sa objektima koji mogu biti i pojedinačni i grupisani (npr. grafički elementi: linija je leaf, slika je kompozit linija, pravougaonika, teksta), kod često postaje komplikovan jer klijent mora da razlikuje te dve vrste. Composite omogućava da svi objekti dele isti interfejs, pa klijent ne mora da zna da li ima posla sa listom ili celinom. Ovo olakšava kod jer se iste operacije (npr. `draw()`) mogu primeniti na bilo kom nivou hijerarhije.

- **<span style="color:#B8E0D2">Primena:</span>**
  - Kada postoji hijerarhija **celina-deo** (part-whole hierarchy)
  - Kada klijent ne treba da pravi razliku između listova i kompozita
  - Kada se želi reprezentovati struktura stabla (npr. fajl sistem, GUI komponente)
  - Kada operacije treba rekurzivno primeniti na celu strukturu

- **<span style="color:#FFF4B2">Struktura:</span>**
  - **Component (Graphic):** Zajednički interfejs za sve objekte
  - **Leaf (Line, Text, Rectangle):** Osnovni elementi bez potomaka
  - **Composite (Picture):** Ima potomke i prosleđuje im pozive
  - **Client:** Komunicira isključivo preko `Component` interfejsa

- **<span style="color:#D8C4F2">Učesnici:</span>**
  - **Component:** Definiše interfejs za sve objekte u kompoziciji
  - **Leaf:** Osnovni grafički objekat bez dece, implementira osnovne operacije
  - **Composite:** Može imati decu (druge Composite ili Leaf objekte), delegira pozive deci
  - **Client:** Radi isključivo sa `Component` interfejsom, ne zna razliku između Leaf i Composite

- **<span style="color:#CCE2CB">Tok operacije:</span>**
  1. Klijent poziva metodu `draw()` na `Component`
  2. Ako je `Leaf`, izvršava se direktno
  3. Ako je `Composite`, metoda se delegira svim potomcima rekurzivno
  4. Svaki potomak obrađuje poziv na isti način

- **<span style="color:#F6C6C7">Posledice:</span>**
  - ✅ **Jednostavan klijentski kod:** Uniformno tretiranje objekata
  - ✅ **Lako dodavanje komponenti:** Novi tipovi Leaf/Composite se dodaju bez menjanja koda
  - ✅ **Fleksibilnost:** Strukture se mogu динамически graditi i menjati
  - ❌ **Previše generički:** Teže je ograničiti koji tipovi mogu biti deca
  - ❌ **Runtime provere:** Neke provere se moraju raditi u runtime-u, ne u compile-time
  - ❌ **Performanse:** Rekurzivne operacije mogu biti skupe za duboke hijerarhije

- **<span style="color:#D4A5FF">Dizajnerske odluke:</span>**
  - **Gde definisati child operacije:** U Component (transparentnost) ili samo u Composite (sigurnost)?
  - **Child ordering:** Da li Composite mora da održava redosled dece?
  - **Caching:** Da li Composite cache-uje rezultate operacija?
  - **Parent reference:** Da li čvorovi znaju za svog roditelja (Chain of Responsibility)?
  - **Sharing:** Može li isti objekat biti u više kompozita? (videti [Flyweight](https://en.wikipedia.org/wiki/Flyweight_pattern))

- **<span style="color:#D4A5FF">Primeri korišćenja:</span>**
  - **Fajl sistemi:** Folderi (Composite) i fajlovi (Leaf)
  - **GUI komponente:** Paneli, prozori sadrže dugmad, labele
  - **Grafički editori:** Grupe oblika, pojedinačni oblici
  - **Organizacione strukture:** Kompanije, odseci, zaposleni

---

**Povezani obrasci:** [Iterator](./13-iterator.md) | [Visitor](./19-visitor.md) | [Decorator](./14-decorator.md)

**Prethodni:** [Adapter](./4-adapter.md) | **Sledeći:** [Observer](./6-observer.md) | **[Nazad na početak](./README.md)**
