# WouroYobi Lift – static website

Four self-contained pages (CSS and JavaScript embedded in each file), one shared `images/` folder. No build step, no dependencies. Publish directly with GitHub Pages.

```
index.html          Home: who, what, where, how to start planning
services.html       Services by customer situation
monte-meubles.html  Furniture-lift education page
contact.html        Enquiry: form (mail/WhatsApp handoff) + planner summary
images/             All photographs (see images/README.txt for expected filenames)
```

## Where to change things (inside the `<script>` of each page, top section "CONFIGURATION")

| What | Where |
|---|---|
| Phone, WhatsApp, email, address, VAT, domain | `COMPANY` object |
| Show/hide the "Image slot" labels on empty photo slots | `SHOW_IMAGE_SLOT_LABELS` |
| Pricing values for the planner | `pricingConfig` (section "COST ESTIMATION") |
| Future AI service | `AI_ENDPOINT` (section "FUTURE AI ENDPOINT") |
| Texts (FR/NL/EN) | `translations` object, keys referenced by `data-i18n="..."` |

The configuration block is identical in all four files: when a value changes, change it in all four.

## Open items that need the owner
- **Email**: the invoice shows `oummoulousmane@yahoo.com` (currently used); the promotional graphic shows `info@wouroyobi-lift.be`. Confirm which mailbox is operational.
- **Pricing**: `pricingConfig.configured` is `false`. The planner shows "Estimate prepared: review by WouroYobi required" until real `{ min, max }` values are entered for every entry and `configured` is set to `true`.
- **Photographs**: not yet supplied; every slot shows a labelled placeholder. Alt texts are neutral and must be checked against the real photos.
- **Domain**: canonical and Open Graph URLs use `https://wouroyobilift-bruxelles.be/`.
- **Services not shown** because unconfirmed: packing, dismantling/reassembly.

## Behaviour notes
- Languages FR / NL / EN: saved choice, then browser language, then French. One HTML file per page.
- The Move Planner is deterministic (no AI). Its summary is stored in the browser (`localStorage`) and carried to the contact page.
- The contact form has no backend: it prepares an e-mail (`mailto:`) or WhatsApp message that the visitor sends themselves.
- Printing the planner summary produces an A4 sheet marked "not a final quotation or contract".
- JSON-LD contains only facts from the supplied invoice (company name, address, VAT, phone, email).
