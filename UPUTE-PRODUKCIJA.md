# Evidencija SZB – upute za besplatnu i sigurnu produkciju

Ova mapa sadrži sve što trebate za objavu aplikacije **besplatno** i **sigurno**.

---

## Što je uključeno

| Datoteka | Svrha |
|----------|--------|
| `index.html` | Glavna aplikacija |
| `data.js` | Liste kultura, fenofaza, vrsta uporabe |
| `manifest.json` | PWA (dodavanje na početni zaslon mobitela) |
| `netlify.toml` | Sigurnosna zaglavlja za **Netlify** |
| `_headers` | Sigurnosna zaglavlja za **Cloudflare Pages** |
| `robots.txt` | Upute za pretraživače |
| `UPUTE-PRODUKCIJA.md` | Ovaj dokument |

**Napomena:** `cultures.json`, `fenofaze.json`, `vrste.json` nisu potrebni za rad (podaci su u `data.js`). Mogu se obrisati prije uploada.

---

## Zašto je ovo sigurno (u okviru statičke aplikacije)

1. **Nema servera s vašim podacima** – OIB, primjene i Excel ostaju u pregledniku korisnika (`localStorage`).
2. **HTTPS** – Netlify i Cloudflare automatski daju SSL certifikat.
3. **Sigurnosna zaglavlja** – sprječavaju ugradnju u tuđi iframe (`X-Frame-Options`), pogrešne tipove datoteka, nepotrebne dozvole mikrofona/lokacije.
4. **CSP** – ograničava skripte na vlastitu domenu + pouzdani CDN (jsDelivr) za Excel i OCR.
5. **Kamera** – dozvoljena samo na istoj domeni, samo kad korisnik sam odabere fotografiju.

**Bitno:** Aplikacija **nije** zamjena za službeni sustav (FIS / ePoljoprivreda). Korisnik je odgovoran za točnost i predaju evidencije.

---

## Opcija 1: Cloudflare Pages (preporučeno – besplatno)

### Prednosti
- Brzo, globalni CDN, automatski HTTPS
- Velikodusan besplatni plan
- Jednostavan upload

### Koraci

1. Idite na **https://dash.cloudflare.com** i registrirajte se (besplatno).
2. U izborniku: **Workers & Pages** → **Create** → **Pages** → **Upload assets**.
3. Nazovite projekt npr. `evidencija-szb`.
4. Povucite **cijeli sadržaj** ove mape (ili zip raspakiran) u upload.
5. Kliknite **Deploy**.
6. Dobijete adresu tipa:  
   `https://evidencija-szb.pages.dev`

### Vlastita domena (opcionalno)
- U projektu: **Custom domains** → dodajte npr. `evidencija.vasedomena.hr`
- Cloudflare vodi kroz DNS (besplatno ako domena već koristi Cloudflare DNS)

### Ažuriranje
- Ponovno Upload assets s novom verzijom datoteka, ili povežite GitHub za automatski deploy.

---

## Opcija 2: Netlify (besplatno)

1. Idite na **https://app.netlify.com** i registrirajte se.
2. Na početnoj: **Sites** → **Add new site** → **Deploy manually**.
3. Povucite mapu s datotekama (ili zip).
4. Dobijete adresu tipa:  
   `https://random-name.netlify.app`
5. **Site settings** → **Domain management** → promijenite ime ili dodajte vlastitu domenu.

`netlify.toml` se automatski primijeni (sigurnosna zaglavlja).

---

## Opcija 3: GitHub Pages (besplatno)

1. Napravite javni ili privatni repozitorij na GitHubu.
2. Uploadajte datoteke (bez netlify.toml ako želite; `_headers` GitHub Pages **ne** čita – zaglavlja su slabija).
3. **Settings** → **Pages** → Source: main branch / root.
4. Adresa: `https://korisnik.github.io/ime-repozitorija/`

**Napomena:** GitHub Pages nema lako `_headers` / CSP kao Cloudflare/Netlify. Za bolju sigurnost preferirajte Cloudflare ili Netlify.

---

## Checklist prije nego što podijelite link

- [ ] Otvorite `https://…` na **Android** (Chrome) i **iPhone** (Safari)
- [ ] Unesite testni zapis i preuzmite Excel
- [ ] Provjerite da Excel ima obrube i hrvatski datum
- [ ] Provjerite da se u Info / početnom ekranu vidi napomena o privatnosti
- [ ] (Opcionalno) Dodajte stranicu na početni zaslon (PWA)
- [ ] Napravite kratku PDF/uputu za poljoprivrednike (1 stranica)

---

## Kako korisnici trebaju koristiti aplikaciju

1. Otvoriti **link** koji im date (ne zip s računala).
2. Po želji: „Dodaj na početni zaslon“.
3. Unijeti ime (i OIB po želji).
4. Unositi primjene tijekom godine.
5. **Preuzeti Excel** nakon unosa / na kraju sezone – to je njihova službena kopija.
6. Čuvati Excel na računalu / USB-u / oblaku (njihova odgovornost).

Ako obrišu podatke preglednika, lokalni unos nestaje – zato je Excel obavezan korak.

---

## Što **ne** raditi

- Ne hostajte preko `http://` (bez S) – kamera i povjerenje pate.
- Ne tražite od korisnika da šalju OIB e-mailom „za test“.
- Ne tvrđite da je aplikacija „službena“ ako nije odobrena od Ministarstva.
- Ne stavljajte API ključeve u kod (ova verzija ih i nema).

---

## Troškovi

| Stavka | Cijena |
|--------|--------|
| Cloudflare Pages / Netlify | **0 €** (besplatni plan) |
| Domenа `.hr` (opcionalno) | cca 10–15 € / godina |
| SSL | **0 €** (uključen) |
| Backend / baza | **nije potreban** |

---

## Ako želite kasnije „pravi“ sustav

- Prijava preko **NIAS / e-Građani**
- Spremanje na server
- Izravni prijenos u FIS  

to zahtijeva razvoj backend sustava, ugovore i usklađenost s GDPR-om – to **nije** dio ovog paketa.

---

## Podrška korisnicima (kratki tekst za dijeljenje)

> Evidencija SZB – jednostavan unos primjene sredstava za zaštitu bilja.  
> Otvorite: **https://VAŠA-ADRESA**  
> Podaci ostaju na vašem telefonu. Na kraju preuzmite Excel datoteku.  
> Za pitanja: [vaš kontakt]

---

## Brzi start (5 minuta)

1. Otvorite https://dash.cloudflare.com → Pages → Upload assets  
2. Uploadajte ovu mapu  
3. Kopirajte dobiveni `https://….pages.dev` link  
4. Pošaljite ga sebi na mobitel i isprobajte  
5. Ako radi – dijelite s korisnicima  

Gotovo.
