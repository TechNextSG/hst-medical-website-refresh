# HST Medical website redesign v4: install guide

**For:** McGallen & Bolden · **From:** TechNext · **Date:** 13 October 2026

v4 is the v3 "Carton" design refined after review, offered as an **alternative** to the v2.2 refresh. Install one version only. Like v2.2, it is two
GeneratePress settings files, one CSS file and the graphics. Together they restyle every page of hstmedical.com
within its classic GeneratePress setup. About 20 minutes to install.

**The look:** a clean Japanese medicine carton. White pages, one solid HST-magenta band, facts in ruled panels,
square corners and Figtree headings.
* The homepage gets a two-column hero. The page title and the "We have joined Kowa" line sit on white, and the
  product collage floats on a white card across the edge of a solid magenta field.
* The awards become a row of three, and the Google rating sits beside "Follow @hstmedical".
* Every following homepage section becomes a ruled two-column spread.
* The best sellers become one sideways-scrolling shelf, not 85 cards down the page.
* The store's category sidebar becomes a single bar across the top.
* Pages and posts open on a grey title panel.

**Every word stays in WordPress:** the CSS only places and styles what the editors already wrote. It adds no
text, scripts, templates or plugins.

**New in v4:**
* Lighter type and lines: Figtree headings and hairline rules.
* A calmer header. The logo sits on one balanced row with the menu, and "Online store" is a compact button with a bag icon.
* Jamie (the AI chat) floats in the bottom-right corner of every page. "AI Chat" leaves the desktop menu row but stays in the phone menu.
* Tighter spacing throughout.
* Bigger product images with no borders, and products tagged "Popular!" first in every list.
* Wide page banners (1640 × 624, the Facebook-cover shape) for the main pages and store categories.
* No Quick view button floating over the product cards.
* A clean search box with a joined button, and the categories as flat chips.

All v4 changes are in the last section of the CSS ("14. v4 refinements"), so they are easy to find and adjust.

## Files

| File | What it is |
|---|---|
| `hst-gp-1-global-colors.json` | GeneratePress colour palette (import) |
| `hst-gp-2-typography.json` | GeneratePress type scale (import) |
| `hst-refresh.min.css` | The CSS to paste into Additional CSS. `hst-refresh.css` is the same CSS in readable form, for future edits. |
| `graphics/` | Five health-goal panels, the offer banner (JPG and WebP) and a trimmed logo |
| `graphics/banners/` | 11 wide page banners (JPG and WebP) |

**Not changed:** templates, plugins, hosting, EasyCart settings, the Jamie chatbot (DocuChat), the UnoDock bar,
product data, page content, and every GeneratePress setting other than the colour palette and the type scale.

## Before you start

* **Back up first, and keep the backup.**
  * Appearance › GeneratePress › Import / Export › Export (type: All).
  * Copy the current Additional CSS into a text file.
  * Note the current logo and the images on the Home and Online store pages.
  * Each import takes effect immediately and has no undo button. Re-importing this backup is the undo.
* **Do steps 2 to 7 in one sitting** (or in maintenance mode, or on a staging copy first).
* **Mobile menu breakpoint:** the header styles assume the live setting of 800 px (GP Premium › Menu Plus).

## Install

1. **Back up** as above.
2. **Import the colour palette.** Appearance › GeneratePress › Import / Export › Import:
   `hst-gp-1-global-colors.json`. This replaces only the Global Colors list:
   * the 7 existing colour names get new values;
   * 4 colours are added: Accent 2, Accent deep, Accent tint, Slate.
3. **Import the type scale.** Same screen: `hst-gp-2-typography.json`. This replaces only the Typography list.
4. **Heading font, served from hstmedical.com.**
   1. Appearance › GeneratePress: activate the **Font Library** module.
   2. Open Appearance › Font Library and click **Allow access to Google Fonts**.
   3. Click **Install Google Fonts**, pick **Figtree** with the weights **500, 600 and 700**, then
      **Install Selected**.
   4. Open the installed font, set **Font Display** to **swap** and save.

   If you skip this step, headings use the device's own font and nothing breaks.
5. **Add the CSS.** Customize › Additional CSS: replace the contents with `hst-refresh.min.css`.
   * WordPress's old built-in checker reports "errors" for current CSS such as `:is()` and `:has()`. These are
     false alarms.
   * Tick **"Update anyway, even though it might break your site?"** and Publish.
6. **Graphics** (Media › Add New, WebP preferred), from `graphics/`:
   * **Home page, "Shop by health goals":** replace `hst_newpanels2.001` with `panel-pain-relief` and
     `hst_newpanels2.002` with `panel-cold-cough-flu`, at Full size. Keep their links.
     * Three more panels are ready for later: `panel-beauty-youth`, `panel-kids-vitamins` and `panel-wellness`.
   * **Home and Online store pages:** replace the `Brown-and-White-Simple-Fashion-Sale-Banner-2` image with
     `promo-20-off`, linked to /store/.
     * Alt text: "Storewide: S$20 off when you buy S$80 and above of HST Medical products. Terms and conditions
       apply."
     * Swap or remove the banner whenever the offer changes or ends.
   * **Page banners** (`graphics/banners/`): set each as the page's **Featured image** (Pages › the page › Featured
     image). Upload the WebP.

     | Banner | Pages |
     |---|---|
     | `banner-pain-relief` | Pain Relief; store categories Pain relief, Rheuma-Salve®, Heritage® External Pain Relief |
     | `banner-cold-cough-flu` | Cold, Cough & Flu; store category Cough, Cold & Flu |
     | `banner-look-good-feel-young` | Look good, feel young; store category Beauty supplements |
     | `banner-halal` | Store category Halal |
     | `banner-store` | Online store, Cart, Account, Where to buy, Promotions, and every other store category |
     | `banner-about` | About |
     | `banner-contact` | Contact, Reseller |
     | `banner-shipping` | Shipping |
     | `banner-joinhst` | Jobs |
     | `banner-chat` | AI Chat |
     | `banner-info` | Medical disclaimer, Privacy policy, Resources |

     The store category pages (for example /store/pain-relief/) are ordinary WordPress pages, so their banner is set
     the same way.
   * Optional: Customize › Site Identity › Logo → `hst-logo-trimmed.png`.
7. **Clear the cache:** purge Fast Velocity Minify.
8. **Check** these pages on a phone and on desktop:
   * Home, Pain Relief, Cold Cough & Flu, Online store, a product with options, the cart and checkout, Blog and a
     post.
   * The sticky menu after scrolling.
   * The phone menu open.
   * The phone bar with the Jamie bubble above it.

## Popular products first

Products whose WP EasyCart label is "Popular!" (the red label) are shown first in every product list while the default
sort ("Most Viewed") is chosen. To change which products lead, change their label in EasyCart. The other sort choices
keep EasyCart's own order.

## The floating chat (Jamie)

The live site already loads HST's DocuChat chatbot ("Jamie") on every page. v4 only places its bubble in the bottom-right
corner (above the phone bar on phones) and frames it. Nothing in DocuChat is changed. If the bubble ever disappears,
check that the DocuChat script is still enabled and that "Visible URLs" in DocuChat is empty (meaning all pages).

## The homepage's Ask Jamie paragraphs

The two Ask Jamie paragraphs at the top of the Home page content (the avatar link and the text link) are hidden on the
homepage, because Jamie now floats in the corner of every page. They stay in the editor and come back if the v4 CSS is removed.

## To roll back

Re-import the backup, paste the old Additional CSS back, restore the Home and Online store images
(Page › Revisions) and the logo, then purge Fast Velocity Minify.

## Notes

* **The homepage layout depends on blocks the editors already have:**

  | Hero element | Where it comes from |
  |---|---|
  | Title | The page title |
  | Kowa line | The first H2 in the content |
    | Collage | The Featured image |

  * Every H4 without an image starts a two-column spread: the heading on the left, the next paragraph,
    awards, panels or video on the right.
  * The **last** H4 on the page becomes the closing magenta band.
  * Remove or reorder blocks and the layout still holds; each block just takes the next free place.
* **Colours:** all from Customize › Colors (Global Colors). Accent #d4006a is the magenta band and buttons. It is
  close to the logo's #DB026D and passes contrast on white.
* **Square corners everywhere**, by design: every `border-radius` in the CSS is 0, including the buttons, inputs
  and the plugin controls the CSS restyles.
* **Browser support:** some layout rules use `:has()` (Chrome and Edge 105+, Safari 15.4+, Firefox 121+). In older
  browsers the pages still work, with simpler layouts.
* **After an EasyCart or GeneratePress update,** check the store, a product with options, the cart and the
  checkout. Tested with GeneratePress 3.6.1, GP Premium 2.5.6 and WP EasyCart 6.0.3.
