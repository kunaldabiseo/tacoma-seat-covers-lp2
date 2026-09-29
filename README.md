# 2024 Toyota Tacoma Seat Covers — LP2

Landing page for **Seat Cover Review** (seatcoverreview.com) promoting Seat Cover Solutions luxury seat covers for the 2024 Toyota Tacoma.

- **Live page:** https://seatcoverreview.com/2024-toyota-tacoma-seat-covers-lp2/
- **Preview (this repo):** https://kunaldabiseo.github.io/tacoma-seat-covers-lp2/

## What the page does

1. The visitor picks a **color** (7 options) and a **coverage** option:
   - Front + Rear — $389 (best value)
   - Front only — $279
   - Rear only — $279
2. Price, button text, the "Your selection" summary and the Part # update instantly.
3. Every buy button on the page (buy box, header, sticky bars, final section) opens the **Seat Cover Solutions checkout** in a new tab with the chosen item already in the cart. Under the item the checkout shows: Your Vehicle, Coverage, Color, Rear Seat (when included) and Part #. The order also carries `Referred By: seatcoverreview.com / lp2`, the button that was clicked, and UTM tags (`utm_source=seatcoverreview`).

The cart is created with Shopify's public (tokenless) Storefront API `cartCreate`. If that call fails, the page falls back to Shopify's public cart link (`/cart/{variantId}:1`). No store login, API key or backend is needed.

## Where to edit

Everything lives in `index.html`. Inside the `<script>` at the bottom:

| What | Where |
|---|---|
| Prices, labels of the coverage options | `SETUPS` |
| Colors and their images | `COLORS` |
| Shopify variant IDs and Part # for each combo | `VARIANTS` |
| Details shown under the item at checkout | `lineDetails()` |
| Store API endpoint | `CONFIG.storefrontApi` |
| UTM tags | `CONFIG.utm` |

If Seat Cover Solutions changes a price, update `SETUPS` (checkout always shows their real price).

## Deploying to the live site

1. WP Admin → WP File Manager → `2024-toyota-tacoma-seat-covers-lp2`
2. Rename the current `index.html` as a backup (e.g. `index-backup-DATE.html`)
3. Upload the new `index.html`
4. WP Rocket → Clear cache

## Tracking

- Google Ads conversion (AW-17495966508) fires on any click to a seatcoversolutions.com link, including the checkout button.
- `begin_checkout` (value, Part #, color, setup) and `cta_click` events go to `dataLayer`.
