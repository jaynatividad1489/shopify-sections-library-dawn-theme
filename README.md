# 🎨 Shopify Sections Library — Dawn Theme Edition

> Production-ready, reusable Liquid sections built specifically for **Shopify's Dawn Theme (v14+)** — following all Dawn conventions, CSS custom properties, and best practices.

![Shopify Dawn](https://img.shields.io/badge/Shopify-Dawn_Theme_v14+-96BF48?style=flat-square&logo=shopify&logoColor=white)
![Liquid](https://img.shields.io/badge/Liquid-Templating-0090D6?style=flat-square)
![Online Store 2.0](https://img.shields.io/badge/Online_Store-2.0-orange?style=flat-square)
![Accessible](https://img.shields.io/badge/Accessibility-WCAG_2.1_AA-blue?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)

---

## ⚠️ Dawn Compatibility First

Every section in this library is built to work **inside Dawn** — not just any Shopify theme. This means:

| Convention | How We Follow It |
|---|---|
| **CSS Custom Properties** | Uses `--color-foreground`, `--color-base-background-1`, `--font-heading-family`, etc. |
| **Dawn Utility Classes** | Uses `page-width`, `button`, `button--primary`, `button--secondary`, `visually-hidden`, `rte`, `center`, `gradient` |
| **Color Scheme Picker** | All sections use Dawn's `color_scheme` setting — works with your theme's color palettes |
| **Section Padding** | All sections use Dawn's standard `padding_top` / `padding_bottom` range settings with responsive scaling |
| **Heading Size Classes** | Uses Dawn's `h0`, `h1`, `h2` classes that inherit your theme typography |
| **Custom Elements** | JavaScript follows Dawn's `customElements.define()` Web Component pattern |
| **Image Handling** | Uses `image_url` + `image_tag` with lazy loading, `srcset`, and `sizes` |
| **Accessibility** | ARIA labels, keyboard navigation, `focus-visible`, `prefers-reduced-motion` |
| **Dawn Components** | Loads `component-card.css`, `component-badge.css`, `component-price.css` where applicable |
| **Translation Keys** | Schema uses `t:sections.*` keys for full i18n compatibility |

---

## 📦 Sections Included

| Section | File | Description |
|---|---|---|
| 🖼️ **Hero Banner** | `sections/hero-banner.liquid` | Full-width image banner with overlay, heading, subtext, dual CTA buttons |
| 💬 **Testimonials Slider** | `sections/testimonials-slider.liquid` | Accessible customer review slider with star ratings, autoplay, swipe support |
| ❓ **FAQ Accordion** | `sections/faq-accordion.liquid` | Native `<details>` accordion with single-open mode and rich text answers |
| 🛍️ **Featured Products** | `sections/featured-products.liquid` | Product grid using Dawn's card system with badges, hover image, quick add |

**Supporting Files:**
```
snippets/
  section-header.liquid   ← Reusable heading/subheading component
  icon-star.liquid        ← SVG star icon for testimonial ratings

assets/
  section-hero-banner.css
  section-testimonials.css
  section-faq.css
  section-featured-products.css
```

---

## 🚀 Installation

### Method 1 — Shopify Theme Editor (No CLI needed)

1. In your Shopify Admin, go to **Online Store → Themes**
2. Click **Actions → Edit Code** on your Dawn theme
3. For each section:
   - Go to `sections/` → Click **Add a new section**
   - Paste the `.liquid` file content → Save
4. For each CSS file:
   - Go to `assets/` → Click **Add a new asset**
   - Create a blank file with the correct name → Paste CSS → Save
5. For snippets:
   - Go to `snippets/` → Click **Add a new snippet**
   - Paste content → Save

### Method 2 — Shopify CLI (Recommended for developers)

```bash
# Clone this repo
git clone https://github.com/jaynatividad1489/shopify-sections-library.git
cd shopify-sections-library

# Copy files into your Dawn theme
cp sections/*.liquid  /path/to/your-dawn-theme/sections/
cp snippets/*.liquid  /path/to/your-dawn-theme/snippets/
cp assets/*.css       /path/to/your-dawn-theme/assets/

# Push to your store
shopify theme push
```

### Method 3 — Development Store (Test first)

```bash
# Start a local dev session on your Dawn theme
shopify theme dev --store=your-store.myshopify.com
```

---

## 🛠️ Section Details

### 🖼️ Hero Banner
**File:** `sections/hero-banner.liquid` + `assets/section-hero-banner.css`

Full-width hero section with background image support, color overlay, and dual CTA buttons.

**Key Settings:**
- Background image (with responsive `srcset`)
- Overlay opacity (0–90%)
- Section height (300–900px)
- Content alignment (Left / Center / Right)
- Color scheme (uses Dawn's palette)
- Subheading, heading (with size and tag selection), rich text body
- Primary + Secondary buttons (labels + URLs)

**Dawn Integration:**
- Uses `.button.button--primary` and `.button.button--secondary`
- Uses `page-width` container
- Uses `color_scheme` setting → works with all Dawn color palettes
- Uses `caption-with-letter-spacing` for subheading

---

### 💬 Testimonials Slider
**File:** `sections/testimonials-slider.liquid` + `assets/section-testimonials.css`

Auto-playing testimonials slider built as a Web Component (`<testimonials-slider>`).

**Key Settings:**
- Heading + subheading
- Autoplay toggle + speed control (2–8 seconds)
- Quote text size (body or subtitle)
- Up to 12 testimonial blocks

**Per Block:**
- Star rating (1–5, rendered with `icon-star` snippet)
- Quote text
- Author name + title
- Optional author photo (with fallback to initials avatar)

**Dawn Integration:**
- Uses `customElements.define()` Web Component pattern (same as Dawn's native JS)
- Uses `color_scheme` and `page-width`
- Keyboard accessible (Arrow keys for navigation)
- Touch/swipe support
- Pause on hover
- Uses `icon-caret` snippet for prev/next arrows

---

### ❓ FAQ Accordion
**File:** `sections/faq-accordion.liquid` + `assets/section-faq.css`

Accessible FAQ accordion using native HTML5 `<details>` / `<summary>` elements, wrapped in a `<faq-accordion>` Web Component for single-open behavior.

**Key Settings:**
- Heading + subheading
- Single-open mode (only one FAQ open at a time)
- Optional CTA prompt (e.g., "Still have questions? Contact us")
- Up to 20 FAQ blocks

**Per Block:**
- Question text
- Rich text answer (supports links, lists, bold, etc.)
- Open by default toggle (per item)

**Dawn Integration:**
- Uses native `<details>` / `<summary>` — no JS needed for basic functionality
- Uses Dawn's `.rte` class for rich text styling
- Uses `icon-caret` snippet for the expand/collapse icon
- Uses `color_scheme`, `page-width`, and `.link` class
- ARIA expanded attributes on summary elements

---

### 🛍️ Featured Products
**File:** `sections/featured-products.liquid` + `assets/section-featured-products.css`

Product grid section that hooks into Dawn's existing card, price, and badge component CSS.

**Key Settings:**
- Collection picker
- Products to show (2–12)
- Columns on desktop (2–5)
- Image ratio (Adapt / Portrait / Square)
- Show hover/secondary image
- Show vendor
- Enable quick add button
- View All button

**Dawn Integration:**
- Uses Dawn's `component-card.css`, `component-price.css`, `component-badge.css`
- Uses Dawn's `.product-grid`, `.grid`, `.card`, `.card__media` classes
- Uses Dawn's `product-form` custom element for cart adds
- Uses `sold_out_badge_color_scheme` and `sale_badge_color_scheme` global settings
- Translation keys: `products.product.add_to_cart`, `products.product.sold_out`, etc.

---

## 📁 Full File Structure

```
shopify-sections-library/
│
├── sections/
│   ├── hero-banner.liquid
│   ├── testimonials-slider.liquid
│   ├── faq-accordion.liquid
│   └── featured-products.liquid
│
├── snippets/
│   ├── section-header.liquid
│   └── icon-star.liquid
│
├── assets/
│   ├── section-hero-banner.css
│   ├── section-testimonials.css
│   ├── section-faq.css
│   └── section-featured-products.css
│
└── README.md
```

---

## 📋 Upcoming Sections

- [ ] Announcement Bar (with countdown timer)
- [ ] Image + Text Split (50/50 with media)
- [ ] Product Tabs (by collection or tag)
- [ ] Newsletter Signup (Klaviyo / Email integration)
- [ ] Before/After Image Slider
- [ ] Icon Columns (Feature highlights)
- [ ] Recently Viewed Products
- [ ] Countdown Timer

---

## 🤝 Contributing

Found a bug? Have a section idea? PRs are welcome!

1. Fork the repo
2. Create your branch: `git checkout -b feature/my-new-section`
3. Run `shopify theme check` to validate before pushing
4. Open a Pull Request

---

## 👤 Author

**John Venedick Natividad**
Senior Shopify Developer & CRM Implementation Specialist
14+ years building eCommerce experiences for global brands

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat-square&logo=linkedin)](https://linkedin.com/in/jaynatividad)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-181717?style=flat-square&logo=github)](https://github.com/jaynatividad1489)
[![Email](https://img.shields.io/badge/Email-Contact-D14836?style=flat-square&logo=gmail&logoColor=white)](mailto:jaynatividad1489@gmail.com)

---

## 📄 License

MIT — free to use in personal and commercial Shopify projects.
If this helped you, a ⭐ star is always appreciated!
