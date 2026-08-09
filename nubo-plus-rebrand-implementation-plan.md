# Nubo Plus Website Implementation Plan

**Status:** Website implementation complete

**Scope:** Standardize the customer-facing paid and access tier as **Nubo Plus** across `www.nubotracker.com`, without changing prices, eligibility, subscription terms, the 30-day device access window, marketplace destinations, or URL structure.
**Decision:** Use **Nubo Plus** as the canonical written name in website copy, metadata, structured data, public summaries, accessibility text, and website source identifiers. Use `PLUS` only for a future compact visual treatment. Do not use `Nubo+` as the canonical website name.

## 1. Approved product language

Nubo Plus is an access tier with several eligible paths:

- an active monthly or annual app subscription;
- an existing lifetime purchase, where available in the app;
- an active device-based access window; or
- a promotional trial.

Website copy should generally say **Nubo Plus access** rather than treating every eligible person as a subscriber. That wording is accurate for device users and trial users.

| Context | Approved language | Avoid |
|---|---|---|
| Canonical product name | Nubo Plus | Nubo+ |
| Paid app option | Nubo Plus app upgrade | Generic paid tier label |
| Subscription holder | Nubo Plus member or Nubo Plus subscriber | Subscription-only wording for every access path |
| Device benefit | Device sync refreshes a 30-day Nubo Plus access window for active phones | A universal or permanent device-access claim |
| Feature availability | Available with Nubo Plus | A subscription requirement where device access is also eligible |
| Trial | Nubo Plus trial | Generic trial label |
| Upgrade CTA | Explore Nubo Plus or Get Nubo Plus in the app | Unclear upgrade action |
| Core product | The free Nubo app, when price is relevant; otherwise Nubo | Basic as the product name |

The phrase “free app” remains correct when comparing prices. It is a price description, not the name of a lesser product tier.

## 2. Fixed product and website behavior

The completed website implementation preserves these rules:

1. Nubo Plus remains listed at `$39.99/year`.
2. Device sync refreshes a 30-day Nubo Plus access window for active phones.
3. The app, device, pricing, FAQ, legal, and indexed URLs remain unchanged.
4. App Store, Google Play, Amazon, and Alexa links remain direct external destinations with `target="_blank"` and `rel="noopener noreferrer"`.
5. The marketing site remains informational. It does not add a local checkout or commerce flow.
6. Astro continues to generate static output. `dist/` is not edited directly.
7. Terms wording remains a name-only update and preserves the existing legal meaning.

## 3. Completed website implementation

### 3.1 Customer decision pages

The core app, pricing, device, comparison, caregiver, Alexa, pumping, and homepage pages now use Nubo Plus consistently in visible text, page titles, descriptions, table headers, ARIA labels, FAQs, and JSON-LD `Offer` names.

- `src/pages/pricing.astro`
- `src/pages/app.astro`
- `src/pages/compare.astro`
- `src/pages/compare/talli.astro`
- `src/pages/device.astro`
- `src/pages/caregivers.astro`
- `src/pages/alexa.astro`
- `src/pages/exclusive-pumping.astro`
- `src/pages/index.astro`

### 3.2 Shared site surfaces

Shared conversion paths, handoff messaging, resource paths, fallback navigation, gift content, and category CTAs are aligned with the same product language.

- `src/components/PlusFollowsDevice.astro`
- `src/components/CaregiverEconomics.astro`
- `src/components/MobileStickyCTA.astro`
- `src/layouts/BlogLayout.astro`
- `src/pages/blog/[category]/index.astro`
- `src/pages/resources.astro`
- `src/pages/404.astro`
- `src/pages/about.astro`
- `src/pages/gift.astro`

### 3.3 Help, legal, and published content

Help content, privacy wording, legal references, and existing articles describe access and features accurately without changing their underlying product, data, or eligibility claims.

- `src/pages/faq.astro`
- `src/pages/privacy.astro`
- `src/pages/terms-of-use.astro`
- `src/content/blog/best-baby-tracker-for-nanny-grandparents.mdx`
- `src/content/blog/free-baby-tracker-no-paywalls.mdx`
- `src/content/blog/grandma-baby-handoff-checklist.mdx`
- `src/content/blog/pumping-tracker-private-data.mdx`

### 3.4 Machine-readable and internal sources

Public summaries and website-only source identifiers are aligned with the customer language.

- `public/llms.txt`
- `public/llms-full.txt`
- `src/data/appFeatureComparison.ts`

The website-only component, data export, row properties, CSS selectors, and related imports use `Plus` or `plus`. This keeps source terminology aligned without changing the rendered product behavior.

## 4. External-surface checklist

The following surfaces are outside this repository and should use the same canonical wording whenever they are updated:

- App Store and Google Play product pages, subscription names, screenshots, descriptions, and release notes;
- app purchase, settings, locked-feature, trial, and restoration copy;
- Alexa skill listing and invocation documentation;
- Amazon product listing images, A+ content, packaging, and inserts;
- customer-support articles, saved replies, subscriber email, and social profile copy; and
- paid campaigns or referral destinations, if any.

Do not make website claims about a specific external surface until that surface has been updated and verified.

## 5. SEO and structured-data rules

- Canonical URLs, route paths, and redirect behavior remain unchanged.
- Visible page titles and descriptions match the underlying page copy.
- `BaseLayout.astro` continues to emit canonical, Open Graph, and X metadata from each page’s props.
- Nubo-owned `Offer` and `SoftwareApplication` names in JSON-LD use Nubo Plus and match the visible pages.
- `llms.txt` and `llms-full.txt` reflect the same price, device-access, and feature information as the rendered site.
- After deployment, request recrawls for `/pricing/`, `/app/`, `/faq/`, `/device/`, `/compare/`, `/caregivers/`, `/alexa/`, and `/exclusive-pumping/` through Search Console when appropriate.

## 6. Validation completed

The implementation was verified with:

1. `npm run build`, which completed successfully and generated 68 static pages.
2. A source audit confirming that the retired tier name is absent from customer-facing and website-source text.
3. A built-output audit confirming the same result in `dist/`.
4. A desktop and mobile review of `/pricing/`, including the Nubo Plus card and device access wording.
5. A rendered FAQ review of Nubo Plus device-access content.
6. A rendered `/app/` review confirming the Nubo Plus comparison header and JSON-LD offer name.
7. A whitespace and typography check for the changed text.

## 7. Definition of done

The website implementation is complete when all of the following are true:

1. Every Nubo-owned customer-facing reference uses Nubo Plus.
2. Visible copy, accessibility text, metadata, JSON-LD, `llms.txt`, and `llms-full.txt` agree.
3. Prices, plan terms, device access behavior, public routes, marketplace links, and static deployment behavior are unchanged.
4. Website source identifiers use the aligned Plus terminology.
5. The Terms of Use wording has received the required owner review.
6. The build passes and the relevant pages are visually checked at desktop and mobile widths.
