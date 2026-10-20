# Klubbkassan

**Kassan för föreningens kiosk, café och evenemang – betala med Swish eller kontant.**

👉 **Öppna appen: [lukasgavelin.github.io/klubbkassan](https://lukasgavelin.github.io/klubbkassan/)**

Klubbkassan är en mobilanpassad kassa-webbapp på svenska för idrottsföreningar, skolklasser, loppisar och andra evenemang. Den består av en enda HTML-fil, kräver ingen server, inget konto och ingen internetanslutning – och den sparar allt lokalt i webbläsaren.

---

## Funktioner

- 🛒 **Snabb kassa** – stora varuknappar som fyller skärmen, en tumme räcker. Antal i korgen visas direkt på knappen.
- ↩️ **Ångra** – felslag ångras med ett tryck i 4 sekunder efter att en vara lagts till.
- 📱 **Swish-QR** – QR-kod med belopp, mottagare och meddelande förifyllt. Kunden skannar och godkänner.
- 💵 **Kontant** – snabbknappar för vanliga sedlar och automatisk växelräkning.
- 📊 **Försäljningsöversikt** – antal köp, total, uppdelat på Swish/kontant och per vara. Export till CSV (öppnas direkt i Excel).
- 🧾 **Menyhantering** – lägg till, redigera, ta bort och sortera varor. Färdig standardmeny med ett tryck.
- 📴 **Fungerar offline** – allt, inklusive QR-generering, är inbäddat i filen.
- 📲 **Installerbar (PWA)** – kan läggas till på hemskärmen när den publiceras på en webbplats.
- ☀️ **Byggd för utomhusbruk** – högkontrast, stora tryckytor, skärmen hålls tänd under betalning.

## Kom igång

### Snabbast: öppna webbappen
1. Gå till **https://lukasgavelin.github.io/klubbkassan/** i mobilen.
2. Följ välkomstguiden: fyll i Swish-nummer, namn på kassan och lägg upp varor.
3. Tryck **Spara och gå till kassan** – klart!
4. Valfritt: välj *Installera* (Android/Chrome) eller *Dela → Lägg till på hemskärmen* (iPhone/Safari) så fungerar appen som en vanlig app, även offline.

### Utan internet: öppna filen
Ladda ner `index.html` och öppna den direkt i webbläsaren. Allt fungerar, utom installation på hemskärmen.

### Egen publicering
Lägg upp alla filer i projektet (`index.html`, `manifest.webmanifest`, `sw.js`, `icon.svg`) på valfri statisk webbhotell, t.ex. **GitHub Pages**, **Netlify** eller **Cloudflare Pages**.

> Appen måste serveras via `https://` för att kunna installeras och cachas av service workern. Som lokal fil fungerar allt utom installationen.

## Så används den

| Steg | Gör så här |
|---|---|
| Lägg till vara | Tryck på varans knapp. Tryck flera gånger för fler. |
| Felslag | Tryck **Ångra** i raden som dyker upp längst ned. |
| Ändra/ta bort | Tryck på korgen uppe till höger → använd **+ / −** eller papperskorgen. |
| Ta betalt | Tryck den gröna knappen **Ta betalt (X kr)**. |
| Swish | Kunden skannar QR-koden. När betalningen syns i kundens app: **Klar / Ny kund**. |
| Kontant | Välj fliken **Kontant**, tryck på beloppet kunden ger → växeln visas. **Klar (kontant) / Ny kund**. |
| Ångrar sig kunden | **Avbryt** – korgen finns kvar. |
| Inställningar & statistik | Kugghjulet uppe till höger. |

### Swish-nummer
- **Föreningar/företag:** 123-nummer med 10 siffror, t.ex. `123 456 78 90`.
- **Privatpersoner:** mobilnummer som börjar på 07, t.ex. `070-123 45 67`. Även `+46 70…` accepteras.

> **Viktigt:** Klubbkassan skapar bara QR-koden – den ser inte om betalningen har gått igenom. Kontrollera alltid att kunden visar en genomförd betalning innan du trycker **Klar**.

## Data & integritet

- All data (inställningar, meny, köphistorik och pågående korg) sparas i webbläsarens `localStorage` på enheten.
- Ingenting skickas till någon server. Ingen spårning, inga cookies, inga konton.
- Data är kopplad till **enheten och webbläsaren**. Rensar du webbläsardata försvinner historiken – exportera CSV regelbundet.

## Filer

| Fil | Beskrivning |
|---|---|
| `index.html` | Hela appen: HTML, CSS, JavaScript och inbäddat QR-bibliotek. Fungerar ensam. |
| `manifest.webmanifest` | PWA-manifest (namn, färger, ikon) – används vid publicering. |
| `sw.js` | Service worker för offline-cache – används vid publicering. |
| `icon.svg` | Appikon / logga. |
| `.nojekyll` | Gör att GitHub Pages publicerar filerna som de är. |
| `docs/TEKNISK-DOKUMENTATION.md` | Teknisk dokumentation: arkitektur, datamodell, Swish-format m.m. |

## Webbläsarstöd

Moderna versioner av Chrome, Edge, Safari (iOS 15+), Firefox och Samsung Internet. Vibration och "håll skärmen tänd" används där webbläsaren stödjer det, annars ignoreras de.

## Kända begränsningar

- Priser hanteras i hela kronor.
- Å, ä och ö i betalningsmeddelandet skrivs som a/o i QR-koden (av kompatibilitetsskäl).
- Ingen synkning mellan enheter – varje telefon har sin egen historik.
- Betalningsstatus verifieras inte automatiskt (kräver Swish Handel/API med certifikat och backend).

## Licens & tredjepart

- QR-generering: [qrcodejs](https://github.com/davidshimjs/qrcodejs) 1.0.0 av Shim Sangmin, MIT-licens (inbäddad i `index.html`).
- "Swish" är ett registrerat varumärke som tillhör Getswish AB. Klubbkassan är inte ansluten till eller godkänd av Getswish AB.
