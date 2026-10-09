# Bureau

An editorial business theme for Masthead: studios, agencies, consultants,
freelancers and independent businesses. Large serif display type, hairline
rules, restrained colour, and a site that is built from content and settings
rather than template edits.

```sh
masthead preview      # demo: "Field Office", a design & strategy studio
masthead validate
masthead package
```

## Content model

Masthead has posts and pages. Bureau turns tagged posts into business content;
the tag names live under **Settings → Content structure** and can be renamed.

| Tag            | Becomes        | Uses these post options                                                        |
|----------------|----------------|--------------------------------------------------------------------------------|
| `Services`     | a service      | price, duration, what's included (one per line), icon                           |
| `Work`         | a case study   | client, logo, services used, challenge/approach/solution/results, metrics, gallery, external link |
| `Team`         | a team member  | role, featured image (portrait), profiles; the body is the biography            |
| `Testimonials` | a testimonial  | quote, role, client/company, featured image (photo), logo; the title is the person's name |
| anything else  | a journal article |                                                                             |

The excerpt is the short description everywhere; the body is the full one.

**Reusable testimonials.** A testimonial's *Shown on* field takes slugs
(`marlow-coffee, brand-strategy, anna-de-vries`). The quote then appears on each
of those service, case-study and team pages, and in any Testimonials section.

**Services ↔ work.** A case study whose *Services used* includes a service's
title is listed as a related project on that service's page.

**Featured.** Featured items lead their sections, and any section can be limited
to featured items only.

Shared presentation options on every post: eyebrow, subtitle, featured image
and its description, image position (below / beside / full bleed / above),
focal point, show image / title / details line, full-width content, header
background, accent, card layout (standard / large / text only), button label
and link.

## Pages

Every Bureau page — the six theme pages and ordinary markdown pages — has the
same hero and section system, set from the page editor.

**Hero:** style (editorial, split, banner, minimal), alignment, eyebrow,
headline, *emphasised words* (set in italic accent), introduction, image +
focal point, two buttons. Untick *Show hero* to keep only a screen-reader title.

**Page:** width (standard, narrow, wide, full), background (default, surface,
dark, primary), accent (secondary, primary, monochrome), and toggles for
navigation, breadcrumbs, the closing call to action and the footer.

**Sections:** a reorderable list. Each section picks a type, a layout
(standard / alternate / compact), eyebrow, title, text, image, link, a maximum
item count, *featured only*, and a background.

| Type           | Content comes from                       |
|----------------|------------------------------------------|
| `services`, `work`, `team`, `testimonials`, `journal` | tagged posts |
| `text`         | the section's own title, text and image (about, story, mission) |
| `points`       | the page's **Points** list (values, process steps) |
| `faq`          | the page's **Questions** list (accordion) |
| `stats`, `clients`, `contact` | site settings |
| `cta`          | the section, falling back to the site's call to action |

A section with nothing to show is left out entirely, so an empty team or a site
without testimonials never leaves a gap. Untick *Show* to hide a section without
losing its settings.

The theme pages (**Bureau · Home / Services / Work / About / Contact /
Journal**) differ only in their starting sections, so every page type can be
reshaped into any other. The demo includes `home-freelancer` and
`home-consultant` to show the same homepage template set up for very different
businesses.

## Settings (tokens)

- **Brand:** logo (falls back to the business name as a wordmark), logo height, favicon.
- **Colours:** primary, text on primary, secondary/accent, background, surface, text, muted, borders. Dark and primary bands are derived from these.
- **Typography:** display, heading and body fonts (Google Fonts or system), base size, type scale, display and heading weights, eyebrow style.
- **Layout:** page width, content width, container padding, section and hero spacing, grid gap, hairline dividers.
- **Header & navigation:** header height, nav spacing, sticky header, header button, navigation links (defaults to Home / Services / Work / About / Contact; empty = published pages).
- **Shape & buttons:** corner, button and image radius; solid / outline / text buttons; lettering; arrows.
- **Images & motion:** card image ratio; natural / monochrome / monochrome-until-hover; subtle motion.
- **Call to action:** the primary button (header, closing band, enquiry buttons) and the closing band above the footer. Clear its heading to remove it site-wide.
- **Contact:** email, phone, address, hours, map embed URL (https only), social links.
- **Proof:** statistics and clients.
- **Footer:** introduction, background, links, copyright line.

Spacing tokens accept `clamp()`, which is how the theme scales between phone
and desktop without extra settings.

## Implementation notes

Liquid has no partials, so `templates/layout.liquid` holds everything shared:
header, hero, the section engine, closing band and footer. The theme page
templates are intentionally empty. `templates/post.liquid` renders all five
post kinds.

Accessibility: skip link, one `h1` per page, labelled landmarks and sections,
visible focus states, native `<details>` for the menu and FAQ, alt text fields
on every image, and motion that switches off for `prefers-reduced-motion`.

Demo photography is loaded from picsum.photos and pravatar.cc in preview only.
