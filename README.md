# Royal Moonlight Arabic Wedding Invitation

Mobile-first wedding invitation website for Ayisha & Omar Sheikh, 15 November 2026, Jumeirah Al Qasr, Madinat Jumeirah, Dubai.

- `index.html`: the whole site in one file (English and Arabic, RTL), with an envelope-opening cover, countdown, events, gallery, venue, travel, dress code, RSVP, wishing wall, contact and thank-you sections.
- `docs/PRD.md`: the product requirements document.

## Run locally

Open `index.html` in a browser, or serve the folder:

```
python3 -m http.server 8000
```

## Status

- RSVP and wishes run in preview mode and save only on the guest's device. The Google Sheet and Apps Script backend is the next step (`ENDPOINT` in the script).
- The screen after the opening (a grand Arabian wedding hall) is waiting for a design reference.
- Photos, families, travel, dress code and contacts are labelled placeholders. Arabic wording needs review by a fluent reader.
