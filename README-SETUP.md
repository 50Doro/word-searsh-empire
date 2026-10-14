# Word Search Empire — WarriorPlus sales page

This folder is the **sales page** you point WarriorPlus at. It is a plain static
site: no build step, no server code, no dependencies to install. Upload the
folder as-is and it works.

```
wordsearch-warriorplus-landing/
├── index.html                       the sales page
├── refund-policy.html               standalone legal pages, linked
├── terms-of-use.html                from the footer of every page
├── privacy.html
├── earnings-results-disclaimer.html
├── deluxe/                          the $47 Deluxe upgrade sales page
│   ├── index.html
│   ├── refund-policy.html
│   ├── terms-of-use.html
│   ├── privacy.html
│   ├── earnings-results-disclaimer.html
│   └── assets/legal.css
├── assets/
│   ├── ui-full.png                  real screenshots of the app (not mockups)
│   ├── topic-dashboard.png
│   ├── puzzle-page.png
│   ├── puzzle-solution.png
│   ├── puzzle-playful.png
│   ├── puzzle-elegant.png
│   ├── puzzle-bold.png
│   ├── puzzle-chalkboard.png
│   ├── book-interior.png
│   ├── legal.css                    shared styling for the legal pages
│   └── fonts/                       self-hosted webfonts
└── README-SETUP.md                  this file
```

---

## 1. Checkout settings (already set — verify once)

The page is live-ready: the order link, the price and the support address are all
filled in. The money-back window is **14 days**.

Open `index.html` and scroll to the `<script>` block at the very bottom. It
starts with:

```js
var BUY_URL       = "https://warriorplus.com/o2/buy/srwmfg/t0y3nb/nbs9nk";
var PRICE         = "$27";
var SUPPORT_EMAIL = "ayoubebay1@gmail.com";
```

| Setting | What it does |
|---|---|
| `BUY_URL` | Your WarriorPlus order link for this product. The top-nav, offer-block and sticky-bar buttons point straight here; the hero button scrolls down to the offer box instead. Swap this if you ever change offer or want to point traffic at a different launch link. |
| `PRICE` | Whatever you actually charge, e.g. `"$17"`. It is printed in four places automatically. |
| `SUPPORT_EMAIL` | Already set to `ayoubebay1@gmail.com`. It appears in the guarantee block and footer of every page; change it here and on the four legal pages if you ever want a different inbox. |

If you ever change the support address, do a **find-and-replace across all five
`.html` files** (each legal page also has a single `SUPPORT_EMAIL = "..."`
line at the bottom). `BUY_URL` and `PRICE` live only in `index.html` — the legal
pages link back to its offer section.

The yellow reminder bar is **gone**. An earlier version of the page showed one
until `BUY_URL` was filled in, with a `SHOW_SETUP_BAR` switch to hide it; both
the bar and that switch have been removed. The script keeps a safety net: if
`BUY_URL` is ever set back to a value starting with `REPLACE`, the buy buttons
scroll to the on-page offer instead of jumping to a dead link.

## 2. The WarriorPlus code and disclaimer (already installed — leave both)

`index.html` carries the WarriorPlus sales-page code, as the last thing before
`</body>`:

```html
<script type="text/javascript" src="https://warriorplus.com/o2/js/t0y3nb"></script>
```

WarriorPlus requires this to remain on the page at all times — it powers the
buttons, tracking and disclaimer behaviour, and removing it after compliance
approval is prohibited. The `t0y3nb` in the URL is **this offer's** ID, so do not
copy it to any other offer.

The WarriorPlus disclaimer text sits directly under the offer buy button. Keep it
there as well.

Both belong to the front-end offer only. The Deluxe OTO is a separate WarriorPlus
offer, so it has its own sales-page code and its own ID — both already installed
in `deluxe/index.html`. Do not copy one page's code to the other.

## 3. Publish it

Any static host works — the page is one HTML file plus images:

1. Upload the whole folder (keeping `index.html` at the root and the four legal
   pages next to it — the footer links between them are relative).
2. Open the live URL and check: no setup banner appears, a button click reaches
   your WarriorPlus order form, the images load, and the four footer legal links
   each open their page.
3. In the WarriorPlus vendor dashboard, set this URL as your product's sales page.
4. Leave the `deluxe/` sub-folder where it is — the footer of this page links to
   `deluxe/index.html`. In the WarriorPlus dashboard, give the Deluxe offer its
   own sales-page URL pointing at `<your-domain>/deluxe/`.

If you host it under the same domain as your other offers, that is fine — there
is nothing server-side in here.

## 4. The product buyers receive

That lives in a separate folder: `wordsearch-deliverables/`.

```
wordsearch-deliverables/
├── WordSearchEmpire.html               the app (one file, works offline)
├── wordsearch-quick-start-guide.pdf    bonus 1
└── wordsearch-book-checklist.pdf       bonus 2
```

Zip those three and upload the zip to WarriorPlus as the product file. **Do not**
put that folder inside the web root you just published, or buyers can download
the product for free.

---

## What has already been done for you

**Compliance (checked against WarriorPlus vendor terms and FTC guidance):**

- No income, earnings or "make money" claims anywhere on the page.
- No fabricated testimonials, names, photographs or results. Proof is limited to
  real screenshots of the product itself.
- A published 14-day refund policy with the request method and processing time —
  short summary in the footer, full text on its own `refund-policy.html` page.
- Four standalone legal pages, each linked from the footer of every page:
  `refund-policy.html`, `terms-of-use.html`, `privacy.html` and
  `earnings-results-disclaimer.html` (plus an affiliate disclosure and a
  "not affiliated with Amazon, KDP, Etsy or any browser vendor" statement).
- Every product claim on the page can be demonstrated by the app itself.
- The WarriorPlus-provided disclaimer is printed under the offer buy button, and
  WarriorPlus's required sales-page code is installed before `</body>` in
  `index.html`. Both must stay on the page — see section 2.

**If you ever add testimonials:** there is an empty, clearly marked block in the
`Proof` section of `index.html` (search for `OPTIONAL — REAL TESTIMONIALS`).
Only use genuine quotes from real buyers, with their permission, and keep the
"your results may differ" line underneath.

**Design and content notes:**

- Fonts are self-hosted in `assets/fonts/`, so the page renders identically
  offline. The **only** outbound request is the required WarriorPlus sales-page
  script in `index.html` (section 2) — leave it in place.
- All screenshots are genuine captures of the app, including the answer-key
  highlighting, the style presets and the book interior.
- The hero contains a small interactive 10×10 word search that highlights each
  hidden word in turn. It pauses automatically for visitors who have
  "reduce motion" switched on.
- The price appears in four places and the call to action reads "Get Instant
  Access" everywhere. Changing `PRICE` updates all of them.

## Things you may still want to change

- **Price.** `$27` is what the page is set to. Change `PRICE` and, if you use a launch
  price, edit the two lines in the `#offer` section that say
  "one-time · no subscription, ever".
- **Branding.** The page is written in the vendor's voice ("I", "my"), which
  suits a solo creator. Rewrite to match how you actually talk to buyers.
- **Support response time.** The guarantee promises a refund when asked. Make
  sure you honour it — persistent refund problems damage network standing.
- **The 14-day window.** It is shorter than the 30 days most vendors on these
  networks advertise, and some affiliates will ask about it. If you want it to
  look more generous, change `14` back to `30` in the guarantee block of
  `index.html` (search for `14-day` and `Fourteen days`) and on
  `refund-policy.html` and `terms-of-use.html`.
- **The `__MACOSX`/`_review` type folders.** None should be uploaded; if your
  editor adds one, delete it first.
