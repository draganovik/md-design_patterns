# 🌉 Bridge

- **<span style="color:#A3C2F2">Tip obrasca:</span>**
  Strukturalni obrazac #obrazac-strukture

- **<span style="color:#F7C59F">Namena:</span>**
  Razdvaja apstrakciju od implementacije kako bi mogli da evoluiraju nezavisno (smanjuje eksploziju klasa kada postoji više dimenzija varijacije).

- **<span style="color:#E8B5D0">Motivacija:</span>**
  Ako kombinujemo vrste prozora (IconWindow, DialogWindow) sa platformama (X11, Win32) dobijamo matriks klasa. Bridge uvodi sloj apstrakcije (`Window`) koji delegira operacije implementacionom interfejsu (`WindowImp`), pa se broj klasa svodi na zbir, ne proizvod.

- **<span style="color:#B8E0D2">Primena:</span>**
  - Više dimenzija varijacije (tip + platforma)
  - Runtime promene implementacije
  - Smanjenje zavisnosti klijenta od konkretnog API-ja
  - Deljenje implementacionih objekata (reference counting)
  - Migracija legacy implementacije bez menjanja apstrakcije

- **<span style="color:#FFF4B2">Struktura:</span>**
  - `Abstraction` (`Window`)
  - `RefinedAbstraction` (`IconWindow`)
  - `Implementor` (`WindowImp`)
  - `ConcreteImplementor` (`XWindowImp`, `MSWindowImp`)

- **<span style="color:#D8C4F2">Učesnici:</span>**
  - **Abstraction:** držI referencu na implementaciju
  - **RefinedAbstraction:** dodaje specifično ponašanje
  - **Implementor:** interfejs baznih operacija
  - **ConcreteImplementor:** platformske realizacije

- **<span style="color:#CCE2CB">Tok operacije:</span>**
  1. Klijent koristi `Window` API.
  2. `Window` delegira pozive na `WindowImp`.
  3. `WindowImp` izvršava platformski specifične akcije.
  4. Implementacija se može zameniti dinamički.

- **<span style="color:#F6C6C7">Posledice:</span>**
  - ✅ Nezavisna evolucija hijerarhija
  - ✅ Manje klasa (eliminacija kombinatorne eksplozije)
  - ✅ Runtime zamena implementacije
  - ✅ Sakrivanje platformskih detalja
  - ❌ Dodatna indirekcija
  - ❌ Veća početna složenost

- **<span style="color:#D4A5FF">Bridge vs Adapter:</span>**
  - Bridge je PROAKTIVAN (dizajniran unapred); Adapter REAKTIVAN (naknadna integracija).
  - Bridge razdvaja dimenzije varijacije; Adapter rešava nekompatibilne interfejse.

- **<span style="color:#D4A5FF">Primeri korišćenja:</span>**
  - GUI toolkiti
  - Graphics backends (OpenGL vs Vulkan)
  - Storage engines (lokalno vs cloud)
  - Messaging (email/SMS/push)

---

**Povezani obrasci:** [Adapter](./4-adapter.md) | [Decorator](./14-decorator.md) | [Abstract Factory](./10-abstract-factory.md)

**Prethodni:** [Factory Method](./11-factory-method.md) | **Sledeći:** [Iterator](./13-iterator.md) | **[Nazad na početak](./README.md)**