# Royal Moonlight Arabic Wedding Invitation

Mobile-first wedding invitation website for Ayisha & Omar Sheikh, 15 November 2026, Jumeirah Al Qasr, Madinat Jumeirah, Dubai.

- `index.html`: the whole site in one file (English and Arabic, RTL), with a video opening (`assets/opening.mp4`), countdown, events, gallery, venue, travel, dress code, RSVP, wishing wall, contact and thank-you sections.
- `docs/PRD.md`: the product requirements document.

## Run locally

Open `index.html` in a browser, or serve the folder:

```
python3 -m http.server 8000
```

## Status

- RSVP and wishes run in preview mode and save only on the guest's device. The Google Sheet and Apps Script backend is the next step (`ENDPOINT` in the script).
- Opening: tapping "Open Invitation" plays `assets/opening.mp4` (6.1 s, 720x1280) and fades into the welcome screen at 4.5 s (`OPEN_FOR` in the script). If the video is missing or blocked, the page goes straight to the welcome screen.
- Butterflies: `assets/butterflies/bf1-5.webp` are cut from Agrim's reference sheet. Each is split down the body so the wings flap in 3D. As the opening fades they fly out of the envelope, two land on the welcome card, and now and then one takes off, circles and lands again.
- The current opening clip carries a third-party watermark (Lú Celebre) and needs replacing with a licensed, watermark-free version before launch.
- The screen after the opening (a grand Arabian wedding hall) is waiting for a design reference.
- Photos, families, travel, dress code and contacts are labelled placeholders. Arabic wording needs review by a fluent reader.
