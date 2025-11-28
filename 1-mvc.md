## 🧭 Model–View–Controller
#obrazac-arhitekture

- **<span style="color:#A3C2F2">Uvod:</span>**  
  MVC je arhitektonski obrazac koji se koristi za organizaciju aplikacija sa korisničkim interfejsom. Uveden je kako bi se smanjila međuzavisnost između različitih delova sistema i omogućila nezavisna izmena istih.

- **<span style="color:#E8B5D0">Struktura:</span>**  
  - **Model:**  
    - Sadrži podatke i poslovnu logiku aplikacije.  
    - Odgovoran je za čuvanje stanja i izvršavanje operacija nad podacima.  
    - Ne zna ništa o prikazu (View) ni o korisničkom unosu (Controller).
  
  - **View:**  
    - Vizuelni sloj koji prikazuje podatke korisniku.  
    - Prati promene u Modelu i osvežava prikaz u skladu sa njima.  
    - Ne komunicira direktno sa Modelom, već kroz posmatranje ili posredovanje.

  - **Controller:**  
    - Prima korisničke događaje (klikovi, unos teksta...).  
    - Prepoznaje korisničku nameru i ažurira Model.  
    - Može uticati na to koji View će se prikazati korisniku.

- **<span style="color:#F6C6C7">Prednosti:</span>**  
  - **Odvajanje odgovornosti:** logika, prikaz i interakcija su jasno razdvojeni.  
  - **Olakšano testiranje:** omogućava izolovano testiranje poslovne logike.  
  - **Fleksibilnost UI-ja:** korisnički interfejs se može menjati bez izmene Modela.  
  - **Višestruki prikazi:** moguće je imati više View-eva nad istim Modelom.  
  - **Timovi mogu raditi paralelno:** olakšava kolaboraciju među različitim ulogama u razvoju.
