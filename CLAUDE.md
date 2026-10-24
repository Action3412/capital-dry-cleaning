# Capital Dry Cleaning — working notes for Claude

Read this before changing anything. It's the house style and the working rules for this site.

## What this is
A single-page website for Capital Dry Cleaning, an independent, family-run dry cleaners at
11 The Centre, High Street, Halstead, Essex CO9 2AJ (just off the High Street, free parking outside).
Phone 01787 477230. Open since the 1980s. Live at https://capitaldrycleaning.co.uk.
Owner's brother and Ben Jackson both work on it, each with their own Claude session.

## How it's built and deployed
- Everything is in `index.html`: styles, illustrations (inline SVG sprite), script. No build step, no framework.
- `404.html` is the not-found page. `_headers` sets security headers. `netlify.toml` tells Netlify to publish the repo root.
- Netlify deploys the `main` branch automatically. A push is live in about a minute.
- `favicon.svg` is the logo master (CDC letters on a T-shirt, dress and jacket pegged to a hanger).
  `favicon-32.png`, `apple-touch-icon.png`, `images/logo-512.png` and `images/og-image.png` are rendered from it.
- `images/photos.json` lists which real photos exist. The page only requests photos named there;
  every other slot shows the matching blue illustration. Filenames are in `images/README.txt`.
- Google Analytics 4 (`G-F85MXCJDR1`) runs in consent mode behind the cookie notice. Click/scroll events are wired in the last script block.
- Structured data (LocalBusiness) and opening hours live in the head and in the Find us section. Keep them in sync if hours change.

## Working rules
1. Pull before you start (`git pull`), make the change, test it opens cleanly, then commit and push to `main`. Don't leave changes unpushed.
2. Keep it one file. Don't split into separate CSS/JS or add a framework.
3. Don't invent facts. Prices, hours, names, services and offers come from the owners. If something is a guess, say so in the chat and mark it clearly in the page.
4. Opening hours: Mon, Tue, Thu, Fri 9.00am–3.00pm; Wed, Sat 9.00am–1.00pm; Sun closed. Change them in three places if they change: the hours list, the JSON-LD block, and the `close` map in the hours script.
5. Current offer: any duvet, any size, cleaned for £10, ends 14 November 2026. It appears in the promo bar and the Offer section.
6. The owner cards (names, bios, portraits) are parked in an HTML comment after the About section until the owners supply details.

## Look and feel
- Palette (CSS variables at the top of `<style>`): `--navy #17365C`, `--blue #2C6AAE`, `--sky #C9DCEE`, `--ice #EEF3F8`, `--deep #0E2340`, text `#1B2B3F`, muted `#5A6B80`. Accent gold `#C9A24A` for pegs and small details.
- Fonts: Libre Franklin for headings and buttons, Source Sans 3 for body. Both from Google Fonts.
- Plain, confident, un-flashy. Square-ish corners (4px), no pills on nav links, no gradient text, no emoji.
- Illustrations: flat shapes with soft gradients and drop shadows, blue world with one or two warm accents each
  (camel, sage, cream, terracotta, oxblood, mustard, blush). Keep new ones in that family. Draw them as `<symbol>`s in the sprite and place with `<use>`.
- Header is two rows: address + phone + Facebook strip, then logo + nav. Nav collapses to a menu button under 1120px.
- The laundry carousel auto-scrolls continuously and loops; keep that behaviour if you touch it.

## Voice
Write like a person who works in the shop: short sentences, plain words, British spelling, no marketing fluff.
Say what the service is and what it costs. Never sound like AI wrote it.
Good: "Bring it in, or we can collect and deliver for free locally."
Bad: "Experience premium garment care solutions tailored to your needs."

## Things not to touch without asking the owners
Business name, address, phone, hours, prices, the Facebook link, the GA measurement ID, the domain settings in Netlify.
