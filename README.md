# Evidencija SZB

Jednostavna web-aplikacija za profesionalne korisnike sredstava za zaštitu bilja (Hrvatska / EU).

- Unos korak po korak (prikladno za manje informatički iskusne korisnike)
- Padajući izbori (usjev, EPPO, BBCH, vrsta uporabe)
- Opcionalno skeniranje etikete (OCR)
- Preuzimanje Excel tablice usklađene sa službenim predloškom
- Podaci **samo na uređaju korisnika** – nema poslužiteljske baze

## Produkcija

Pogledajte **UPUTE-PRODUKCIJA.md** – besplatni hosting (Cloudflare Pages ili Netlify), sigurnosna zaglavlja, checklist.

## Lokalno pokretanje

Otvorite `index.html` u pregledniku **ili** (bolje) pokrenite lokalni server:

```bash
npx --yes serve .
```

Zatim otvorite prikazani `http://localhost:…` link.

## Privatnost

Aplikacija ne šalje evidenciju ni OIB na server.
Excel i OCR biblioteke učitavaju se s jsDelivr CDN-a samo kad korisnik zatraži te funkcije.
