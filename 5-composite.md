## 🌳 Composite

- **<span style="color:#A3C2F2">Tip obrasca:</span>**
  Strukturalni obrazac #obrazac-strukture

- **<span style="color:#F7C59F">Namena:</span>**
  Predstavlja hijerarhiju celina i delova korišćenjem stablastih struktura. Omogućava klijentima da tretiraju pojedinačne objekte i njihove grupe uniformno.

- **<span style="color:#E8B5D0">Motivacija:</span>**
  Kada radimo sa objektima koji mogu biti i pojedinačni i grupisani, kod često postaje komplikovan jer klijent mora da razlikuje te dve vrste.
  Composite omogućava da svi objekti dele isti interfejs, pa klijent ne mora da zna da li ima posla sa listom ili celinom.
  Ipak, ako struktura mora da bude strogo kontrolisana, ovaj pristup zahteva dodatne provere van samog obrasca.

- **<span style="color:#B8E0D2">Primena:</span>**

  - Kada postoji hijerarhija **celina-deo**.
  - Kada klijent ne treba da pravi razliku između listova i kompozita (npr. `Line` i `Picture`).

- **<span style="color:#FFF4B2">Struktura:</span>**

  - **Component (Graphic):** Zajednički interfejs.
  - **Leaf (Line, Text, Rectangle):** Nema potomke.
  - **Composite (Picture):** Ima potomke i prosleđuje im pozive.
  - **Client:** Komunicira preko `Component` interfejsa.

- **<span style="color:#D8C4F2">Učesnici:</span>**

  - **Component:** Definiše interfejs za sve objekte.
  - **Leaf:** Osnovni grafički objekat bez dece.
  - **Composite:** Može imati decu (i druge Composite ili Leaf).
  - **Client:** Radi isključivo sa `Component` interfejsom.

- **<span style="color:#CCE2CB">Tok operacije:</span>**

  1. Klijent poziva metodu `draw()` na `Component`.
  2. Ako je `Leaf`, izvršava se direktno.
  3. Ako je `Composite`, metoda se delegira deci rekurzivno.

- **<span style="color:#F6C6C7">Posledice:</span>**
  - Olakšava dodavanje novih komponenti (Leaf/Composite).
  - Klijentski kod je jednostavan i univerzalan.
  - Može biti previše generički — teže je ograničiti koje komponente se mogu nalaziti unutar kompozita bez dodatne provere u run-time-u.
