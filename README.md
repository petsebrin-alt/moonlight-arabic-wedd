# Royal Moonlight Arabic Wedding Invitation

Mobile-first wedding invitation website for Ayisha & Omar Sheikh, 15 November 2026, Jumeirah Al Qasr, Madinat Jumeirah, Dubai.

- `index.html`: the whole site in one file (English and Arabic, RTL), with an envelope opening, countdown, events, gallery, venue, travel, dress code, RSVP, wishing wall, contact and thank-you sections.
- `docs/PRD.md`: the product requirements document.

## Run locally

Open `index.html` in a browser, or serve the folder:

```
python3 -m http.server 8000
```

## Status

- RSVP and wishes run in preview mode and save only on the guest's device. The Google Sheet and Apps Script backend is the next step (`ENDPOINT` in the script).
- Opening: Agrim's navy envelope with the gold wax seal (`assets/opening/`), real gold butterflies and a blue-and-white flower border. Tapping the seal folds the flap back, the invitation card rises, butterflies fly out, and the page fades into the welcome screen. The seal shows the letter "L" from the reference photo; swap `assets/opening/seal.webp` for an "A & O" seal if wanted.
- The screen after the opening (a grand Arabian wedding hall) is waiting for a design reference.
- Photos, families, travel, dress code and contacts are labelled placeholders. Arabic wording needs review by a fluent reader.
