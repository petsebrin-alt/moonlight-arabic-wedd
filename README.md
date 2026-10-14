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
- Welcome and countdown follow Agrim's Figma "Group 240" (`assets/welcome/`): a carved flower arch framing a palace at dusk (`arch.webp`, with the moon moved up under the arch's point; `arch-floor.webp` is a soft reflection that fills taller screens), with the hanging lanterns kept. The Urdu Bismillah starts inside the arch's sky, then "Dear Guest", the names and the walima invitation write themselves in while the two flower garlands sway in the breeze, gold glitter falls, and small butterflies flit between the flowers (garlands, rose-covered pillars and the flower beds), resting on them now and then. The client's couple photo stands in the bottom-right corner beside the glass "Tap here" button, and the bride's lehenga sways. "Tap here" opens the rest of the invitation at the Reveal Date card (light blush pink melting into champagne gold, a small glowing "Reveal Date" heading): guests scratch the three softly beating, gold-glowing hearts (or tap Reveal Date) to uncover 15 November 2026, with confetti, followed by the live countdown in gold wreaths.
- Meet Our Families follows Agrim's reference: a moonlit card for the groom's family and one for the bride's, each photo in a gold Islamic arch with jasmine. As each card scrolls into view its gold arch lights up from both sides to the tip, then keeps a soft glow with sparks of light rising up the frame, and the card's border glows. The photos in `assets/families/` are the client's sample families (the arch and flowers are part of each image; the glow traces that arch), with sample parents' names (Mr. Abdullah & Mrs. Khadija Sheikh; Mr. Yusuf & Mrs. Fatima Al Hashimi) to replace with the real ones.
- Wedding Celebrations follow Agrim's template: a moonlit navy section with hanging brass lanterns, and for each of Haldi, Mehendi, Nikah, Walima and Reception a photo (`assets/events/`, from Agrim's reference; Reception is the welcome couple in front of the invitation's own lantern-lit hall) beside a champagne-gold board with the date, time, venue, a short line and a glowing "View location" button that opens Google Maps, alternating sides, with gold dividers between them. Each celebration starts hidden behind two pastel clouds (`cloud-1..3.webp`, drawn for this site) that part to the edges as you scroll to it, following the reference video; scrolling back up closes them. With reduced motion there are no clouds. The schedule is a sample to confirm (only Walima's 15 November, 6:30 PM at Jumeirah Al Qasr comes from the original brief).
- Moments gallery: seven couple photos (`assets/gallery/`) on a scroll-driven orbit, after Agrim's Framer reference: the stage pins under the top bar, and scrolling turns the orbit so each photo comes to the front in turn (scrolling up turns it back), and a gold flower frame below (`assets/gallery/story-frame.webp`, marble background removed) pops up with that photo's chapter of their story (met, friends, best friends, falling in love, love in bloom, engaged, forever begins; the years are samples to confirm); tapping a photo opens it full size with its chapter. With reduced motion it is a plain two-column gallery. The photos are samples; some carry their sources' watermarks, so swap in the couple's own photos before launch.
- Venue: a palace photo in the gold arch (`assets/venue/`, a sample image to replace with the real venue), with a few small fireworks bursting in its sky, left and right, as it scrolls into view (and now and then while it stays on screen). The Get Directions button warms from gold to a gold-and-blush glow on hover (or tap), and Copy Address fills with light blue.
- Flower bush: a low, dense bush of white roses and peonies (`assets/flowers/`, the client's bouquet flowers cut along their real petal edges, over a mound of fresh leaves) in three overlapping rows on the wave between Dress Code and RSVP, and a mirrored one on the wave between Events and Gallery. As it scrolls into view the leaves rise, then the flowers open like a time-lapse (bud, half-open rose, full bloom), rippling through the rows; scrolling back closes them into buds again. With reduced motion they are simply in bloom.
- Travel, dress code and contacts are labelled placeholders. Urdu and Hindi wording needs review by fluent readers.
