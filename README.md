# Imperial Scent House — Landing Page Plan

A premium dark + gold e-commerce landing page for the perfume brand, with full catalog, cart, checkout, and WhatsApp ordering.

## Scope

Single-page React app (TanStack Start web_app scaffold) with smooth scroll sections, a slide-out cart, and a checkout modal. No real payment processing — Cash on Delivery + manual payment methods (Easypaisa / JazzCash / Bank Transfer), with order confirmation sent via WhatsApp deep link.

## Sections (in order)

1. **Sticky Nav** — ISH logo, links (Best Sellers, Collection, Oud, Reviews), cart icon with count
2. **Hero** — Headline "Feel Royal. Smell Premium — Without Luxury Prices", subtext, two CTAs (Shop Now / View Collection), trust badges (COD, Fast Delivery, Premium Oils), hero perfume bottle visual
3. **Why Choose Us** — 5 feature cards with gold icons
4. **Best Sellers** — 8 featured product cards (Dior Sauvage, Aventus Creed, Baccarat Rouge, Blue de Chanel, Gucci Oud, Dunhill Desire, CK Eternity, One Million) with image, name, price, 5-star rating, Add to Cart, Quick Buy
5. **Full Collection** — All ~55 perfumes from poster with search bar, category filter chips (Fresh / Oud / Strong / Sweet / All), sort-by-price toggle, responsive grid
6. **Oud Collection** — Separately styled darker section, 8 oud products with smoky visual treatment
7. **Limited Offer Banner** — "Buy 2 → Rs.300 OFF, Buy 3 → Free Delivery", Grab Offer CTA
8. **Product Details** — Volume 50ml, Extrait de Parfum, 8–12h longevity, premium packaging
9. **Reviews / Social Proof** — 3–6 testimonial cards with stars
10. **Final CTA** — "Smell Premium. Order Now." + Place Your Order button
11. **Footer** — Brand, phone numbers (+92 318-6775756, +92 340 2660364), payment methods, tagline "Feel Royal. Every Moment."

## Interactive features

- **Cart drawer** (Sheet) — add / remove / quantity +/-, live subtotal, auto-apply offer (Buy 2 = Rs.300 off, Buy 3 = free delivery message), Checkout button
- **Checkout modal** — Name, Phone, Address, Payment method (COD default, Easypaisa, JazzCash, Bank Transfer); on submit composes a WhatsApp message with order details and opens `wa.me/923186775756`
- **Floating WhatsApp button** (bottom-right, mobile + desktop)
- **Sticky mobile "Buy Now" bar** when scrolled past hero
- **Quick Buy** — adds product + opens checkout immediately

## Design system

- Background: deep navy-black `#0a0e1a` → `#020308` gradient
- Gold accents: `#d4a84c` primary, `#f0d78c` highlight
- Fonts: Playfair Display (headings, royal serif) + Inter (body)
- Cards: subtle gold border `rgba(212,168,76,0.2)`, soft glow on hover
- Animations: fade-in on scroll, gentle hover lift on cards, gold shimmer on primary buttons
- Mobile-first, fully responsive grid (1 / 2 / 3 / 4 cols)

## Technical details

- Stack: TanStack Start web_app artifact (Vite + React + Tailwind + shadcn/ui)
- State: `useState` for cart in a `CartContext`; persisted to `localStorage`
- Data: single `products.ts` array with `{id, name, price, category, badge?}`; categories inferred (Fresh / Oud / Strong / Sweet / Designer)
- Product images: use the uploaded ISH bottle (`src/assets/ish-bottle.jpg`) as the universal product visual for v1 (all bottles same shape per the poster); oud collection uses a generated oud/smoke visual
- Logo: extract/recreate "ISH" gold crest as small SVG/text mark in nav and footer
- WhatsApp link format: `https://wa.me/923186775756?text=<encoded order summary>`
- SEO: title "Imperial Scent House — Luxury Inspired Perfumes in Pakistan", meta description, OG tags, semantic H1, alt text, JSON-LD `Product` + `Organization`
- No backend needed for v1 — checkout goes through WhatsApp. Lovable Cloud can be added later if real order storage is needed.

## Out of scope (v1)

- Real payment gateway integration
- Individual product detail pages (cards open a quick-view dialog instead)
- Admin panel / order database
- User accounts

## Open question

I'll use the uploaded poster's bottle photo as the product image for all perfumes (they share the same ISH bottle design). If you want per-product unique imagery, that's a follow-up generation pass after the page is built.
