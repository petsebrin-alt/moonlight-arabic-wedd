# Royal Moonlight Arabic Wedding Invitation — Product Requirements Document

| | |
|---|---|
| **Project** | Royal Moonlight Arabic Wedding Invitation (website) |
| **Owner** | Agrim |
| **Document status** | Draft v1.0 for review. **No build work starts until this PRD is approved.** |
| **Date** | 13 October 2026 |
| **Design and build approach** | Designed and developed entirely with Claude, directly in code. No Figma. |

> **How to read placeholders.** Anything in `[[DOUBLE SQUARE BRACKETS]]` is a placeholder that must be confirmed or supplied. Text tagged **⚑ AR-REVIEW** is Arabic wording that a fluent Arabic speaker must check before launch. Text tagged **⚑ CONFIRM** is an assumption made from the brief.

---

## Contents

1. Goals and success criteria
2. Wedding details (placeholders)
3. Guest journey and section order
4. Section-by-section requirements
5. Suggested invitation copy (English and Arabic)
6. Visual design: colours, typography, layout
7. Responsive layout
8. Animations, triggers and behaviour
9. Interaction rules (tap, hover, overlays, audio)
10. RSVP requirements
11. Wishing wall requirements
12. Storage, data and organiser access
13. Asset checklist
14. Accessibility criteria
15. Performance criteria
16. Testing plan
17. Development and hosting plan
18. Missing information Agrim needs to provide
19. Out of scope for v1
20. Approval

---

## 1. Goals and success criteria

**Goal.** A premium, elegant, mobile-first wedding invitation website with a royal, moonlit Arabic courtyard theme, in English and Arabic, that guests open from a shared link (WhatsApp, SMS, email).

**What guests must be able to do**
1. Open the invitation and understand who, when and where within 10 seconds.
2. See a live countdown to the wedding.
3. See which events they are invited to, with times and places.
4. Get directions to the venue in one tap.
5. RSVP in under one minute, and see confirmation only when it is truly saved.
6. Leave a wish for the couple and read approved wishes from other guests.
7. Switch between English and Arabic at any time, with correct right-to-left layout.

**What the organiser must be able to do**
1. See every RSVP in one place, live, from a phone or laptop, and export it.
2. Approve or reject wishes before they appear publicly.
3. Update details (times, venue, events) without a developer redesigning the site.

**Success criteria**
- Works smoothly on a mid-range Android phone over 4G and on recent iPhones.
- Lighthouse mobile scores: Performance ≥ 90, Accessibility ≥ 95, Best Practices ≥ 95.
- Text contrast meets WCAG 2.2 AA everywhere.
- Zero lost RSVPs: every confirmed RSVP exists in the organiser's sheet.
- Visuals look realistic, premium and crisp. **No blur effects, no cinematic effects** (no depth-of-field, no lens flares, no bokeh, no film grain, no heavy parallax, no glassmorphism blur).

---

## 2. Wedding details (placeholders)

All of these appear on the site as editable text drawn from one content file, so they can be changed without touching layout.

| Field | Current value (placeholder) | Status |
|---|---|---|
| Bride's name (EN) | `[[Ayisha]]` | ⚑ CONFIRM spelling (Ayisha / Aisha / Ayesha) |
| Groom's name (EN) | `[[Omar Sheikh]]` | ⚑ CONFIRM full name and capitalisation |
| Bride's name (AR) | `[[عائشة]]` | ⚑ AR-REVIEW, confirm preferred Arabic spelling |
| Groom's name (AR) | `[[عمر شيخ]]` | ⚑ AR-REVIEW |
| Main event date | `[[Sunday, 15 November 2026]]` | ⚑ CONFIRM: "15.11.2026" read as 15 November 2026 (a Sunday) |
| Main event time | `[[6:30 PM]]` | ⚑ CONFIRM which event this time belongs to |
| Time zone | `[[Gulf Standard Time, UTC+4 (Dubai)]]` | ⚑ CONFIRM. The brief's timezone field said "evening 6.30pm"; we assume Dubai time |
| Countdown target | `2026-11-15T18:30:00+04:00` | Derived from the two rows above |
| Venue | `[[Jumeirah Al Qasr]]` | ⚑ CONFIRM which hall / lawn / terrace inside the resort |
| Address | `[[Madinat Jumeirah, King Salman Bin Abdulaziz Al Saud Street, Umm Suqeim 3, Dubai, UAE]]` | ⚑ CONFIRM exact address and preferred Google Maps link |
| RSVP deadline | `[[Sunday, 1 November 2026, 11:59 PM GST]]` | ⚑ CONFIRM (default: two weeks before) |
| Hosts / families | `[[Family of the bride]]`, `[[Family of the groom]]` | Missing |
| Contact people | `[[Name, role, WhatsApp number]]` × 2 | Missing |
| Dress code | `[[Formal / Black tie / Traditional]]` | Missing |

---

## 3. Guest journey and section order

### 3.1 Journey

1. **Receives link** on WhatsApp. Link preview shows a crisp cover image, couple names and date (Open Graph tags).
2. **Lands on the cover.** Sees a sealed midnight-navy envelope in soft moonlight, a gold butterfly resting on the flap with gold dust rising from it, ivory roses, and an "Open Invitation" button. Nothing else on the page is reachable yet.
3. **Taps "Open Invitation".** The envelope-opening sequence plays (see 4.1): the flap opens, butterflies fly out, "Dear Guest" is written in gold, and the invitation scroll rises and unrolls. The next screen then appears automatically. Focus moves to its heading.
4. **Reads the welcome**, scrolls to the countdown and the couple story.
5. **Checks the schedule** to see which events apply.
6. **Browses the gallery** (optional).
7. **Taps "Get Directions"**, which opens Google Maps.
8. **Reads travel, stay and dress code** if travelling.
9. **Completes the RSVP.** Sees confirmation once saved.
10. **Leaves a wish**, is told it will appear after approval, and opens "View all wishes".
11. **Finds contact help** if anything is unclear.
12. **Reaches the thank-you** and uses "Back to top".

Returning guests (same device) skip the cover automatically if they opened it within the last 30 days, with a "Replay opening" link in the footer. This uses local storage only as a convenience.

### 3.2 Section order (final page order)

| # | Section | Anchor | In navigation menu |
|---|---|---|---|
| 1 | Opening cover | `#cover` | No |
| 2 | Welcome | `#welcome` | Home |
| 3 | Countdown | `#countdown` | No (part of Home) |
| 4 | Couple and families | `#couple` | Couple |
| 5 | Event schedule | `#events` | Events |
| 6 | Gallery | `#gallery` | Gallery |
| 7 | Venue | `#venue` | Venue |
| 8 | Travel and stay | `#travel` | Travel |
| 9 | Dress code | `#dress-code` | Dress Code |
| 10 | RSVP | `#rsvp` | RSVP (highlighted) |
| 11 | Wishing wall | `#wishes` | Wishes |
| 12 | Contact and assistance | `#contact` | Contact |
| 13 | Thank you + Back to top | `#thanks` | No |

### 3.3 Persistent elements (after the cover is opened)

- **Top bar** (slim, navy, appears after scrolling past the Welcome section): monogram on the start side; language switch (EN | ع) and menu button on the end side.
- **Menu**: full-screen overlay listing the anchors above. Rendered at page level, above everything (see §9.3).
- **Floating RSVP button** on mobile, bottom end corner, shown from the Countdown until the RSVP section is in view, hidden after a successful RSVP on this device.
- **Optional sound toggle** (only if Agrim supplies music), bottom start corner, off by default.

---

## 4. Section-by-section requirements

Each section lists content, layout and acceptance criteria. Copy is in §5.

### 4.1 Opening cover (revised 13 Oct 2026)
Motion reference: Agrim's screen recording of the Pinterest envelope video (inspected frame by frame). Colours adapted to midnight navy, ivory and champagne gold. The video's watermark and final garden scene are not used.

**Before the tap (idle)**
- Full-screen moonlit background: midnight navy with a soft silver moonlight wash from the top corner, twinkling stars, dark navy foliage in the top corners.
- A midnight-navy envelope sits in the lower part of the screen, sealed with a champagne-gold wax seal embossed with a butterfly.
- A gold butterfly rests on the flap above the seal, slowly opening and closing its wings, with a fine stream of gold dust rising from it.
- Four smaller gold butterflies hover gently around the envelope. Ivory roses, jasmine and pale blue florets frame the bottom corners.
- "Open Invitation" button and the date sit above the envelope. Language switch top end corner.

**Sequence after the tap (about 7 seconds, then a 4-second hold)**

| Time | What happens |
|---|---|
| 0.0 s | Button fades. A "Skip" button appears. The resting butterfly beats its wings faster |
| 0.1–1.4 s | The flap swings open upwards. A warm champagne glow rises from inside the envelope, with gold dust drifting up |
| 0.7–2.6 s | The butterfly lifts off and flies up in a graceful S-curve, leaving a sparkling gold trail |
| 1.3–3.5 s | Six more butterflies burst out of the envelope and settle around the edges of the screen |
| 2.6–4.5 s | The butterfly glides across the top of the screen and "Dear Guest" is written in flowing gold script behind it (handwriting reveal, right-to-left in Arabic) |
| 3.5–4.9 s | A rolled ivory-and-gold invitation scroll rises out of the envelope |
| 5.0–6.6 s | The scroll unrolls downwards to show: "With joy, we invite you to celebrate our wedding.", the couple's names and the date. The butterfly perches on the scroll |
| 6.7–10.5 s | Hold on the finished invitation. "Skip" becomes "Continue" |
| 10.5 s | The cover fades and the next screen appears automatically |

**Rules**
- All wording is live, editable text (EN and AR). "Dear Guest" is large gold script; the rest uses the readable serif.
- Glows and gold dust are drawn with gradients and particles, never a blur filter. The page text stays crisp.
- Reduced motion: tapping shows the finished invitation with a short fade, holds, then continues.
- "Skip" jumps to the finished invitation; "Continue" goes straight to the next screen.

**Next screen: grand Arabian wedding hall (pending)**
After the opening, the guest arrives in a grand Arabian wedding hall. Agrim will supply the reference; it will be designed after that. Until then the preview fades into the current Welcome section.

### 4.2 Welcome
- Couple names, invitation wording, date, time, venue name.
- Small ornamental divider (SVG) between blocks.
- "Add to calendar" button (downloads an `.ics` file; also offers a Google Calendar link).
- Acceptance: all text is live, editable text, never baked into images.

### 4.3 Countdown
- Four tiles: Days, Hours, Minutes, Seconds. Gold numerals on navy tiles with a thin gold arch outline.
- Counts down to `2026-11-15T18:30:00+04:00` regardless of the guest's own time zone. A small line states "Dubai time (GST, UTC+4)".
- Numbers use tabular figures so the layout never shifts as digits change.
- Arabic version: labels in Arabic. Numerals: Western digits (0–9) by default, with Eastern Arabic digits (٠–٩) as an option. ⚑ CONFIRM preference.
- After the target time: shows "Today is the day" during the event day, then "Thank you for celebrating with us" afterwards.
- Screen readers: the visible ticking is `aria-hidden`; a hidden summary ("30 days, 4 hours to go") updates once per minute, not every second.
- Reduced motion: numbers change without the flip/fade animation.

### 4.4 Couple introduction and family welcome
- Two portrait frames shaped as arches (bride, groom), each with name and a short line `[[about the bride]]`, `[[about the groom]]`.
- Optional short story timeline "How we met" (up to three moments) `[[optional]]`.
- Family welcome: "Together with their families" with parents' names `[[Mr & Mrs …]]` for both sides.
- Placeholders show a labelled ivory arch frame reading "Photo coming soon: bride portrait".

### 4.5 Event schedule
- Cards in a vertical timeline. Each card: event name, date, time, venue/hall, short note, dress note, "Add to calendar".
- **Only confirmed events are shown.** Each event in the content file has a `status` of `confirmed` or `pending`. Pending events are hidden on the live site. In the review build they show a "Pending confirmation" badge so Agrim can see them.
- Events currently pending: `[[Haldi]]`, `[[Mehendi]]`, `[[Nikah]]`, `[[Walima]]`, `[[Reception]]`. Each needs date, time, venue and whether all guests are invited.
- Per-guest invitations (optional, see §10.6): a guest's link can carry which events they are invited to, so the schedule and RSVP only list those.

### 4.6 Photo gallery
- Mobile: two-column masonry grid of 6–12 photos. Desktop: three columns.
- Tap opens a full-screen lightbox (page-level overlay) with swipe left/right, pinch zoom, a visible close button, counter "3 / 12", and captions.
- Images are lazy-loaded, served in AVIF/WebP with JPEG fallback, with fixed aspect ratios so nothing jumps.
- Placeholder tiles: ivory arch frame with label "Gallery photo 1 placeholder".

### 4.7 Venue
- Venue name, hall, full address, one or two venue photos (`[[venue photos]]`).
- **"Get Directions"** button opens Google Maps (`https://www.google.com/maps/dir/?api=1&destination=...`), which opens the app on phones.
- Secondary "Copy address" button with "Copied" confirmation.
- Embedded map is **not** loaded by default (heavy and privacy-unfriendly). A static map image or illustration with a "Show map" tap loads the Google Maps embed on request.
- Parking / arrival note `[[e.g. Valet at Al Qasr main entrance]]`.

### 4.8 Travel and guest stay
- Cards: Arriving in Dubai (airports DXB / DWC, distance to venue `[[confirm]]`), Getting to the venue (taxi, ride-hailing, valet), Where to stay (`[[recommended hotels, any group rate code, booking link, deadline]]`), Visa note ("Please check visa requirements for your nationality" with a link to the official UAE government portal, no invented visa rules), Weather in mid-November `[[short note]]`.
- If no travel details are supplied, the section collapses to a short "Need help with travel? Contact us" line.

### 4.9 Dress code
- Short statement `[[Dress code]]` plus optional per-event dress notes.
- Optional palette swatches "Colours we'd love to see" `[[optional]]`.
- Optional modesty or venue guidance only if Agrim supplies it. We do not invent customs.

### 4.10 RSVP
Full requirements in §10.

### 4.11 Wishing wall
Full requirements in §11.

### 4.12 Contact and guest assistance
- Two contact cards: name, role (e.g. "Bride's family"), WhatsApp button (`https://wa.me/<number>`), call button (`tel:`), optional email.
- Short FAQ accordion `[[optional]]`: children welcome?, photography policy?, parking?, gifts?
- Every answer is supplied by Agrim. Empty questions are hidden.

### 4.13 Thank you and Back to top
- Moonlit closing panel with a crescent moon, couple monogram, "Thank you" message, hashtag `[[#AyishaWedsOmar]]` (optional).
- **"Back to top"** button scrolls smoothly to Welcome (instantly with reduced motion) and moves focus to the Welcome heading. It does not return to the closed cover.

---

## 5. Suggested invitation copy

Arabic below is a starting draft only. **Every Arabic line is ⚑ AR-REVIEW.** We have deliberately not added any religious verse, prayer, Bismillah or du'a. If Agrim wants one, please supply the exact text and its source, and we will place it exactly as given.

### 5.1 Cover
| EN | AR (⚑ AR-REVIEW) |
|---|---|
| You are invited to the wedding of | يسعدنا دعوتكم لحضور حفل زفاف |
| Ayisha & Omar | عائشة و عمر |
| 15 · 11 · 2026 | ١٥ · ١١ · ٢٠٢٦ |
| Open Invitation | افتح الدعوة |
| Dear Guest | ضيفنا العزيز |
| With joy, we invite you to celebrate our wedding. | بكل فرح، ندعوكم للاحتفال بزفافنا. |
| Skip / Continue | تخطٍّ / متابعة |

### 5.2 Welcome
**EN**
> Together with their families,
> **Ayisha** and **Omar Sheikh**
> request the pleasure of your company
> as they celebrate their marriage.
>
> Sunday, 15 November 2026 · 6:30 in the evening
> Jumeirah Al Qasr, Madinat Jumeirah, Dubai

**AR (⚑ AR-REVIEW)**
> بكل الحب والسرور، وبمشاركة عائلتيهما،
> يتشرّف **عائشة** و**عمر شيخ**
> بدعوتكم لمشاركتهما فرحة زفافهما.
>
> الأحد، ١٥ نوفمبر ٢٠٢٦ · الساعة السادسة والنصف مساءً
> جميرا القصر، مدينة جميرا، دبي

Button: Add to calendar / أضف إلى التقويم

### 5.3 Countdown
| EN | AR (⚑ AR-REVIEW) |
|---|---|
| Counting down to our celebration | العدّ التنازلي لليلة العمر |
| Days · Hours · Minutes · Seconds | أيام · ساعات · دقائق · ثوانٍ |
| Dubai time (GST, UTC+4) | بتوقيت دبي (UTC+4) |
| Today is the day | اليوم هو يومنا |

### 5.4 Couple and families
| EN | AR (⚑ AR-REVIEW) |
|---|---|
| The Couple | العروسان |
| With joy, our families welcome you | تتشرّف عائلتانا بالترحيب بكم |
| Son of `[[parents]]` / Daughter of `[[parents]]` | نجل `[[ ]]` / كريمة `[[ ]]` |

### 5.5 Events
| EN | AR (⚑ AR-REVIEW) |
|---|---|
| Wedding Celebrations | برنامج الحفل |
| Pending confirmation | بانتظار التأكيد |
| Haldi · Mehendi · Nikah · Walima · Reception | الهلدي · المهندي · عقد القران (النكاح) · الوليمة · حفل الاستقبال |

Event names are kept as names only. No descriptions of what happens at each ceremony will be written unless Agrim supplies them.

### 5.6 Other headings and buttons
| EN | AR (⚑ AR-REVIEW) |
|---|---|
| Moments | لحظات |
| The Venue | مكان الحفل |
| Get Directions | احصل على الاتجاهات |
| Copy address / Copied | انسخ العنوان / تم النسخ |
| Travel & Stay | السفر والإقامة |
| Dress Code | قواعد اللباس |
| Kindly Reply | يُرجى تأكيد الحضور |
| Please reply by `[[1 November 2026]]` | يُرجى الرد قبل `[[١ نوفمبر ٢٠٢٦]]` |
| Joyfully attending / Regretfully unable to attend | سأحضر بكل سرور / أعتذر عن الحضور |
| Send RSVP | أرسل الرد |
| Wishes for the Couple | تهاني للعروسين |
| Leave a wish | اترك تهنئة |
| View all wishes | عرض جميع التهاني |
| Close | إغلاق |
| Need help? | هل تحتاج إلى مساعدة؟ |
| Thank you | شكراً لكم |
| We can't wait to celebrate with you | نتطلّع للاحتفال معكم |
| Back to top | العودة إلى الأعلى |

### 5.7 RSVP and wish messages
| State | EN | AR (⚑ AR-REVIEW) |
|---|---|---|
| Sending | Sending your reply… | جارٍ إرسال ردّك… |
| RSVP success (attending) | Thank you, `{name}`. Your reply is saved. We look forward to celebrating with you. | شكراً لك يا `{name}`. تم حفظ ردّك، ونتطلّع للاحتفال معك. |
| RSVP success (not attending) | Thank you, `{name}`. Your reply is saved. You will be missed. | شكراً لك يا `{name}`. تم حفظ ردّك، وسنفتقد حضورك. |
| RSVP error | We couldn't save your reply. Please check your connection and try again. Your answers are still here. | تعذّر حفظ ردّك. يُرجى التحقق من الاتصال والمحاولة مرة أخرى. إجاباتك ما زالت محفوظة هنا. |
| RSVP closed | RSVPs closed on `{date}`. Please contact `{contact}` if you need to change your reply. | انتهت مهلة تأكيد الحضور في `{date}`. يُرجى التواصل مع `{contact}` لأي تعديل. |
| Wish received | Thank you! Your wish will appear once it has been approved. | شكراً لك! ستظهر تهنئتك بعد الموافقة عليها. |
| No wishes yet | Be the first to leave a wish. | كن أول من يترك تهنئة. |

---

## 6. Visual design

### 6.1 Art direction
- **Scene:** a royal Arabic courtyard at night under a full or near-full moon. Graceful pointed and horseshoe arches, carved geometric screens (mashrabiya style), a reflecting pool or tiled floor, brass/gold lanterns casting warm light, restrained ivory flowers (roses, jasmine, gardenia) in small clusters, never overwhelming.
- **Quality bar:** realistic, crisp and premium, like high-end architectural photography or a precise rendering. Sharp edges, fine detail in carvings, clean gold metal.
- **Strictly avoid:** blur and backdrop blur, depth-of-field, bokeh, lens flare, glow halos on text, film grain, letterboxing, slow-zoom "cinematic" pans, heavy parallax, video backgrounds, neon, cartoon or clip-art style, generic stock "Arabian Nights" clichés.
- **Ornament language:** thin gold line work (1–1.5 px at mobile scale), 8-point star geometric patterns, arch-shaped frames for photos and cards, small crescent moon motif. Ornaments are SVG so they stay crisp at any size.
- **Restraint:** ornament frames content, it never sits behind body text. Each section has at most one decorative focal element.

### 6.2 Colour palette

| Token | Hex | Use |
|---|---|---|
| `--navy` (Midnight navy) | `#101A33` | Primary dark background, text on light |
| `--navy-raised` | `#1A2547` | Cards and tiles on navy |
| `--ivory` | `#F8F3E8` | Light section background, text on navy |
| `--gold` (Champagne gold) | `#C8A96B` | Ornaments, borders, headings **on navy**, primary button fill |
| `--gold-deep` | `#7A5C24` | Gold-tone **text on ivory or silver** (accessible variant) |
| `--silver` (Moonlight silver) | `#DCE4F0` | Moonlight accents, secondary text on navy, light panels |
| `--silver-muted` | `#A9B4C6` | Tertiary text on navy (captions) |
| `--ink` | `#1E2438` | Body text on ivory |
| `--ink-muted` | `#5A6275` | Secondary text on ivory |
| `--error` | `[[#B3261E on ivory / #FFB4AB on navy]]` | Form errors (to be checked in build) |
| `--success` | `[[#2E6B4F on ivory / #A8D5BA on navy]]` | Form success (to be checked in build) |

**Measured contrast (WCAG 2.x formula)**

| Text / background | Ratio | Result |
|---|---|---|
| Ivory on navy | 15.6 : 1 | Pass AAA |
| Silver on navy | 13.5 : 1 | Pass AAA |
| Silver-muted on navy | 8.2 : 1 | Pass AAA |
| Gold on navy | 7.7 : 1 | Pass AAA |
| Gold on navy-raised | 6.7 : 1 | Pass AA (AAA for large text) |
| Navy on gold (button label) | 7.7 : 1 | Pass AAA |
| Ink on ivory | 13.9 : 1 | Pass AAA |
| Ink-muted on ivory | 5.5 : 1 | Pass AA |
| Gold-deep on ivory | 5.6 : 1 | Pass AA |
| Gold-deep on silver | 4.9 : 1 | Pass AA |
| **Champagne gold on ivory** | **2.0 : 1** | **Fails. Never use `#C8A96B` for text on ivory.** Decoration only. |

**Rule:** text sits only on solid colour, never directly on a photograph. Where text overlays an image (cover), the image area behind text is a deliberately dark, low-detail part of the scene (night sky), plus a solid navy gradient band if needed. No blur scrims.

**Section rhythm:** dark (navy) and light (ivory) sections alternate so the page breathes: Cover (navy) → Welcome (navy) → Countdown (navy) → Couple (ivory) → Events (navy) → Gallery (ivory) → Venue (navy) → Travel (ivory) → Dress code (ivory) → RSVP (navy) → Wishes (ivory) → Contact (navy) → Thanks (navy). Transitions between them use an arch-shaped or geometric SVG edge, not a fade.

### 6.3 Typography

All fonts are free (SIL Open Font License), self-hosted and subset.

| Role | English | Arabic | Notes |
|---|---|---|---|
| Display (names) | **Cormorant Garamond** 500/600 | **Aref Ruqaa** 400/700 | Ruqaa is decorative; used for names and short headings only. ⚑ AR-REVIEW of style choice |
| Section headings | Cormorant Garamond 600 | **Amiri** 700 | Elegant, high legibility |
| Eyebrow / small caps labels | **Jost** 500, uppercase, +0.12em tracking | IBM Plex Sans Arabic 500 (no letter spacing, no uppercase) | Never letter-space Arabic |
| Body | **Jost** 400 | **IBM Plex Sans Arabic** 400 | Simple and readable |
| Numerals (countdown) | Cormorant Garamond, tabular | IBM Plex Sans Arabic, tabular | |

**Type scale (mobile → desktop), fluid with `clamp()`**

| Token | Mobile | Desktop | Line height |
|---|---|---|---|
| Display (names) | 44 px | 80 px | 1.1 |
| H2 (section) | 32 px | 48 px | 1.2 |
| H3 (card) | 22 px | 28 px | 1.3 |
| Body | 17 px | 18 px | 1.6 EN / 1.8 AR |
| Small / caption | 14 px | 15 px | 1.5 |
| Minimum anywhere | 14 px | 14 px | |

- Arabic body text renders about 10% larger than English at the same token for equal visual weight.
- Maximum line length 65 characters (EN), about 55 characters (AR).
- No text is ever an image. Names, dates and headings are live text so they can be edited, translated, read by screen readers and searched.

### 6.4 Components (design system built in code)
- **Buttons:** Primary = gold fill, navy text, 48 px min height, 999 px pill or arch-top shape. Secondary = 1.5 px gold outline, gold text on navy / gold-deep on ivory. Pressed state darkens 8%; focus ring 3 px silver on navy, 3 px navy on ivory, 2 px offset.
- **Cards:** navy-raised with 1 px gold hairline border and arch top, or ivory with gold-deep hairline.
- **Arch frame:** reusable SVG mask for photos (bride, groom, venue, gallery placeholders).
- **Dividers:** small gold ornament (star + lines), 120–200 px wide.
- **Form fields:** 52 px tall, ivory fill on navy section, ink text, gold-deep focus border, clear label above (never placeholder-only labels).
- **Overlay shell:** shared component for menu, gallery lightbox, wishes overlay and map (see §9.3).

---

## 7. Responsive layout

**Mobile-first.** Designed at 360 × 780 first, then scaled up.

| Breakpoint | Width | Layout |
|---|---|---|
| Base | 320–599 px | Single column, 20 px side padding, full-width cards, 2-col gallery |
| Tablet | 600–1023 px | Single column centred at max 640 px, events as 2-col grid, 3-col gallery |
| Desktop | ≥ 1024 px | Content max 1120 px; text blocks max 680 px; couple portraits side by side; venue photo + details side by side; 3-col gallery; menu becomes inline top-bar links |
| Large | ≥ 1440 px | Same as desktop with larger background art; content does not stretch |

- Uses `svh`/`dvh` units for full-height panels so mobile address bars do not cause jumps.
- Respects safe areas on notched phones (`env(safe-area-inset-*)`) for the top bar, floating RSVP and sound buttons.
- Landscape phones: cover arch scales down to fit height; nothing is cropped.
- **RTL:** layout uses CSS logical properties (`margin-inline-start`, `inset-inline-end`, etc.) throughout, so switching `dir="rtl"` mirrors the layout correctly. Things that **mirror**: navigation order, timeline side, button icon positions, swipe direction in the lightbox, floating button side. Things that **do not mirror**: the arch, lanterns, moon, photos, phone numbers, map, and countdown digit order.
- **Language switch:** a two-option toggle `EN | ع` in the top bar and on the cover. Switching updates `lang` and `dir` on `<html>`, swaps text from the content files, keeps the guest at the same section, and remembers the choice. Each language has its own URL (`/` and `/ar/`) so a link can be shared directly in Arabic, with `hreflang` tags. Default language: English, or Arabic if the guest's browser language is Arabic. ⚑ CONFIRM default.

---

## 8. Animations, triggers and behaviour

**Principles:** gentle, slow, sparing. Text never moves once it is readable. No blur, no cinematic camera moves. Everything uses CSS transforms and opacity only (GPU-friendly, no layout shift).

| # | Animation | Trigger | Behaviour | Duration / easing | Reduced motion |
|---|---|---|---|---|---|
| A1 | Lantern sway | Page load (cover) and when lantern is in view | Rotation ±2.5° around the hanging point, slightly different timing per lantern so they do not move in sync | 5–7 s loop, ease-in-out | Static |
| A2 | Lantern glow pulse | Same as A1 | Inner flame brightness varies 90–100% opacity. No outer blur halo; glow is a crisp painted gradient in the PNG | 3 s loop | Static |
| A3 | Star twinkle | When the star field is in view | 15–25 small SVG stars, each fades between 40% and 100% opacity at random delays | 2–5 s each | Static stars |
| A4 | Envelope opening | Tap on "Open Invitation" | Flap opens, butterfly trail, "Dear Guest" handwriting, butterflies burst out, scroll rises and unrolls (full timeline in 4.1), then auto-continues | about 7 s plus 4 s hold | Finished invitation shown with a short fade |
| A5 | Scroll entrance | Section enters viewport (IntersectionObserver, 15% visible) | Ornaments, cards and images fade in from 16 px below. Each element animates once only | 600 ms, ease-out, 80 ms stagger, max 4 staggered items | Shown instantly |
| A6 | Headings and body text | n/a | **Text is never animated letter-by-letter, never typed out, never moves after appearing.** Text blocks may share the section's single 400 ms opacity fade only | | Shown instantly |
| A7 | Countdown tick | Every second | Only the changing digit cross-fades (150 ms). Tile size fixed | 150 ms | No transition |
| A8 | Moon | n/a | Static. A very slow 60 s silver-shimmer on the moon edge is optional | | Static |
| A9 | Button press | Tap / click | Scale 0.97 and darken, then back | 120 ms | Colour change only |
| A10 | Overlay open/close | Tap | Overlay slides up from bottom (mobile) or fades (desktop) | 250 ms open, 200 ms close | Instant |
| A11 | Floral accents | Section in view | Ivory flowers appear with A5 only. No falling petals | | Static |

**Rules**
- `prefers-reduced-motion: reduce` disables A1–A3, A5, A7, A8, A11 and shortens A4/A10 as shown. A visible "Reduce motion" toggle in the menu does the same for guests who want it without changing system settings.
- Looping animations pause when off-screen or when the browser tab is hidden.
- Nothing flashes more than 3 times per second.
- No animation blocks reading or interaction; content is usable before any animation finishes.
- No scroll-jacking. Native scrolling everywhere.

---

## 9. Interaction rules

### 9.1 Tap equivalents for every hover
| Hover effect (desktop) | Mobile / touch equivalent |
|---|---|
| Button lifts / changes colour | Pressed state on tap (`:active`) and same visual on keyboard focus |
| Gallery photo shows caption | Caption always visible below photo on touch devices; tap opens lightbox |
| Event card reveals "Add to calendar" | Button always visible on touch devices |
| Couple portrait shows short bio | Bio always visible below portrait on touch devices |
| Nav link underline | Active section indicator in menu |
| Map preview hint | "Show map" button |
| Tooltip on icons | Visible text label next to every icon; no tooltip-only information |

Hover styles are applied only under `@media (hover: hover) and (pointer: fine)` so touch devices never get "sticky hover".

### 9.2 Touch targets
Minimum 48 × 48 px, with 8 px spacing between targets.

### 9.3 Menus, pop-ups and overlays (never clipped)
- All overlays (menu, gallery lightbox, "View all wishes", map, confirmation dialogs) are rendered **at the end of `<body>`**, outside every section, using the native `<dialog>` element in the top layer (or a single page-level portal root as fallback).
- No section uses `overflow: hidden`, `transform`, `filter` or `contain` in a way that could trap an overlay.
- A single z-index scale is defined: content 0, decorations 1, sticky top bar 100, floating buttons 200, overlays 1000, toasts 1100.
- Every overlay: covers the full viewport (`100dvh`), has a **visible close button** (top end corner, 48 px, with "Close" label for screen readers), closes on Esc, closes on the phone's Back button (uses history state), traps focus inside, returns focus to the button that opened it, and locks background scroll without jumping the page.

### 9.4 Background audio (optional)
- Only built if Agrim supplies a licensed music file.
- **Never autoplays.** Audio is off by default. After the cover is opened, a small sound toggle appears ("Play music"). Music starts only when the guest taps it.
- Toggle shows clear on/off state, volume starts at 40% with a 2 s fade in, pauses automatically when the tab is hidden or a video plays, and the choice is remembered.
- The site works fully without audio.

### 9.5 Other interactions
- "Add to calendar": generates an `.ics` file with correct time zone (Asia/Dubai) and a Google Calendar link.
- "Copy address": uses the Clipboard API with a visible "Copied" message.
- Smooth scrolling for menu links (instant with reduced motion).
- Share button in the thank-you section using the Web Share API on phones, with "Copy link" fallback.

---

## 10. RSVP requirements

### 10.1 Fields

| Field | Type | Required | Validation |
|---|---|---|---|
| Full name | Text | Yes | 2–80 characters, letters (any script), spaces, `.'-`; trimmed |
| Attending? | Two large choice cards: "Joyfully attending" / "Regretfully unable to attend" | Yes | One must be selected |
| Number of guests (including you) | Stepper − / + | Yes if attending | Whole number 1 to `[[max per invite, default 4]]`. Hidden and set to 0 if not attending |
| Which events? | Checkboxes listing **confirmed** events only (or only those on the guest's invite) | Yes if attending, at least one | Hidden if not attending |
| Dietary requirements | Text area | No | Max 300 characters; with helper "Allergies or dietary needs (optional)" |
| Phone or email | Text | `[[optional, ⚑ CONFIRM]]` | Valid format if given. Helps the organiser contact guests and detect duplicates |
| Message to the couple | Text area | No | Max 300 characters (private, not posted to the wishing wall) |
| Hidden: honeypot field | Hidden input | — | Must be empty (spam protection) |

### 10.2 Deadline
- RSVP deadline `[[1 November 2026, 23:59 GST]]` shown above the form: "Please reply by …".
- After the deadline the form is replaced by the "RSVPs closed" message with contact links. The server also rejects submissions after the deadline, so the rule cannot be bypassed.

### 10.3 States
| State | What the guest sees |
|---|---|
| Idle | Form with labels, hints, required markers ("required" in text, not colour alone) |
| Field error (validation) | Shown when leaving a field or on submit. Red message under the field, field outlined, error icon, `aria-invalid` and `aria-describedby` set. On submit with errors, an error summary appears at the top listing each problem as a link to its field; focus moves to the summary |
| Submitting / loading | Button changes to "Sending your reply…" with a small spinner, becomes disabled to prevent double submission; all inputs read-only |
| **Success** | **Shown only after the server confirms the row was written** (response `{ ok: true, id }`). Form is replaced with a personalised thank-you card, a summary of what they sent, and "Add to calendar". Focus moves to the thank-you heading. The device remembers the RSVP so the floating RSVP button hides |
| Error | Network failure, timeout (15 s) or server error: a clear message above the button, all entered answers kept, "Try again" button, and contact links as a fallback. **Never shows success on error** |
| Closed | Deadline passed (see 10.2) |
| Already replied (same device) | "You replied on {date}. Need to change it?" with a button to submit an updated reply (new row marked as update) |

### 10.4 Rules
- Double submission is blocked by disabling the button and by a client-generated submission ID that the server de-duplicates.
- Updates: a guest re-submitting creates a new row with the same name/contact. The organiser's sheet shows the latest reply per guest in a "Latest replies" view.
- All text is stored as plain text and escaped when displayed.

### 10.5 Data saved per RSVP
`submission_id, submitted_at (UTC and Dubai time), language, full_name, attending (yes/no), guest_count, events (list), dietary, contact, message, invite_code (if used), user_agent_summary (mobile/desktop only), is_update`.

### 10.6 Optional: personalised invite links
Each household gets a link like `…/?i=K7Q2` where the code maps to the household name, maximum guest count, and which events they are invited to. This pre-fills the name, caps the guest count and limits events. ⚑ CONFIRM whether Agrim wants this. It is recommended when not every guest is invited to every event (common with Haldi / Mehendi / Nikah / Walima / Reception).

---

## 11. Wishing wall requirements

### 11.1 Submitting a wish
- Fields: **Name** (required, 2–60 characters) and **Message** (required, 2–500 characters, live character counter). Honeypot field for spam.
- States: idle, validation errors, sending, success, error (same patterns as RSVP).
- Success message: "Thank you! Your wish will appear once it has been approved." The guest's own wish is shown to them on their device with a "Pending approval" label so they know it was received. It is **not** visible to anyone else yet.

### 11.2 Moderation
- Every new wish is saved with status `pending`. **Nothing appears publicly until the organiser approves it.**
- Organiser approves by ticking an "Approved" checkbox in the Wishes sheet (see §12). Unticking hides it again. A "Hidden" option removes it permanently from the public wall.
- Basic automatic help: a word list flags (does not reject) messages containing links or listed words so the organiser can review them first.

### 11.3 Display
- Section shows the **latest 3–6 approved wishes** as elegant ivory cards with gold-deep quote marks, name and date.
- Approved wishes are shared across all devices: every guest's browser fetches the current approved list from the server when the section comes into view (and caches it for 2 minutes).
- Arabic and English wishes each render in their own direction automatically (`dir="auto"` per card), regardless of the site language.

### 11.4 "View all wishes" overlay
- Opens a **full-screen overlay** on mobile (page-level `<dialog>`, see §9.3), a centred large panel on desktop.
- Header with title "Wishes for the Couple", count, and a **visible Close button** that stays fixed while the list scrolls.
- Scrollable list of all approved wishes, newest first, loaded 20 at a time as the guest scrolls.
- Background page does not scroll while open. Esc and the phone's Back button close it. Focus returns to the "View all wishes" button.
- Empty state: "Be the first to leave a wish."

---

## 12. Storage, data and organiser access

### 12.1 Recommended stack (default)

**Google Sheets + Google Apps Script as the backend, static site on Cloudflare Pages.**

Why this default: it costs nothing, needs no server to maintain, and the organiser views and moderates everything in a spreadsheet they already know, on phone or laptop, live.

```
Guest's browser ──HTTPS──► Apps Script web app (doPost / doGet)
                                │  validates, de-duplicates, checks deadline,
                                │  rate-limits, writes with a lock
                                ▼
                     Google Sheet (owned by the organiser)
                       ├─ RSVPs          (one row per submission)
                       ├─ RSVP Summary   (formulas: totals, per event, latest per guest)
                       ├─ Wishes         (status: pending / approved / hidden)
                       └─ Settings       (deadline, max guests, invite codes)
```

**How it works**
- **RSVP:** the site sends the form to the Apps Script endpoint. The script validates everything again on the server, checks the deadline and honeypot, takes a lock (so simultaneous submissions never overwrite each other), appends a row, and only then returns `{ ok: true }`. The site shows success only on that response.
- **Wishes:** submissions are appended to the Wishes sheet with `Approved` unticked. The public site calls `GET ?action=wishes`, and the script returns **only approved** wishes (name, message, date; never contact details). This is how wishes are shared across all devices.
- **Spam and abuse:** honeypot, server-side validation, length limits, per-device rate limit (e.g. max 5 submissions per 10 minutes), and optional Cloudflare Turnstile (invisible captcha) if spam appears.

**How the organiser views responses**
- Open the Google Sheet (shared only with the organisers) on any device. New RSVPs appear within seconds.
- **RSVP Summary** tab: total attending guests, total declined, guests per event, dietary list, latest reply per guest, list of invite codes not yet replied (if invite links are used).
- Filter, sort, and export to Excel/CSV/PDF from Sheets.
- Optional: email notification to the organiser for each new RSVP or new wish (Apps Script `MailApp`). ⚑ CONFIRM.

**How the organiser moderates wishes**
- Open the **Wishes** tab; new wishes have a yellow "Pending" highlight. Tick **Approved** to publish, set **Hidden** to remove. Changes show on the site within about 2 minutes.

**Limits to know**
- Apps Script handles a wedding-sized guest list comfortably (hundreds of submissions). Responses take about 1–2 seconds, which the loading state covers.
- Data lives in the organiser's Google account; only people the sheet is shared with can see RSVPs.

**Alternative (only if needed):** Supabase (hosted Postgres) with row-level security and a small password-protected `/admin` page for viewing RSVPs and approving wishes. Worth it only if the guest list is very large (1,000+), if Agrim wants a custom admin screen instead of a spreadsheet, or if a Google account cannot be used.

### 12.2 Privacy
- Short privacy note under the RSVP form: what is collected, why, who sees it, and that it will be deleted `[[60 days]]` after the wedding. ⚑ CONFIRM retention.
- Dietary information is optional and visible only to organisers.
- No analytics cookies by default. If Agrim wants visit stats, use cookieless analytics (Cloudflare Web Analytics).
- Search engines: `noindex` by default so the invitation does not appear in Google search. ⚑ CONFIRM.

### 12.3 Content management
All wording, names, dates, events and contacts live in two content files (`content/en.json`, `content/ar.json`) plus `content/event.json` for shared data (dates, times, statuses, map links). Changing a time or confirming an event means editing one value; the site rebuilds and deploys automatically.

---

## 13. Asset checklist

Agrim will supply final assets. Until then, every image slot shows a labelled placeholder (ivory or navy panel, thin gold arch outline, text such as "PLACEHOLDER · cover-courtyard-mobile.webp · 1080 × 1920").

**File rules**
- Photos/backgrounds: supply as high-quality JPEG or PNG at the size below; we will export AVIF + WebP + JPEG versions. Sharp focus throughout (no blur or bokeh), as per the visual rule.
- Transparent elements: PNG-24 with alpha, trimmed tight, at 2× the display size. Edges must be clean (no halos).
- SVG: flat vector, no embedded raster images, strokes converted or set with `vector-effect`, colours using the palette so we can recolour via CSS.
- Filenames: lowercase, hyphens, no spaces, as below.

### 13.1 Backgrounds

| # | Filename | Suggested size (px) | Description | Priority |
|---|---|---|---|---|
| B1 | `bg-cover-courtyard-mobile.jpg` | 1080 × 1920 (9:16) | Moonlit courtyard, central arch, dark open sky in upper third for text | Must |
| B2 | `bg-cover-courtyard-desktop.jpg` | 2560 × 1440 (16:9) | Same scene, wider composition | Must |
| B3 | `bg-night-sky-tile.jpg` | 1080 × 1920 | Clean navy night sky with faint stars, for navy sections | Should |
| B4 | `bg-courtyard-floor-mobile.jpg` | 1080 × 1350 | Tiled courtyard floor / reflecting pool for Venue or Thanks section | Could |
| B5 | `bg-ivory-texture.jpg` | 1600 × 1600 | Very subtle ivory paper/plaster texture (seamless) | Could |
| B6 | `og-share-image.jpg` | 1200 × 630 | WhatsApp/social link preview: arch, names, date as live-composed graphic | Must |

### 13.2 Transparent PNGs

| # | Filename | Suggested size (px, 2×) | Description | Priority |
|---|---|---|---|---|
| P1 | `cover-roses-left.png`, `cover-roses-right.png` | 1200 × 1000 each | Photographic ivory roses with jasmine and pale blue florets, for the cover corners (currently drawn in code) | Should |
| P2 | `butterfly-gold.png` (optional) | 400 × 320 | Photographic gold butterfly, wings open, if a more realistic butterfly is wanted (currently drawn in code) | Could |
| P2b | `bg-grand-hall-*.jpg` | 1080 × 1920 and 2560 × 1440 | Grand Arabian wedding hall for the screen after the opening | Must, reference pending |
| P3 | `lantern-gold-large.png` | 400 × 900 | Hanging gold lantern with chain, lit, pivot at top centre | Must |
| P4 | `lantern-gold-small.png` | 260 × 600 | Smaller lantern variant | Must |
| P5 | `moon-full.png` | 800 × 800 | Crisp, realistic moon | Must |
| P6 | `flowers-ivory-cluster-a.png` | 800 × 600 | Restrained ivory rose/jasmine cluster, corner placement | Should |
| P7 | `flowers-ivory-cluster-b.png` | 600 × 800 | Second cluster, mirrored use | Should |
| P8 | `flowers-ivory-garland.png` | 1600 × 300 | Thin garland for section edges | Could |
| P9 | `mashrabiya-screen-panel.png` | 800 × 1600 | Carved screen panel for side decoration on desktop | Could |

### 13.3 SVG decorations

| # | Filename | Viewbox | Description | Priority |
|---|---|---|---|---|
| S1 | `arch-frame.svg` | 0 0 400 600 | Line-art arch outline for frames and cards | Must (built by Claude) |
| S2 | `arch-mask.svg` | 0 0 400 560 | Arch shape mask for photos | Must (built by Claude) |
| S3 | `divider-star.svg` | 0 0 240 24 | 8-point star with flanking lines | Must (built by Claude) |
| S4 | `pattern-geometric-8star.svg` | 0 0 120 120 | Seamless geometric tile | Must (built by Claude) |
| S5 | `border-arch-edge.svg` | 0 0 1440 80 | Scalloped/arched section edge | Must (built by Claude) |
| S6 | `star-twinkle.svg` | 0 0 24 24 | Small 4/8-point star for twinkles | Must (built by Claude) |
| S7 | `crescent-moon.svg` | 0 0 64 64 | Crescent motif | Must (built by Claude) |
| S8 | `monogram-ao.svg` | 0 0 200 200 | Couple monogram `[[A & O]]`, letters as live text inside SVG frame | Should (built by Claude, ⚑ CONFIRM letters) |
| S9 | `corner-ornament.svg` | 0 0 160 160 | Gold corner flourish for cards | Should |
| S10 | Icon set: `icon-map-pin`, `icon-calendar`, `icon-clock`, `icon-whatsapp`, `icon-phone`, `icon-close`, `icon-menu`, `icon-music-on`, `icon-music-off`, `icon-copy`, `icon-share`, `icon-arrow-up` | 0 0 24 24 | Thin-line icons in gold | Must (built by Claude) |

SVGs S1–S10 can be drawn by Claude in code. Agrim may replace any of them with supplied artwork.

### 13.4 Photographs (supplied by Agrim)

| # | Filename | Suggested size (px) | Description | Priority |
|---|---|---|---|---|
| F1 | `couple-bride-portrait.jpg` | 1200 × 1600 (3:4) | Bride portrait (arch-masked) | Should |
| F2 | `couple-groom-portrait.jpg` | 1200 × 1600 (3:4) | Groom portrait | Should |
| F3 | `couple-together.jpg` | 1600 × 2000 (4:5) | Optional joint photo | Could |
| F4–F15 | `gallery-01.jpg` … `gallery-12.jpg` | Long edge 2000 | Gallery photos with captions | Should |
| V1 | `venue-01.jpg` | 1600 × 1000 | Venue exterior/hall | Must |
| V2 | `venue-02.jpg` | 1600 × 1000 | Second venue view | Could |
| V3 | `venue-map-static.png` | 1200 × 800 | Static map or illustrated map (Claude can create an illustrated one) | Should |

### 13.5 Other assets

| # | Filename | Format | Description | Priority |
|---|---|---|---|---|
| A1 | `music-background.mp3` | MP3 128 kbps, ≤ 3 MB, loopable | Licensed instrumental track | Optional |
| A2 | `favicon.svg`, `apple-touch-icon.png` (180 × 180) | SVG/PNG | Monogram icon | Must (built by Claude) |
| A3 | Style references | Any | Images Agrim likes for mood, arches, lanterns, flowers | Requested |

---

## 14. Accessibility criteria

Target: **WCAG 2.2 Level AA.**

- **Contrast:** text ≥ 4.5 : 1, large text and UI components ≥ 3 : 1 (palette verified in §6.2).
- **Structure:** one `<h1>` (couple names), logical `<h2>` per section, landmarks (`header`, `nav`, `main`, `footer`), skip link "Skip to RSVP" and "Skip to content".
- **Language:** `<html lang="en" dir="ltr">` or `lang="ar" dir="rtl"`. Mixed-language snippets marked with `lang`. Names in both scripts are announced correctly.
- **Keyboard:** everything reachable and operable by keyboard in a logical order (also correct in RTL). Visible focus ring on every interactive element.
- **Screen readers:** cover button, countdown summary, form errors, loading and success messages announced via live regions. Decorative images `alt=""`; meaningful photos have alt text (`[[captions from Agrim]]`).
- **Forms:** visible labels, required fields marked in text, errors described in words with suggestions, error summary, no time limit on filling the form.
- **Motion:** respects `prefers-reduced-motion` and offers an on-page toggle. No auto-playing audio. Looping animations can be stopped.
- **Zoom and text size:** works at 200% zoom and with large system font sizes without loss of content or horizontal scrolling (except the gallery lightbox).
- **Touch:** targets ≥ 48 px; no gesture-only actions (swipe in lightbox also has arrow buttons).
- **Overlays:** focus trapped, Esc and Back close, focus returns.
- **No information by colour alone** (attending/not attending cards have icons and text; errors have icons and text).

---

## 15. Performance criteria

| Metric (mobile, 4G, mid-range Android) | Target |
|---|---|
| Largest Contentful Paint | ≤ 2.0 s |
| Cumulative Layout Shift | ≤ 0.05 |
| Interaction to Next Paint | ≤ 150 ms |
| Total JavaScript (gzipped) | ≤ 60 KB |
| Initial page weight (before scrolling) | ≤ 900 KB |
| Full page weight with all images | ≤ 4 MB (music excluded) |
| Animation frame rate | Steady 60 fps on mid-range phones |

**How**
- Static HTML generated at build time; minimal JavaScript, no heavy framework at runtime.
- Cover image preloaded at the right size; everything else lazy-loaded with fixed dimensions.
- Responsive images (`srcset` with 640/960/1280/1920 widths), AVIF/WebP.
- Fonts self-hosted, subset to used characters (Latin + Arabic), `font-display: swap`, two weights per family maximum, preload only the display font.
- Google Maps embed and music load only on request.
- Animations use transform/opacity only; looping ones pause off-screen.
- Cached at the edge by Cloudflare; long cache for hashed assets.

---

## 16. Testing plan

### 16.1 Devices and browsers
| Device | Browsers |
|---|---|
| iPhone (iOS 17+, small and large) | Safari, Chrome, **WhatsApp in-app browser** |
| Android mid-range (e.g. Samsung A-series) | Chrome, Samsung Internet, **WhatsApp in-app browser**, Instagram in-app browser |
| iPad / tablet | Safari, Chrome |
| Desktop | Chrome, Safari, Firefox, Edge |

### 16.2 Automated tests
- **End-to-end (Playwright)** at 360 × 780, 390 × 844, 768 × 1024, 1440 × 900, in both EN and AR:
  - Cover blocks scrolling until tapped; opening reveals Welcome and moves focus.
  - Language switch mirrors layout, keeps position, persists.
  - Countdown matches the target time when the browser is set to different time zones (London, Dubai, New York, Kolkata).
  - RSVP: validation messages, loading state, success **only after a mocked successful save**, error state on mocked failure/timeout keeps entered data, deadline closed state, double-tap protection.
  - Wishes: submit → pending message; approved-only list rendering; "View all wishes" overlay opens full-screen, scrolls, close button visible, Esc/Back close, focus returns.
  - Menu, lightbox and wishes overlays are above all content and not clipped (screenshot check at each breakpoint).
  - Reduced-motion mode: no looping animations running.
- **Accessibility:** axe-core on every section in both languages, zero serious/critical issues.
- **Performance:** Lighthouse CI on each deploy with the budgets in §15.
- **Visual regression:** screenshot comparison per section, both languages, to catch layout breaks.

### 16.3 Manual tests
- Screen reader passes: VoiceOver (iOS) and TalkBack (Android) in both languages.
- Keyboard-only pass on desktop.
- Real backend test: submit 20 RSVPs and 10 wishes from different phones at the same time; confirm every row arrives once, approved wishes appear on all devices.
- WhatsApp link preview check (image, title, description).
- Arabic review session with a fluent reader: wording, names, digits, line breaks, font rendering.
- Visual check against the "crisp, no blur, no cinematic effects" rule on real devices.

### 16.4 Launch checklist
All placeholders replaced or deliberately hidden; pending events hidden; RSVP deadline set; sheet shared only with organisers; test data cleared; `noindex` decision applied; custom domain and HTTPS working; final Arabic sign-off.

---

## 17. Development and hosting plan

### 17.1 Technology
| Part | Choice | Why |
|---|---|---|
| Site framework | **Astro** (static output) with plain TypeScript for interactions | Fast static HTML, built-in i18n routing for `/` and `/ar/`, tiny JavaScript |
| Styling | Hand-written CSS with design tokens (custom properties) and logical properties | Full control over the premium look and RTL |
| Content | JSON content files per language | Easy edits, clean translation workflow |
| Backend | Google Apps Script web app + Google Sheet | See §12 |
| Hosting | **Cloudflare Pages** (free tier) | Global CDN including the Middle East, HTTPS, preview links for every change |
| Source control | GitHub repository `[[to be created]]` | Every change reviewable, auto-deploy on merge |
| Domain | `[[e.g. ayishaandomar.com]]` or the free `*.pages.dev` address | ⚑ CONFIRM |

Alternative host: Netlify or Vercel work equally well; no change to the plan.

### 17.2 Phases

| Phase | Output | Agrim's involvement |
|---|---|---|
| 0. PRD review | This document approved with answers to §18 | Review and answer |
| 1. Design foundation | Live style page: colours, type in EN/AR, buttons, arch frames, ornaments, lantern and star animations | Approve the look |
| 2. Cover + Welcome + Countdown prototype | Clickable preview link on mobile | Approve the first impression |
| 3. All sections with placeholders | Full page in EN and AR | Review layout and copy |
| 4. RSVP and wishing wall backend | Google Sheet + Apps Script connected; organiser guide (1 page) | Share a Google account/sheet for ownership |
| 5. Real assets and content | Replace placeholders with supplied assets and confirmed details | Supply assets and details |
| 6. Testing and Arabic review | Test report, fixes, Arabic sign-off | Arabic reviewer |
| 7. Launch | Live URL, link preview, final checks | Final approval, then share with guests |
| 8. After the wedding | Switch to thank-you mode, export data, delete personal data per retention | Optional |

Preview links are produced at every phase so Agrim reviews on a real phone, which replaces Figma reviews.

### 17.3 Ownership
The Google Sheet and Apps Script should be owned by Agrim's (or the couple's) Google account so the organisers keep full control of guest data. The code and hosting can be set up under Agrim's GitHub and Cloudflare accounts.

---

## 18. Missing information Agrim needs to provide

**Confirm (assumptions made)**
1. Couple names: exact English spelling and Arabic spelling for Ayisha and Omar Sheikh; whether the bride's surname is shown.
2. Date: 15 November 2026 (Sunday) is correct.
3. Time and time zone: 6:30 PM Dubai time (GST, UTC+4), and which event it refers to.
4. Venue: which space at Jumeirah Al Qasr; exact address; preferred Google Maps link.
5. Default site language (English, or auto-detect Arabic browsers).
6. Digits in Arabic version: Western (15) or Eastern Arabic (١٥).

**Supply**
7. Events: for each of Haldi, Mehendi, Nikah, Walima, Reception — confirmed or not, date, time, venue, who is invited, dress note.
8. Whether every guest sees every event, or personalised invite links are needed (§10.6).
9. RSVP deadline and maximum guests per invitation.
10. Whether to ask for phone/email in the RSVP.
11. Families: parents' names and how they should be written (EN and AR).
12. Couple introduction text (short bios, optional "how we met").
13. Dress code (overall and per event).
14. Travel and stay details: hotels, group rates or codes, transport advice.
15. Contacts for guest assistance: names, roles, WhatsApp numbers.
16. FAQ answers (children, photography, gifts, parking), if wanted.
17. Invitation wording preference, if different from §5, and any religious text you want included (exact wording and source; we will not write it).
18. Optional hashtag and monogram letters.
19. Photos: portraits, gallery (with captions/alt text), venue photos.
20. Style references and final decorative assets (§13).
21. Background music file and confirmation that it is licensed for this use (optional).
22. A fluent Arabic reviewer to approve all Arabic text.
23. Google account that will own the RSVP sheet, and who else should see responses.
24. Whether organisers want email alerts for new RSVPs and wishes.
25. Domain name preference (custom domain or free address).
26. Data retention period after the wedding, and whether the site should be hidden from search engines.
27. Reference for the grand Arabian wedding hall screen that follows the opening.

---

## 19. Out of scope for v1

- Payments, gift registry checkout or cash gifts.
- Guest photo uploads.
- Live streaming.
- Accounts or logins for guests.
- Push notifications or SMS sending.
- Video backgrounds or 3D scenes.
- Any languages beyond English and Arabic.

These can be added later if wanted.

---

## 20. Approval

| Item | Status |
|---|---|
| PRD reviewed by Agrim | ☐ |
| Answers to §18 received | ☐ |
| Recommended storage stack (Google Sheets + Apps Script) approved | ☐ |
| Hosting (Cloudflare Pages) approved | ☐ |
| Go-ahead to start Phase 1 | ☐ |

*No website development will begin until this PRD is approved.*
