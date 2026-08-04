# Nubo Tools Strategy and Execution Tracker

> **IMPORTANT:** This document is the single source of truth for Nubo's public calculators and practical tools. Read it in full before creating, changing, or retiring a tool. The public product position in [Why Nubo does not predict your baby](/blog/product/why-nubo-does-not-predict-your-baby/) takes precedence over search-volume opportunity.

---

## Purpose

Nubo's tools should make the early months easier to understand and easier to coordinate. They can do transparent date or time arithmetic, show broad evidence-based reference ranges, and organize facts that a parent has entered. They must not predict a baby's behavior, turn normal variation into a score, or act as a medical advisor.

The program has two complementary goals:

1. Give expecting and new parents a genuinely useful, no-login answer to a specific practical question.
2. Show why a private, shared record of what actually happened is more useful than a confident prediction of what will happen next.

The desired parent outcome is: "I understand the context, I can see what happened, and I know what to bring to the people helping care for my baby." It is not: "The website told me what my baby should do."

---

## Nubo's non-prediction standard

### Tools may

- Calculate dates, ages, elapsed time, and totals from visible inputs.
- Show broad age-based reference ranges from named, reputable sources.
- Help parents record, organize, export, or share their own observations.
- Make uncertainty visible and prompt parents to observe their own baby.
- Link parents to a pediatrician, lactation professional, or official public-health source when a question needs professional judgment.
- Use a parent-selected plan as a flexible starting point, provided the result is editable and is never framed as the right schedule for the baby.

### Tools may not

- Predict a baby's next nap, bedtime, feed, developmental outcome, behavior, or health status.
- Calculate an "optimal" wake window, a sleep score, a sleep debt, a schedule grade, or a likelihood that a baby will sleep.
- Tell a parent that a baby should eat, sleep, develop, or react at a precise time.
- Assess feeding adequacy, milk supply, growth velocity, allergy risk, or vaccine eligibility.
- Diagnose, triage, treat, dose medication, or recommend treatment.
- Use AI chat or generated advice to answer health or parenting questions.
- Create compulsive loops through countdowns, warning colors, streaks, achievement badges, or anxiety-oriented notifications.

### Required result language

Use language such as:

- "Here is the date calculation based on what you entered."
- "This is a broad reference range, not a schedule for your baby."
- "Your baby's cues and your care team's guidance matter more than any chart."
- "Here is the history you recorded, ready to review or share."

Do not use language such as:

- "Your baby is due for a nap."
- "You missed the window."
- "Your baby needs X."
- "Your baby is behind."
- "This result means your baby is healthy, unhealthy, eating enough, or not eating enough."

---

## Information architecture

### Public routes

- Directory: `/tools/`
- Detail pages: `/tools/[slug]/`
- Methodology and sources: `/tools/methodology/`

The Resources page at `/resources/` should include a prominent **Free baby calculators and practical tools** callout after the current "Start here" section. It should feature six launch tools, link to `/tools/`, and state: "No predictions, scores, or pressure."

The `/tools/` directory should support category filters and short plain-language descriptions. It should use progressive disclosure: show featured tools first, then category groups. Do not place a wall of every tool card on `/resources/`.

### Categories

1. Pregnancy and dates
2. Baby age and preemie support
3. Sleep references and logged-time summaries
4. Feeding and pumping organization
5. Diapers and daily records
6. Solids and allergen records
7. Growth, milestones, and care preparation
8. Caregiver coordination and return to work
9. Planning and gifts

### Blog embeds

An article can include a compact version of one relevant tool. The complete, canonical experience lives on its own `/tools/[slug]/` page. The article supplies the explanation and context. The tool supplies the practical action. Do not duplicate the full calculator and its SEO copy in multiple articles.

Every embed must end with a neutral next step such as: "Keep the real timeline in one place with Nubo." Never use "Get a personalized recommendation."

---

## Design and content requirements

Every tool page must include:

1. A direct, query-matched H1 and a one-sentence statement of what the tool does.
2. A short input form with clear labels, usable from a phone with one hand.
3. A plain-language result that distinguishes calculation from guidance.
4. A visible source, source version or publication date, and Nubo review date.
5. A concise tool-specific limitations note.
6. A relevant "when to ask a professional" path where the topic has medical sensitivity.
7. Static explanatory content, FAQ, and internal links that can be crawled without JavaScript.
8. A soft connection to the relevant Nubo feature, article, guide, App page, caregiver page, or product page.

### Interaction rules

- Calculations should run locally in the browser. Do not require an account to receive a result.
- Make repeat visits feel effortless: after a valid entry, save that tool's inputs locally in the same browser and restore them automatically on the next visit.
- Recalculate the result from the restored inputs on every visit. Do not treat a stored result as current when source data, the tool version, or a time-based input has changed.
- Store a small, namespaced record per tool, for example `nubo:tools:v1:corrected-age-calculator`. Include only the input fields, result-display state, save timestamp, and tool-data version. Never store a baby's name unless a future tool has an explicit, approved need for it.
- Show a quiet, persistent note near the result: "Saved only in this browser. Nothing is sent to Nubo." Pair it with a one-tap **Clear saved values** control.
- Include a **Start fresh** control that clears the current form and local values, plus an accessible confirmation that the browser-only record was removed.
- Browser-only saving is the default for a tool. Exporting, printing, sharing, or moving data into a Nubo account must always be a separate explicit action.
- State clearly that saved values remain on the device until the parent clears them or clears browser site data. Do not promise recovery after a browser reset, private-browsing session, device change, or storage cleanup.
- For shared-device safety, avoid saving highly sensitive free-text notes unless the parent deliberately selects "Save on this device." This additional confirmation is required for Level C and D tools that accept reaction notes, health measurements, or similarly sensitive details.
- Keep a result printable and copyable. Offer a simple text summary before considering PDF output.
- Use calm, neutral colors. Never use a red result merely because a value is outside a typical range.
- Prefer a range and the factors that affect it over a single, falsely precise number.
- Let a parent change any planning input. The tool must never lock a family into a schedule.

### SEO and schema requirements

- Each tool needs a unique title, description, canonical URL, Open Graph image, and static introductory copy.
- Use `WebApplication` JSON-LD for an interactive tool when appropriate. Use `FAQPage` only when the visible page has a real FAQ section.
- Link from the tool to its related educational article and from that article back to the canonical tool.
- Do not create thin pages that differ only by an age or keyword variation.
- Add tool routes to the sitemap and keep their main explanatory content available in static HTML.

---

## Source, clinical, and privacy governance

### Source hierarchy

Use primary and institutional sources first: AAP and HealthyChildren.org, CDC, WHO, ACOG, Academy of Breastfeeding Medicine, and peer-reviewed research. Do not cite competitor apps, blogs, or AI summaries as a medical or developmental source.

Each implementation task must list its exact source URLs, the data or rules used, and test examples in the tool's implementation notes before release.

### Review levels

| Level | Meaning | Examples | Release requirement |
|---|---|---|---|
| A | Pure date, time, or arithmetic | due date, baby age, elapsed-time total | Product and engineering review |
| B | Educational planning or reference | sleep range, caregiver handoff, pumping work planner | Product, content, and source review |
| C | Health-adjacent education | milk storage, allergen record, milestone navigator | Product, content, and clinical-source review |
| D | Clinical interpretation risk | percentile viewer, vaccine lookup | Explicit owner approval, professional-source review, update owner, and additional privacy review |

### Data and privacy rules

- Do not send a baby's name, email address, birth date, health measurements, caregiver details, tool values, or tool results to Nubo merely to show a result.
- Tool inputs and result state may be saved locally on the visitor's browser according to the interaction rules above. They are not cookies, analytics events, cloud backups, or Nubo account data.
- Keep Level C and D values local unless a parent deliberately exports, shares, or separately chooses to save a sensitive note on the device.
- Never use inputs to create advertising audiences, retargeting, or health profiles.
- If the tool points into Nubo, explain whether information transfers. Default behavior is no transfer, including when a locally saved tool value exists.

---

## Tool inventory and backlog

Status keys: `[ ] PENDING`, `[~] RESEARCH`, `[x] DONE`, `[!] BLOCKED`, `[−] EXCLUDED`.

### Phase 1: trusted foundation

These first tools establish the program's philosophy. Build only after the shared route, source display, disclaimer pattern, analytics events, and methodology page are ready.

| ID | Tool | Route | Level | Status | Related Nubo content | Definition of done |
|---|---|---|---|---|---|---|
| TOOL-001 | Estimated due date calculator | `/tools/due-date-calculator/` | A | `[ ] PENDING` | Pregnancy acquisition, App page | Calculates estimated due date, pregnancy week, and trimester from visible inputs. Labels result as an estimate. |
| TOOL-002 | Baby age calculator | `/tools/baby-age-calculator/` | A | `[ ] PENDING` | What To Expect, first 12 weeks guide | Shows chronological age in days, weeks, months, and years. |
| TOOL-003 | Preemie corrected-age calculator | `/tools/corrected-age-calculator/` | B | `[ ] PENDING` | Fenton preemie growth charts | Shows corrected age and PMA, explains the inputs, and links to the Fenton article. |
| TOOL-004 | Sleep ranges by age | `/tools/baby-sleep-ranges-by-age/` | B | `[ ] PENDING` | Newborn sleep hours | Age selector returns broad sourced total-sleep ranges and observation prompts. No next-sleep output. |
| TOOL-005 | Wake windows by age reference | `/tools/wake-windows-by-age/` | B | `[ ] PENDING` | Newborn wake windows | Age selector returns a broad reference range and sleepy cues. No last-wake-time input, countdown, or nap prediction. |
| TOOL-006 | Feeding patterns by age | `/tools/baby-feeding-patterns-by-age/` | B | `[ ] PENDING` | Newborn feeding schedule, cluster feeding | Shows broad age and feeding-method reference information. No volume prescription or next-feed time. |
| TOOL-007 | Allergen introduction record | `/tools/allergen-introduction-record/` | C | `[ ] PENDING` | Allergen introduction tracker | Records parent-entered introductions and reactions, with a parent-configured calendar. Does not assess risk or tell a parent when to introduce an allergen. |
| TOOL-008 | Return-to-work pumping planner | `/tools/return-to-work-pumping-planner/` | B | `[ ] PENDING` | Exclusive pumping cluster, return-to-work handoff | Creates an editable workday planning worksheet from parent-entered constraints. Does not predict supply or intake. |

### Phase 2: track, organize, and coordinate

| ID | Tool | Route | Level | Status | Related Nubo content | Definition of done |
|---|---|---|---|---|---|---|
| TOOL-009 | Daily baby log totalizer | `/tools/baby-log-totalizer/` | A | `[ ] PENDING` | Why track, first 12 weeks guide | Totals parent-entered sleep, feeds, diapers, or pumping entries. Describes only what was entered. |
| TOOL-010 | Daily diaper record | `/tools/daily-diaper-record/` | B | `[ ] PENDING` | Diaper output guide | Provides a one-day count record and educational reference link. No adequacy determination. |
| TOOL-011 | Breast-milk storage time helper | `/tools/breast-milk-storage-time-helper/` | C | `[ ] PENDING` | Exclusive pumping tracker | Displays source-backed handling information for the parent-selected storage context, exact source version, and no safety guarantee. |
| TOOL-012 | Pediatrician visit prep builder | `/tools/pediatrician-visit-prep/` | B | `[ ] PENDING` | Pediatrician visit article | Produces an editable checklist for questions, logs, measurements, and records. It does not interpret the data. |
| TOOL-013 | Caregiver handoff builder | `/tools/caregiver-handoff-builder/` | B | `[ ] PENDING` | Nanny, grandparent, and return-to-work posts | Produces a parent-controlled handoff summary with routine, contact, and note fields. |
| TOOL-014 | Tummy-time planner and totalizer | `/tools/tummy-time-planner/` | B | `[ ] PENDING` | What To Expect | Helps parents record sessions and see an editable daily plan. It is not a developmental assessment. |
| TOOL-015 | Milestones by age navigator | `/tools/baby-milestones-by-age/` | C | `[ ] PENDING` | CDC milestones bonus post | Shows official age-group checklists with "learn and discuss" framing, never a pass/fail outcome. |
| TOOL-016 | First 12 weeks routine builder | `/tools/first-12-weeks-routine-builder/` | B | `[ ] PENDING` | First 12 weeks guide | Lets a family select what it wants to remember and coordinate. Outputs a flexible tracking checklist, not a baby schedule. |

### Phase 3: expanded planning and reference tools

| ID | Tool | Route | Level | Status | Related Nubo content | Definition of done |
|---|---|---|---|---|---|---|
| TOOL-017 | Trimester calculator | `/tools/pregnancy-trimester-calculator/` | A | `[ ] PENDING` | TOOL-001 | Date arithmetic companion to the due-date tool. |
| TOOL-018 | Pregnancy countdown | `/tools/pregnancy-countdown/` | A | `[ ] PENDING` | TOOL-001 | Shows time until the estimated due date, clearly labelled as date math only. |
| TOOL-019 | Parental-leave return-date planner | `/tools/parental-leave-return-planner/` | B | `[ ] PENDING` | Return-to-work handoff | Calendar planning that also displays baby's chronological age on the selected date. |
| TOOL-020 | Nap-transition reference guide | `/tools/nap-transition-guide/` | B | `[ ] PENDING` | Sleep regressions, sleep-hours article | Age and current nap-count lookup with flexible educational information. No recommendation that a baby must drop a nap. |
| TOOL-021 | Cluster-feeding pattern record | `/tools/cluster-feeding-record/` | B | `[ ] PENDING` | Cluster feeding | A parent-entered timestamp summary and questions-to-bring-to-care guide. No diagnosis or supply assessment. |
| TOOL-022 | First-food readiness guide | `/tools/first-food-readiness-guide/` | C | `[ ] PENDING` | Allergen introduction tracker | Source-backed educational checklist, with a professional discussion path where appropriate. |
| TOOL-023 | Top-9 allergen progress record | `/tools/top-9-allergen-record/` | C | `[ ] PENDING` | Allergen introduction tracker | A broader record view that complements TOOL-007 and avoids duplicate implementation logic. |
| TOOL-024 | Baby meal-planning worksheet | `/tools/baby-meal-planning-worksheet/` | B | `[ ] PENDING` | Feeding content | Parent-selected meal ideas and a printable plan. No nutrition adequacy claim. |
| TOOL-025 | Baby shower registry budget planner | `/tools/baby-shower-registry-budget/` | A | `[ ] PENDING` | Baby shower gifts | Arithmetic and category planning only. |
| TOOL-026 | Newborn essentials timeline | `/tools/newborn-essentials-timeline/` | B | `[ ] PENDING` | Baby shower gifts, first 12 weeks guide | Parent-selected checklist and date planner. |

### Phase 4: conditional tools requiring explicit approval

Do not start these from the normal backlog. Each one needs a separate scope decision and an update owner before implementation.

| ID | Tool | Route | Level | Status | Approval conditions |
|---|---|---|---|---|---|
| TOOL-027 | Infant growth percentile viewer | `/tools/infant-growth-percentile-viewer/` | D | `[~] RESEARCH` | Use official chart data and calculation methods. Show a reference position only, never an alert, diagnosis, or healthy/unhealthy conclusion. Keep inputs local. |
| TOOL-028 | Preemie growth reference viewer | `/tools/preemie-growth-reference-viewer/` | D | `[~] RESEARCH` | Use current Fenton methodology and make the Fenton-to-WHO transition explicit. Require clinical-source review. |
| TOOL-029 | Vaccine schedule lookup | `/tools/child-vaccine-schedule/` | D | `[~] RESEARCH` | Provide a source-linked, jurisdiction-specific official schedule lookup only. Do not calculate catch-up doses or individual recommendations. |
| TOOL-030 | Formula preparation expiry helper | `/tools/formula-preparation-expiry-helper/` | C | `[~] RESEARCH` | Only if exact product-label and public-health rules can be presented without unsafe generalization. |
| TOOL-031 | Poop-color education guide | `/tools/baby-poop-color-guide/` | C | `[~] RESEARCH` | Needs clinician-reviewed escalation copy and source maintenance. It must never diagnose from a color selection. |

### Excluded ideas

| Idea | Status | Reason |
|---|---|---|
| Next nap calculator | `[−] EXCLUDED` | Predicts exact future sleep timing and conflicts with Nubo's product position. |
| Bedtime calculator | `[−] EXCLUDED` | Converts a broad sleep reference into an implied rule for an individual baby. |
| Personalized nap schedule | `[−] EXCLUDED` | Prediction-driven, high-pressure, and incompatible with the no-prediction standard. |
| Sleep score, sleep debt, or schedule grade | `[−] EXCLUDED` | Creates a scorecard and can reward compulsive checking. |
| Bottle-volume or intake-adequacy calculator | `[−] EXCLUDED` | Risks inappropriate feeding guidance and clinical interpretation. |
| Next-feed calculator | `[−] EXCLUDED` | Implies a specific feeding time for an individual baby. |
| Sleep regression diagnostic quiz | `[−] EXCLUDED` | Treats normal variability as diagnosis. |
| Formula mixing calculator | `[−] EXCLUDED` | Product-specific preparation errors can be unsafe. Follow the formula label and professional guidance. |
| Milk-supply predictor | `[−] EXCLUDED` | Makes unsupported clinical and emotional claims. |
| Growth velocity assessment | `[−] EXCLUDED` | Requires clinical interpretation of a trajectory. |
| Allergy-risk calculator | `[−] EXCLUDED` | Clinical-risk determination is outside Nubo's role. |
| Medication, fever, jaundice, dehydration, or symptom calculators | `[−] EXCLUDED` | High-stakes medical triage or dosing is out of scope. |
| AI parenting or medical advisor | `[−] EXCLUDED` | Conflicts directly with the no-AI-medical-advice position. |

---

## Blog and guide integration map

| Existing page | Tool placement | Required framing |
|---|---|---|
| Newborn wake windows | TOOL-005 | Broad range and sleepy cues. No countdown or next-nap result. |
| Newborn sleep hours | TOOL-004 and TOOL-009 | Compare logged total with a broad reference range. No quality score. |
| Newborn feeding schedule | TOOL-006 | Typical patterns only. Do not tell a parent to feed now or a specific amount. |
| Cluster feeding | TOOL-021 | Help record the pattern and prepare a question for a professional if needed. |
| Newborn diaper output | TOOL-010 | Let the parent count what happened. Keep existing escalation information visible. |
| Allergen introduction | TOOL-007 or TOOL-023 | Parent-controlled record and calendar. No reaction evaluation. |
| Fenton preemie growth charts | TOOL-003, later TOOL-028 if approved | Corrected age is arithmetic. Growth interpretation belongs with the care team. |
| Pediatrician visit | TOOL-012 | Organize questions and data, not medical conclusions. |
| Exclusive pumping tracker | TOOL-008 and TOOL-011 | Workday organization and sourced storage guidance, not supply prediction. |
| Returning to work handoff | TOOL-013 and TOOL-019 | Caregiver coordination and calendar planning. |
| Best baby shower gifts | TOOL-025 and TOOL-026 | General planning only. |

---

## Implementation workflow for each tool

1. Confirm the tool is still consistent with the non-prediction standard.
2. Verify the search intent, related content, exact source material, and source update cadence.
3. Write the input, calculation, result, limitation, and escalation copy before implementation.
4. Define at least five test cases, including boundary dates, invalid inputs, and mobile interaction checks.
5. Build the canonical page and any compact blog embed from shared logic.
6. Add metadata, JSON-LD where appropriate, internal links, analytics, source display, privacy notice, local-save behavior, and clear-data controls.
7. Test locally, including keyboard, mobile, no-JavaScript explanatory content, calculations, result copy, initial save, restored state, stale-data recalculation, and clearing saved values.
8. Run `npm run build` and visually verify the tool page and each article embed.
9. Mark the tool complete below and append an execution-log entry. Never remove previous log entries.

### Minimum acceptance checklist

- [ ] Result is deterministic, transparent, and does not make a prediction.
- [ ] No result uses normative, alarmist, or scorekeeping language.
- [ ] Inputs are not sent to a server by default.
- [ ] Valid inputs restore automatically in the same browser, and the result recalculates from them.
- [ ] The page clearly explains local-only storage and has usable Clear saved values and Start fresh controls.
- [ ] Sensitive free-text data uses an additional save-on-this-device confirmation where required.
- [ ] Sources, review date, and limitations are visible.
- [ ] Mobile, keyboard, and screen-reader flows are usable.
- [ ] Related page links are accurate and no link points to unpublished content.
- [ ] Analytics record interaction without capturing health data.
- [ ] Build and visual checks pass.

---

## Measurement plan

Track only privacy-respecting, aggregate behavior:

- Organic entrances to each tool.
- Tool-start and tool-completion events.
- Source-link and related-content clicks.
- Tool-to-App-page and tool-to-store clicks.
- Return visits to a tool or related guide.
- Search Console impressions, clicks, and query themes.

Do not track entered values, baby-specific inputs, or health-related results.

Success is not maximum tool engagement. A successful tool gives a parent a bounded answer quickly and lets them move on with more confidence.

---

## Execution log

> Append new entries here as tools are completed. Format: `[YYYY-MM-DD] TOOL-NNN - Status - Notes`

*(No entries yet.)*

---

*Document version: 1.0 · Created: 2026-08-04 · Strategy anchor: Nubo provides transparent guidance, practical organization, and caregiver coordination. It does not predict a baby or provide medical advice.*
