# Royal Moonlight Arabic Wedding Invitation

Mobile-first wedding invitation website for Ayisha & Omar Sheikh, 15 November 2026, Jumeirah Al Qasr, Madinat Jumeirah, Dubai.

- `index.html`: the whole site in one file (English, Urdu (right to left, Nastaliq) and Hindi), with an envelope opening, countdown, events, gallery, venue, travel, dress code, RSVP, wishing wall, contact and thank-you sections.
- `docs/PRD.md`: the product requirements document.

## Views

- On a phone the invitation fills the screen.
- On a computer (760 px wide or more) it is shown inside an iPhone 17 Pro Max frame (440 x 956 screen, Deep Blue), sized to fit the whole window, on a moonlit royal-blue sky with twinkling stars, a crescent moon, shooting stars, falling gold sparkles and a mosque skyline. Add `?full=1` to the address to see the plain page.
- The whole site uses blues only: navy sections and pale moonlight-blue card sections, with gold accents.

## Run locally

Open `index.html` in a browser, or serve the folder:

```
python3 -m http.server 8000
```

## Status

- RSVP and wishes run in preview mode and save only on the guest's device. The Google Sheet and Apps Script backend is the next step (`ENDPOINT` in the script).
- Opening: Agrim's navy envelope with the gold wax seal (`assets/opening/`), real gold butterflies and a white lily-and-rose bouquet running edge to edge along the bottom. Tapping the seal folds the flap back, the invitation card rises, butterflies fly out, and the page fades into the welcome screen. The seal shows the letter "L" from the reference photo; swap `assets/opening/seal.webp` for an "A & O" seal if wanted.
- Welcome and countdown follow Agrim's Figma "Group 240" (`assets/welcome/`): drapes on both sides, a small crescent moon rising behind the hills and a lantern-lit floor (the tent and the moon's blur were removed from the background). The Bismillah is written in Urdu, then "Dear Guest", the names and the walima invitation write themselves in while the curtains sway, gold glitter falls and three butterflies keep flying around. The client's couple photo stands in the bottom-right corner beside the glass "Tap here" button, and the bride's lehenga sways. "Tap here" opens the rest of the invitation at the Reveal Date card (light blush pink melting into champagne gold, a small glowing "Reveal Date" heading): guests scratch the three softly beating, gold-glowing hearts (or tap Reveal Date) to uncover 15 November 2026, with confetti, followed by the live countdown in gold wreaths.
- Meet Our Families follows Agrim's reference: a moonlit card for the groom's family and one for the bride's, each photo in a gold Islamic arch with jasmine. As each card scrolls into view its gold arch lights up from both sides to the tip, then keeps a soft glow with sparks of light rising up the frame, and the card's border glows. The photos in `assets/families/` are the client's sample families (the arch and flowers are part of each image; the glow traces that arch), with sample parents' names (Mr. Abdullah & Mrs. Khadija Sheikh; Mr. Yusuf & Mrs. Fatima Al Hashimi) to replace with the real ones.
- Wedding Celebrations: a white section with hanging birdcage lanterns and Edison pendants (`assets/events/`), and for each of Haldi, Mehendi, Nikah, Walima and Reception a couple photo with its flowers and lanterns, in a gold frame (from Agrim's reference; Reception is the welcome couple in front of the invitation's own lantern-lit hall), with a champagne-gold board overlapping it with the date, time, venue, a short line and a glowing "View location" button that opens Google Maps. As you scroll, each board and couple slide in from opposite edges and meet in the middle, alternating sides. The schedule is a sample to confirm (only Walima's 15 November, 6:30 PM at Jumeirah Al Qasr comes from the original brief).
- Gallery photos, travel, dress code and contacts are labelled placeholders. Urdu and Hindi wording needs review by fluent readers.
