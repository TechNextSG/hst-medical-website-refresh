# HST Medical website refresh v2.2: install guide

**For:** McGallen & Bolden · **From:** TechNext · **Date:** 12 October 2026

As agreed on the 8 October call, this package holds the GeneratePress settings, one CSS file and the graphics.
Together they restyle every page of hstmedical.com within its classic GeneratePress setup. About 20 minutes to install.

## Files

| File | What it is |
|---|---|
| `hst-gp-1-global-colors.json` | GeneratePress colour palette (import) |
| `hst-gp-2-typography.json` | GeneratePress type scale (import) |
| `hst-refresh.min.css` | The CSS to paste into Additional CSS. `hst-refresh.css` is the same CSS in readable form, for future edits. |
| `graphics/` | Two home-page panels and the offer banner (JPG and WebP), and a trimmed logo |

**Not changed:** templates, plugins, hosting, EasyCart settings, the Jamie chatbot (DocuChat), the UnoDock bar,
product data, and every GeneratePress setting other than the colour palette and the type scale.
**No script is added.** Built and tested against the live site of 9 October 2026.

## Before you start

* **Back up first, and keep the backup.** Appearance › GeneratePress › Import / Export › Export (type: All).
  Copy the current Additional CSS into a text file. Note the current logo (Customize › Site Identity) and the
  images on the Home and Online store pages. Each import below takes effect immediately and has no undo button;
  re-importing this backup is the undo.
* **Do steps 2 to 7 in one sitting** (or in maintenance mode, or on a staging copy first): between the steps the
  site shows a mix of old and new styles.
* **Mobile menu breakpoint:** the header styles assume the live setting of 800 px (GP Premium › Menu Plus). If you
  change it, tell us and we will re-issue the CSS to match.

## Install

1. **Back up** as above.
2. **Import the colour palette.** Appearance › GeneratePress › Import / Export › Import:
   `hst-gp-1-global-colors.json`. This file holds only the Global Colors list, and GeneratePress swaps in that list
   and leaves every other setting alone. The list has the site's 7 colours (same names; 6 get new values) plus 4
   new ones.
3. **Import the type scale.** Same screen, `hst-gp-2-typography.json`. This file holds only the Typography list
   (sizes, weights, line heights; the device's own font for text), which GeneratePress swaps in the same way.
   Header layout, widths, menus, spacing, sticky menu, CSS print method and every other setting stay exactly as
   the site has them.
4. **Heading font (served from hstmedical.com).** Appearance › GeneratePress: activate the **Font Library**
   module. Open Appearance › Font Library. At "Connect to Google Fonts?", click **Allow access to Google Fonts**
   (this lets the admin screen list Google's fonts). Click **Install Google Fonts**, pick **Plus Jakarta Sans**
   with the weights **700** and **800**, then **Install Selected**. Open the installed font, set **Font Display**
   to **swap** and save. The font files are then stored on hstmedical.com, so visitors' browsers never contact
   Google. (Do not add it as a Google font in Customize › Typography.) If this step is skipped, headings use the
   device's own font; nothing breaks.
5. **Add the CSS.** Customize › Additional CSS: replace the contents with `hst-refresh.min.css`.
   WordPress's built-in checker (from 2016) then says *"There are 99 errors which must be fixed before you can
   save."* These are false alarms: it does not know current CSS such as `:is()` and `:has()`, which every
   current browser supports. Tick **"Update anyway, even though it might break your site?"** and Publish.
6. **Graphics** (Media › Add New, WebP preferred), from `graphics/`:
   * **Home page, "Shop by health goals":** replace `hst_newpanels2.001` with `panel-pain-relief` and
     `hst_newpanels2.002` with `panel-cold-cough-flu`, at Full size. Keep their links (/pain-relief/ and
     /cold-cough-flu/).
   * **Home and Online store pages:** replace the `Brown-and-White-Simple-Fashion-Sale-Banner-2` image with
     `promo-20-off`, linked to /store/. Alt text: "Storewide: S$20 off when you buy S$80 and above of HST
     Medical products. Terms and conditions apply." **Swap or remove it whenever the offer changes or ends.**
   * Optional: Customize › Site Identity › Logo → `hst-logo-trimmed.png` (same artwork, empty margins removed,
     so the logo shows slightly larger in the same space).
7. **Clear the cache:** purge Fast Velocity Minify. StaticDelivr needs no purge (new files get new addresses).
8. **Check** on a phone and on desktop: Home, Pain Relief, Cold Cough & Flu, Online store, a product with
   options, the cart and checkout, Blog and a post. Widths: phone, 768 to 800 px, 801 to 1100 px (the menu must
   stay on one row) and desktop. States: the sticky menu after scrolling (desktop and phone), the phone menu
   open, and the phone bar at the bottom with the Jamie bubble above it. Also check that new images look sharp.

## To roll back

1. Re-import the backup from "Before you start" (it restores the colours, the typography and every other
   GeneratePress setting).
2. Paste the old Additional CSS back. Publish.
3. Restore the Home and Online store images (Page › Revisions) and, if it was changed, the logo.
4. Optional: remove Plus Jakarta Sans in Appearance › Font Library.
5. Purge Fast Velocity Minify.

## Notes

* **What the two settings files change, and nothing else:**
  * Global colours: Contrast #222222 → #1f2933, Contrast 2 #575760 → #4b5563, Contrast 3 #b2b2be → #d3dae2,
    Base #f0f0f0 → #e5e9ee, Base 2 #f7f8f9 → #f4f6f8, Base 3 stays #ffffff, Accent #D10056 → #dd1860;
    new: Accent 2 #a8114a, Accent deep #b3124c, Accent tint #fdeef3, Slate #3d4a57.
  * Typography: text in each device's own font, 17 px (16 px on phones); headings 700 (H1 800) at 44 / 32 / 22 /
    18 / 16 px, smaller on tablets and phones; menu 15 px; buttons 15 px semibold; widget titles 13 px capitals;
    footer 14 px.
* **Element colours are in the CSS.** Link, menu, heading, footer, form and button colours and the heading font
  are set in `hst-refresh.css` section 2b (with the same selectors GeneratePress uses), and the link underlines in
  sections 2 and 2b, not in Customize › Colors. Change them in the CSS. Changing the magenta needs the palette
  and the button gradients and EasyCart colour in section 1 (`--hst-stamp`, `--hst-stamp-hover`,
  `--wpec-main-color`). EasyCart's own Design colour and font settings no longer show through on store pages.
* **Logo:** shown up to 88 px tall on desktop (143 × 88 px) and 60 px on phones (98 × 60 px), so the header is
  77 px tall on phones instead of 144 px. Today the logo is 200 × 123 px everywhere. The "A subsidiary of Kowa"
  line becomes about 6 px tall on desktop and 4 px on phones (7 px and 5 px with the trimmed logo). If it must
  stay readable, delete the two `max-height` values for `.site-logo img.header-image` in section 3 to keep
  today's size.
* **Header:** stays full width and laid out as today (logo left, menu right). "Online store" becomes the magenta
  shop button and is drawn at the end of the menu. Moving "Online store" to the end in Appearance › Menus as well
  makes the keyboard order match what is on screen.
* **Footer:** a short light band. At 800 px and below the article list is hidden (Blog is in the main menu) and
  the FDA statement shows as small print with its link underlined.
* **Phone bar (UnoDock) and Jamie bubble (DocuChat):** the CSS recolours the bar to the site palette and enlarges
  its labels to 12 px (delete the rules under "the refresh palette for the dock" in section 13 to keep the bar's
  own colours), moves the Jamie bubble above the bar, and leaves room under the footer so the bar never covers
  the copyright line. Their plugins are not changed. If UnoDock is ever removed, delete section 13.
* **Editors' colours:** bright red and orange text set in the editor shows in slightly deeper shades so it
  passes contrast. The content itself is not edited.
* **Browser support:** some layout rules use `:has()` (Chrome and Edge 105+, Safari 15.4+, Firefox 121+). In older
  browsers the pages still work, with simpler layouts.
* **After an EasyCart or GeneratePress update,** check the store, a product with options and a sale price, the
  cart and the checkout. Tested with GeneratePress 3.6.1, GP Premium 2.5.6 and WP EasyCart 6.0.3.

## For HST to confirm

1. **Accent colour:** the design uses #dd1860. Today's accent is #D10056; the logo magenta is #DB026D. If HST
   prefers one of those, we re-issue the colours file and the matching CSS values.
2. **Logo size** and whether the "A subsidiary of Kowa" line must be readable (see Notes).
3. **The FDA statement** in the footer ("not evaluated by the U.S. Food and Drug Administration"): keep it on a
   Singapore site?
4. **Store categories:** the phone Filters list shows both "Pain relief" and "Pain Relief" (two categories). Merge
   or rename one?
5. **Free delivery wording:** the Promotions page says "SGD 30 and above"; the Shipping page says above SGD 30,
   with SGD 1.99 at SGD 30 and below. Which is right?
