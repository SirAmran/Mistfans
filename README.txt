YOYO'S DEVICES: Portable Mini Water-Cooling Fan (/mistfans)
==============================================================
Single-file pages: index.html and learn-more.html (CSS + JS
inlined, no separate style.css/script.js). Images live in /images.

WHAT'S ALREADY DONE
--------------------
✓ Brand: displays as "YOYOS DEVICES" (uppercase, no apostrophe,
  single solid color) everywhere, matching your live site.
✓ Logo + favicon: images/logo.png (nav), images/favicon-32.png
  (browser tab), images/apple-touch-icon.png (iOS home screen).
✓ Product photos: hero, the large feature photo under "Cooler
  air, wherever you go", and all 4 use-case cards (Home / Office
  / Travel / Outdoors) use your real photos. The Office card and
  the large feature photo both use the image you most recently
  sent.
✓ "AC feeling" messaging: added to the hero subtext and the
  "Why You Need This" section as a feeling/sensation ("that AC
  feeling"), not a literal claim that it's an air conditioner,
  keeps it honest while giving visitors the comfort hook you
  wanted.
✓ Demo video: embedded YouTube video on BOTH index.html and
  learn-more.html.
✓ Pricing: 1 unit ₦15,000 (was ₦17,000), 2 units ₦25,000
  (was ₦26,500), 3 units ₦30,000 (was ₦32,000). 2-unit tier
  tagged "Most Popular", 3-unit tier tagged "Best Value".
✓ Order form: Package dropdown, Full Name, Phone, WhatsApp
  (optional), Delivery Address, Special Requests/Gate Code,
  COD notice, confirmation checkbox, Complete Order button.
✓ Order confirmation screen: after a successful submission,
  the form is replaced with an "Order Received" confirmation
  (checkmark, order reference, package, contact number,
  delivery time, payment method, "keep your phone reachable"
  tip, Done button).
✓ Order reference: auto-generated per order in the format
  MISTFAN-MMDDHHMMSS-XX, where XX is two RANDOM letters (not
  fixed), so two orders placed in the same second never get
  the same reference.
✓ Learn More page: full manufacturer specs (battery, voltage,
  charging input, cell type, motor RPM, speeds, material, etc.),
  a real product description, the same demo video embedded,
  "What's in the Box", and care tips.
✓ Animations: big, bouncy "fanned into place" reveals across
  both pages (cards tilt slightly and settle into place one
  after another as you scroll, with a visible cascade delay,
  not the subtle fade from before).

IMPORTANT: SEPARATE ORDER PIPELINE
-------------------------------------
This form is named "mistfan-order" (was briefly "fan-order"),
deliberately different from whatever name the Type 928 form
uses. Netlify Forms treats each named form as a separate
submission stream, so as long as your Gmail/Zapier/Apps Script
automation triggers on the FORM NAME (or a dedicated Netlify
notification rule) rather than "any Netlify form submission",
these orders will already land somewhere separate from Type 928.

To make sure of this before going live:
1. In Netlify: Site settings → Forms → Notifications, add a
   NEW notification (email or outgoing webhook) scoped to the
   "mistfan-order" form specifically, separate from whatever
   notification is set up for the Type 928 form.
2. Point that notification/webhook to its own Gmail filter and
   its own Google Sheet (or a new tab in the same spreadsheet),
   do not reuse the Type 928 Zapier/Apps Script trigger as-is,
   since that one is presumably still filtering/parsing on the
   Type 928 form's field names.
3. The hidden "orderReference" field (MISTFAN-... prefix) is
   included in every submission, so even if both forms
   temporarily land in one place while you're setting this up,
   you can filter/sort on that prefix to tell them apart.

STILL TO DO BEFORE GOING LIVE
-------------------------------
1. META PIXEL ID: index.html <head>, replace PIXEL_ID_HERE
   with your real Pixel ID.

2. WHATSAPP / CONTACT: footer of index.html and
   learn-more.html, replace WHATSAPP_NUMBER_HERE.

3. GO LIVE WITH REAL SUBMISSIONS: inside index.html's
   <script>, find:
     const MOCK_SUBMIT_MODE = true;
   Set this to false once you've confirmed the separate
   Netlify → Gmail → Sheets pipeline above is working for
   "mistfan-order" submissions.

4. Confirm water tank volume and full charge time once you
   have them, not officially published by the manufacturer,
   so the Learn More page currently says so honestly instead
   of guessing a number.

DEPLOY
------
Push this whole /mistfans folder to the same Netlify site as
the Type 928 page, under the /mistfans path. No build step,
plain HTML with inline CSS/JS.
