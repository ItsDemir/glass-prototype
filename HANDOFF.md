# Leal Glass homepage prototype: handoff

Open `index.html` in any browser. It is one file with inline CSS and JavaScript. The only network request is one Google Fonts stylesheet for all three families. There are no images, so nothing else needs to load.

The live site at lealglassinc.com could not be opened from the build environment, because the network policy blocked that host. Everything on the page comes from the facts in the brief. Anything the brief did not state is a marked placeholder, not an invention.

## 1. Design tokens

All tokens are CSS variables at the top of `index.html`.

### Color

* Ink `#070B10`, page background
* Deep `#0A1017` and `#0C1219`, raised surfaces
* Line `rgba(190,225,240,0.14)` for hairlines, and `rgba(190,225,240,0.30)` for hover and field borders
* Text `#E8F1F5`
* Muted `#98A9B5`, 8.15 to 1 on Ink
* Muted high `#A9B8C3`, 9.71 to 1 on Ink
* Aqua `#5CE1E6`, 12.56 to 1 on Ink. Used for primary buttons, eyebrows and small details only
* Aqua ink `#03161A`, text on aqua, 11.79 to 1
* Aqua tint `rgba(92,225,230,0.12)` and aqua line `rgba(92,225,230,0.55)` for selected states
* Chromatic edge: a 1px gradient from aqua through near transparent white to `rgba(255,120,200,0.65)`. Used on the builder card border only
* Indigo glow `rgba(88,92,255,0.22)`
* Card fill `rgba(255,255,255,0.025)`
* Scene wall `#E7EDF1` to `#C3CFD6`, the one light surface on the page
* Review marker `#FFC857`. Prototype only. It is not part of the brand and goes away at launch

### Type

* Display: Unbounded 300 to 500. H1 is `clamp(2.125rem, 1.1rem + 3.2vw, 3.875rem)`, which is 34px on phones and 62px on desktop. H2 is 26px to 44px. H3 is 18px to 22px. Letter spacing is negative 0.02em on H1 and H2, and negative 0.01em on H3. Headings use `text-wrap: balance`
* Body: Instrument Sans 400, 500, 600. 16px to 18px with a 1.6 line height
* Utility: JetBrains Mono 400, 500. 11px to 13px, uppercase, 0.08em to 0.14em tracking
* Prices use tabular numbers

### Space

* Scale: 4, 8, 12, 16, 24, 32, 48, 72, 104
* Container: 1240px maximum, 16px side gutters on phones, 24px from 700px
* Section padding: `clamp(48px, 6vw, 80px)`

### Shape

* 4px for buttons, chips, spec cells and inputs
* 12px for cards, panels and the scene frame
* 28px for the builder card

### Motion

* Hover and focus transitions: 220ms
* Cards lift 4px. Buttons lift 1px with a soft aqua glow
* The one orchestrated moment is the builder redraw: glass fades in over 360ms, the reflection streak sweeps over 800ms, hardware fades in over 300ms
* The glass slab behind the hero drifts on a 9 second loop and is hidden under 900px
* `prefers-reduced-motion` turns off the drift, the redraw and every transition

### Breakpoints

Layouts use grid `auto-fit` with `minmax()` wherever possible. Media queries only handle the nav and a few refinements: 480, 560, 640, 700, 760, 900 (nav collapses), 960 (hero becomes two columns), 1000, 1100 and 1200.

## 2. Placeholders that need real content

Each one is marked on the page with an amber dashed tag, so it cannot be mistaken for finished content.

1. **Product photos.** All eight list rows and six category cards use illustrations and line glyphs. Real photos should show glass edge, translucency and hardware detail. Add a quick view to each row.
2. **Certification badges.** Badge files, the standard each one covers, and the link to the existing Certificates page. Slot is in the proof band, and the footer Certificates link is a prototype link.
3. **Customer reviews and rating.** Real reviews with name, date and product, used with permission.
4. **Installed project photos.** With city and product used.
5. **Warranty summary.** A short summary and a link to the full terms.
6. **Verified pickup address.** The page shows 18361 NE 4th Ct, North Miami, Florida 33179, tagged "Owner to confirm address". The old site also lists 1331 NW 155th Dr, Miami Gardens in its store location link. Confirm which one is correct. The Get directions link and the Google Maps link both use the address shown on the page.
7. **Round glass table top price and sizes.** The row shows "See sizes" and "Price to confirm".
8. **Newsletter offer terms.** The headline is "Get a 10% cash back offer." The brief also asks to say exactly what the visitor gets. Needed: what the 10% applies to, minimum order, expiry and how it is paid.
9. **Tub panel height.** The brief's readout rule gives 78″ H for everything except the sliding tub door, but a bathtub panel is not that tall and its list row has no height. The builder shows "See sizes" for it. Also confirm 78″ H for the hinged door, since its list row has no height either.
10. **Social profile URLs.** Facebook and Instagram.
11. **Footer policy links.** Shipping, returns and warranty are tagged "Link to add". Move the useful ones from the old nine column footer here.
12. **Best price guarantee terms.** The page states the guarantee in one sentence. The terms behind it are not defined in the brief.
13. **Live URLs.** See section 3.
14. **Trade reply time.** For the trade quote page. The brief says to leave a promise you can fill in.

## 3. How links behave in the prototype

* Nav links, hero buttons, the builder button and the six category cards jump to a real place on the page. Category links and the builder button land on the matching row in the Best sellers sheet and highlight it. If a filter had hidden that row, the filter resets to All first.
* Mirror tiles and Round table tops apply the Tiles and tops filter.
* The Wholesale and bulk orders button in the trade banner opens an email to sales@lealglassinc.com with a subject line. It works today, before the trade quote page exists.
* These have no live destination yet. Clicking one shows a toast that names where it will go: Select options on every row, the eight hardware chips, Cart, Certificates, Terms, Privacy, Cookie policy, Facebook and Instagram. Each carries a `data-proto` attribute. To wire one up, replace its `href` and delete the attribute.
* Search is real. It searches the products and hardware names on the page.

## 4. Choices made that you may want to reverse

* The builder opens on Sliding door in Matte black. Black hardware gives the strongest first impression against the pale wall. The brief lists Chrome first. To switch, change `state.finish` in the script. The same object holds the default enclosure type.
* A proof band was added under the trade banner, because item 10 of the audit asks for reviews, project photos, warranty and certification. It was not in the page structure list.
* Chip and filter names match the brief exactly. Product names are split from their specs, as in item 15 of the audit.
* A `noindex` meta tag is set. Remove it at launch.

## 5. Before launch

1. Delete the `--flag` token, the `.flag` and `.todo` classes, the toast element and the `data-proto` script block.
2. Remove the `noindex` meta tag.
3. Replace placeholders using the list above.
4. Add a cookie notice with a real consent tool. The old banner showed raw template variables, so do not reuse its text.

## 6. Next steps

1. **Product detail page with a size and finish configurator.** Reuse the builder scene so the finish preview carries through. Add a size picker that updates the price, a measuring guide, an installation checklist, a warranty summary and a sticky buy bar on mobile.
2. **Trade quote page with plan upload.** Project type, number of openings, widths and heights, hardware finish, delivery or pickup, file upload for plans, and a clear reply time promise.
3. **"Measure your opening" guide.** The audit found no size guide and no measuring help. This is the biggest gap in how buyers understand what a "From" price turns into.

Prompts 3 and 4 from the brief follow after these: the sliding door category page with a sticky filter bar, and a mobile first cart and checkout that shows shipping cost before payment.
