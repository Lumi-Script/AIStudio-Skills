---
name: "frontend-design"
description: >
  Universal design constitution and domain-specific architectural guidelines
  for building distinctive, production-grade frontend web applications. Use when
  building or restyling websites, landing pages, SaaS dashboards, e-commerce stores,
  games (2D/casual), 3D spatial apps (Three.js/WebGL), educational simulations,
  mobile web apps, scientific tools, or creative portfolios. Enforces anti-AI
  slop rules, zero-pill discipline, typographic hierarchy, viewport presence,
  and high-fidelity image asset generation.
---

# Universal Frontend Design Constitution

This skill guides the creation of distinctive, production-grade frontend
interfaces that avoid generic "AI slop" aesthetics. Implement real, working code
with exceptional attention to aesthetic details, domain-specific visual
languages, and intentional design choices.

--------------------------------------------------------------------------------

## 0. Order of Resolution & First Principles

When design requirements or constraints conflict, resolve them in this exact
order:

1.  **Function**: Every interactive control must have a working handler; no dead
    clicks, mock stubs, or placeholder boxes.
2.  **Legibility & Accessibility**: WCAG AA contrast (4.5:1 text, 3:1 large),
    visible focus rings (`focus-visible`), touch targets $\ge 40\text{px}$
    (mobile $\ge 44\text{px}$), `prefers-reduced-motion` compliance.
3.  **Layout Integrity**: Desktop baseline is 1440px wide
    ($900\text{px}$–$1200\text{px}$ content container width or full-width
    sidebar layout). Nothing overflows, clips, or wraps in a way that breaks
    layout. Single-line controls with truncation escape hatch.
4.  **Spatial & Typographic Math**: Container outer padding $\ge$ inner padding
    between children (minimum container padding 16px). Button padding:
    horizontal $\approx 2\times$ vertical (`py-2 px-4`). Nested radius math:
    $r_{\text{inner}} = r_{\text{outer}} - \text{padding}$.
5.  **Aesthetic Direction**: Domain-native visual language, intentional
    typography pairings, curated palette, and anti-slop restraint.

*A lower-priority rule never justifies violating a higher one.*

--------------------------------------------------------------------------------

## 1. Domain-Native Aesthetics & Anti-Slop Bans

AI-generated interfaces look generic because models default to purple gradients,
rounded-2xl cards with 1px translucent borders, floating stat boxes, sparkle
icons, and generic verbs. Every interface must look like it was crafted by a
human designer with taste for a specific domain.

### A. Zero-Pill & Metadata Discipline

-   **No Static Pill Enclosures**: Never wrap metadata (categories, tags, dates,
    statuses, scores, read times) in rounded pill boxes, bordered chips, or
    colored capsules. Render metadata as **clean, unboxed text** with subtle
    typographic separators (`·`, `/`, `-`).
-   **Static Metadata vs. Interactive Filter Controls**:
    -   **Static Text Metadata (NO PILLS)**: Informational labels (tags,
        timestamps, category names, counts, publication dates). Must be rendered
        as quiet inline text.
    -   **Interactive Filter Controls (BUTTONS/TABS ALLOWED)**: Segmented
        controls, filter bars, and state selectors that trigger client-side
        filtering when clicked are functional button elements (`<button>`). They
        may have active/inactive visual states, styled with clean segmented
        backgrounds rather than garish candy badges.
-   **No Header Badges or Compound Pill Islands**: Avoid secondary pill tags
    attached to brand names and compound metric clusters in the header.
-   **Nav Links as Clean Typography**: Primary navigation links must be text
    with subtle hover underlines, never filled capsule buttons.
-   **No Badge Sandwich on Cards**: Cards must lead directly with the primary
    title or a quiet 1-line text kicker, never a pair of pill badges on top.

```tsx
// ❌ DON'T: Static metadata wrapped in pill boxes / bordered chips
<div className="flex items-center gap-2">
  <span className="bg-slate-100 border border-slate-200 rounded-full px-2 py-0.5 text-xs text-slate-700">Robotics</span>
  <span className="bg-emerald-50 text-emerald-700 rounded-full px-2 py-0.5 text-xs">Published 2026</span>
</div>

// ✅ DO: Clean unboxed metadata with typographic separators
<div className="flex items-center gap-2 text-xs text-slate-500">
  <span>Robotics</span>
  <span aria-hidden="true">·</span>
  <span>Published March 2026</span>
  <span aria-hidden="true">·</span>
  <span>4 min read</span>
</div>

// ✅ DO: Interactive filter tabs / segmented controls (functional buttons with click handlers)
<div className="flex items-center gap-1 p-1 bg-slate-100 rounded-lg">
  <button onClick={() => setFilter('all')} className={`px-3 py-1.5 text-xs font-medium rounded-md transition-colors ${filter === 'all' ? 'bg-white text-slate-900 shadow-sm' : 'text-slate-600 hover:text-slate-900'}`}>
    All Projects
  </button>
  <button onClick={() => setFilter('hardware')} className={`px-3 py-1.5 text-xs font-medium rounded-md transition-colors ${filter === 'hardware' ? 'bg-white text-slate-900 shadow-sm' : 'text-slate-600 hover:text-slate-900'}`}>
    Hardware
  </button>
</div>
```

### B. Eradicating Mechanical Pseudo-Technical Clutter

-   **No Code-Comment Headers**: Prohibit prefixing section headers or card
    titles with comment syntax (`//`, `/* */`, `>_`, `#`) or uppercase
    snake-case identifiers. Use clean, natural title-case prose.
-   **Editorial Numbering vs Mechanical Prefixes**:
    -   **BANNED**: Mechanical/code-style prefixes (`// 01 ARCHITECTURE`, `01 //
        SERVICES`, `>_ DISCOVER`, `FEAT_01: AUTOMATION`).
    -   **ALLOWED**: Natural, human editorial numbering for curated
        chapter/service lists (`01. Strategy & Research`, `02. Full-Stack
        Engineering`, `Chapter 1: The First Principle`).
-   **No Fake Compiler or Execution Tags**: Prohibit mock status flags
    (execution IDs, compiler modes, verification flags). Do not invent fake
    versioned product names (e.g., "SYNTHEX v4.8-CORE", "NEXUS ENGINE v2"), fake
    API versions, or fake system status indicators (e.g., "ONLINE // LATENCY:
    1.4s", "INVARIANTS: VERIFIED") unless the prompt explicitly requests a
    system monitoring console.
-   **No Ornamental Footer Engines**: Prohibit pinned bottom status bars
    boasting fake background engines, active threads, or buzzword telemetry
    tickers. Footers must only contain quiet copyright, site links, or real user
    actions.
-   **No Hallucinated Cockpit Scoreboards**: Prohibit arbitrary single-number
    AI/innovation scores (e.g., "92/100 INNOVATION SCORE"), fake percentage
    breakdowns (e.g., "NOVELTY: 94%, FEASIBILITY: 88%"), and fabricated tier
    classifications (e.g., "TIER 1 // TRANSFORMATIVE") unless the prompt
    explicitly requests a scoring interface.

```tsx
// ❌ DON'T: Code comments or mechanical snake-case prefixes
<h3 className="text-lg font-mono">// 01_CORE_PIPELINE</h3>
<span className="text-xs font-mono">STATUS: ONLINE // LATENCY: 12ms</span>

// ✅ DO: Natural editorial title case (with optional clean numerical index)
<h3 className="text-lg font-semibold text-slate-900">01. Automated Pipeline Engineering</h3>
```

### C. Component Architecture & Spatial Presence

-   **Whitespace Over "Cards Within Cards"**: Prohibit nesting rounded bordered
    boxes inside larger bordered containers. Separate content using whitespace
    margins (`2rem`–`3rem`) and subtle hairline dividers (`1px solid
    rgba(0,0,0,0.06)`).
-   **Single-Elevation Depth**: Maximum 1 level of card elevation per screen.
-   **Motif Propagation**: Establish a single governing visual idea (e.g.
    consistent radius scale, hairline divider style, or asymmetric offset) that
    propagates across sections in transformed ways, avoiding repetitive
    identical card clones.
-   **Density Orchestration & Section Rhythm**: Pace attention deliberately by
    alternating dense explanatory sections with airy proof or media rest
    sections.
-   **Focal Anchor**: Each viewport frame must have exactly ONE dominant visual
    anchor; competing equal weights (multiple primary CTAs or rival
    high-contrast banners) read as indecision.
-   **No "Desert Island" Viewport Collapse**: Prohibit shrinking desktop apps
    into a single 300px mobile card floating in an empty void. Design for a
    1440px-wide viewport unless the prompt explicitly specifies mobile.
-   **No "Everything Store" Overcrowding**: Prefer 3–5 well-developed content
    sections over 8+ shallow ones. For e-commerce or marketplaces, show 1
    hero/promotional area + 1 featured collection + 1 secondary collection at
    most.

### D. Typographic Hierarchy, Font Selection & Tabular Discipline

-   **Font Selection & Anti-Defaulting Rule**: Never use Inter, Geist, Space
    Grotesk, or Roboto as a lazy default for display, marketing, or distinctive
    brand surfaces. Pair a characterful display face with a complementary body
    face chosen deliberately for the domain.
-   **The 2+1 Font Rule**: Every application must use at most **two font
    families** (1 expressive display face + 1 readable body face) plus at most
    **one monospace outlier** strictly for data tables, metrics, or code.
    -   *Display / Hero / Brand*: High-character faces (e.g., `Syne`, `Clash
        Display`, `Cormorant Garamond`, `Instrument Serif`, `Cabinet Grotesk`,
        `Fraunces`, `Cinzel`).
    -   *Body Prose*: Refined legibility (e.g., `Plus Jakarta Sans`, `Satoshi`,
        `General Sans`, `Source Serif 4`, `Lora`).
    -   *Data & Telemetry*: Always pair with tabular numerals (`font-mono
        tabular-nums`, `JetBrains Mono`, `IBM Plex Mono`).
-   **Strict Type Scale**: Refined Display (20px–36px), Body (15px–16px, 1.5–1.7
    line-height, measure 65–75ch), Muted Metadata (12px–13px). Maximum 2 active
    weights (Regular 400, SemiBold 600).
-   **No Orphan Headline Words**: Always apply `text-wrap: balance` (or
    `max-w-2xl` width constraints) to headlines to prevent isolated single-word
    trailing lines.
-   **Dark Mode Optical Compensation**: Light text on dark surfaces requires
    subtle optical compensation (slightly heavier weight or `tracking-wide` /
    `+0.01em`) to prevent spindly, low-legibility type.
-   **Tabular Numerals (`font-variant-numeric: tabular-nums`)**: All numbers in
    tables, dashboards, and spreadsheets must use tabular numerals or monospace
    fonts for vertical alignment.
-   **No All-Caps Shouting**: Prohibit uppercase micro-labels and technical
    lead-ins.
-   **No Ghost Typography / Watermarks**: Absolutely prohibit placing large,
    low-opacity ghost words or phrases behind headings, hero sections, or
    content areas (e.g., giant faded "MEET THE BATCH" text behind page content).
    All visible text must be readable, purposeful content.

### E. Visual Restraint & Icon Decoupling

-   **No Line-by-Line Decorative Icons**: Do not prefix text lines, labels, or
    stats with decorative emoji or icons.
-   **No Table Row Dot Scatter**: Do not prefix every row in a table column with
    a colored status dot or badge icon.
-   **Affordance-Only Icons**: Reserve icons strictly for functional interactive
    affordances (search, expand, sort, media).

### F. Color & Contrast System

-   **60-30-10 Color Distribution**: Allocate color with discipline:
    -   **60% Dominant Neutral Canvas**: Clean background field (pure off-white
        or deep dark slate).
    -   **30% Structural Surfaces**: Subdued card backgrounds, hairline borders,
        and muted typography.
    -   **10% Accent Budget**: High-intent accent color concentrated strictly at
        primary action points (CTAs, active tabs, focused states).
-   **Sophisticated Neutrals**: Tint neutrals with $<5\%$ saturation, strictly
    warm or strictly cool, not mixed. Avoid the default warm-cream background
    with terracotta accents (the generic AI tell).
-   **Surface Contrast**: Background-to-container brightness delta $\le 12\%$
    (dark mode), $\le 7\%$ (light mode). Supply container boundaries with a soft
    shadow *or* a hairline border (one, not both; avoid ghost cards).
-   **No Hue-Only State Signaling**: Never convey critical semantic state
    (success, warning, error) by color alone. Always pair status colors with an
    explicit text label or icon for color-blind accessibility.
-   **Measured Scrims for Media Overlays**: When text sits on photography or
    video, apply a measured contrast scrim (`bg-gradient-to-t from-black/80
    via-black/40 to-transparent`) ensuring at least 4.5:1 contrast across all
    media luminance frames.

### G. Motion & Interaction Latency Budgets

-   **Routine Feedback $\le 200\text{ms}$**: Micro-interactions, hover states,
    and button presses must respond within 100–200ms using smooth settling
    curves (`cubic-bezier(0.16, 1, 0.3, 1)`).
-   **Compositor-Only Properties**: Only animate `transform`, `opacity`, or
    `filter`. Never animate layout geometry (`width`, `height`, `top`, `left`,
    `margin`) on scroll or hover.
-   **Zero-Latency Content Availability**: Critical instructions, values, and
    controls must be immediately reachable in the DOM without waiting for
    scroll-reveal animations.

### H. Social Proof & Quantitative Rigor

-   **Claim-to-Proof Adjacency**: Place external evidence (metrics, logos,
    testimonials) adjacent to the specific claim it substantiates (distance $\le
    1$ section).
-   **Quantitative Precision**: Quantitative claims must include explicit units,
    timeframes, and context (e.g. `+140% Qualified Inbound Leads in 6 Months`,
    not vague vanity metrics).
-   **Attributable Testimonials**: Testimonials must include full name, role,
    organization, and a concrete before/change/outcome statement.

### I. Overlay & Sticky Surface Governance

-   **15% Mobile Sticky Cap**: The aggregate height of all fixed/sticky elements
    (top navigation + promotional banner + floating bottom CTA) must NEVER
    exceed 15% of the mobile viewport height.
-   **No Arrival Popups**: Modals and promotional prompts require $\ge
    10\text{s}$ dwell + user interaction intent; never fire on first page load.

--------------------------------------------------------------------------------

## 2. Top Bar Contract

Every top navigation bar follows a strict one-row, three-zone contract:

$$\text{[Brand title, one line]} \quad\text{—}\quad \text{[4–6 nav links, 1–2 word labels, single-line]} \quad\text{—}\quad \text{[1–2 primary actions]}$$

-   **Exhaustive Contract**: The header contains exactly these three zones and
    nothing more. No taglines, descriptors, status tickers, or second rows.
-   **Brand Zone**: A single text element (wordmark in the display face). No
    adjacent descriptor, subtitle, location badge, or subtext in the DOM.
-   **Regional / B2B Subtitles**: Regional trust markers (e.g., "Munich
    Facility", "Made in Germany", "ISO 9001 Certified") belong in the **Hero
    Section**, **About Section**, or **Footer**, NEVER attached to the top
    navigation brand mark.
-   **Nav Links**: Text links with subtle hover underlines. If nav items exceed
    5, hide items 6+ behind `hidden xl:flex` or a "More" dropdown.
-   **Single-Line Controls**: Labels inside buttons, links, segmented controls,
    and tabs must read on one line (`whitespace-nowrap shrink-0`). When labels
    are dynamic or viewports narrow, use `truncate` with a `max-width`.

```tsx
// ❌ DON'T: Brand lockup with subtitle tags, location chips, or extra metadata
<header className="flex items-center justify-between px-6 py-4">
  <div className="flex items-center gap-2">
    <span className="text-xl font-bold">Apex Industrial</span>
    <span className="text-xs bg-slate-100 rounded px-1.5 py-0.5">Munich Facility</span>
    <span className="text-xs text-slate-400">// Precision Engineering</span>
  </div>
  ...
</header>

// ✅ DO: Clean 3-zone Top Bar Contract with single-element Brand Zone
<header className="flex items-center justify-between px-6 py-4 border-b border-slate-200">
  {/* Zone 1: Single text element wordmark */}
  <a href="/" className="text-lg font-bold tracking-tight text-slate-900">
    Apex Industrial
  </a>

  {/* Zone 2: 4-6 clean text navigation links */}
  <nav className="hidden md:flex items-center gap-6 text-sm font-medium text-slate-600">
    <a href="#capabilities" className="hover:text-slate-900 transition-colors">Capabilities</a>
    <a href="#facility" className="hover:text-slate-900 transition-colors">Facility</a>
    <a href="#case-studies" className="hover:text-slate-900 transition-colors">Case Studies</a>
    <a href="#certifications" className="hover:text-slate-900 transition-colors">Certifications</a>
  </nav>

  {/* Zone 3: 1-2 primary actions */}
  <div className="flex items-center gap-3">
    <button className="px-4 py-2 text-xs font-medium text-white bg-slate-900 rounded-lg hover:bg-slate-800 transition-colors whitespace-nowrap">
      Request Quote
    </button>
  </div>
</header>
```

--------------------------------------------------------------------------------

## 3. High-Fidelity Image Asset Generation & `generate_image` Integration

Visual assets make or break an application. Follow these mandatory rules for all
imagery:

### A. Ban on Fragile External URLs

-   **NEVER** use unverified external image hosts (`images.unsplash.com`,
    `picsum.photos`, `placeholder.com`, `via.placeholder.com`). These domains
    fail or get blocked in hermetic evaluation sandboxes, leading to broken
    images and critical evaluation failures.
-   **Always invoke the `generate_image` tool** to create high-fidelity,
    context-appropriate images.

### B. `generate_image` Tool Protocol

When generating images, provide:

1.  `Prompt`: Rich, domain-authentic description specifying subject,
    environment, lighting, texture, camera angle, and mood.
2.  `ImageName`: Descriptive lowercase name with underscores (e.g.,
    `hero_marine_propeller`, `fashion_streetwear_denim`, `card_deck_showcase`).
3.  `AspectRatio`: Standard aspect ratio matching container geometry:
    -   `16:9` → Hero banners, landscape backdrops, cinematic headers.
    -   `4:3` → Product cards, article cards, thumbnail grids.
    -   `1:1` → User avatars, square product showcases, game icons, insignias.
    -   `3:4` → Book covers, posters, vertical editorial portraits.
    -   `9:16` → Full-screen mobile wallpapers, vertical video/story cards.

### C. Parallel Batch Generation Workflow (Mandatory)

When an interface requires visual assets (e.g. hero banner, Bento grid cards,
showcase cards, avatars, feature thumbnails):

-   **Inventory All Visual Slots Upfront**: Before calling `generate_image`,
    audit your entire planned layout (Hero, every Bento grid card, feature
    spotlights, avatars) and list **all** required visual assets. If multiple
    images are needed, plan them all at once.
-   **Single Parallel Batch Turn**: Emit **all** `generate_image` tool calls
    together in parallel within a **single turn** (aim for ~3–5 images).
    **NEVER** split image generation across multiple turns (e.g., do not
    generate 2 images first and then realize a Bento card needs a 3rd image in
    the next turn).
-   **Two-Phase Flow for Timestamped Paths**: Generated image filenames include
    completion timestamps (`<name>_<timestamp>.png`). Follow this two-phase
    protocol whenever using `generate_image` (even for a single image):
    1.  *Phase 1 (Single Batch Generation Turn)*: Issue all `generate_image`
        calls simultaneously in one turn. Do not create or edit component files
        yet.
    2.  *Phase 2 (Implementation Turn)*: In the following turn, take the exact
        returned file paths from the tool responses (e.g.
        `hero_banner_1742081234567.png`) and write/update all components
        referencing those paths. If any image generation call fails or returns
        an error, apply the Zero-Broken-Image Policy (Section E) using a styled
        CSS/SVG fallback container rather than guessing paths or retrying in
        this turn.

### D. Domain-Specific Prompt Recipes

-   **E-Commerce & Retail**: "Studio product photography of [product
    description] on a clean neutral travertine surface, soft diffused side
    lighting, shallow depth of field, 8k commercial quality, minimalist luxury
    aesthetic."
-   **Landing & Marketing**: "Cinematic wide-angle view of [subject/industry
    context], golden hour natural illumination, modern architectural lines,
    atmospheric depth, editorial grade."
-   **Creative & Editorial**: "High-contrast documentary editorial photo of
    [scene], dramatic natural window shadows, rich organic textures, muted color
    grading, Leica 35mm aesthetic."
-   **Technical & Scientific**: "Clean scientific isometric rendering of
    [system/molecule/device], sleek metallic surfaces, precise technical
    cross-sections, subtle studio rim lighting."
-   **Games & 2D Play**: "Thematic hand-crafted game asset of
    [character/card/item], sharp clean outlines, vibrant game color palette,
    top-down or isometric perspective."

### E. Zero-Broken-Image Policy (Mandatory Fallback)

Every image slot in your markup must be resilient:

-   Always specify `referrerPolicy="no-referrer"` and descriptive `alt` text on
    `<img>` tags.
-   Provide a styled CSS fallback container (e.g. subtle gradient mesh with
    domain SVG icon and item title) so that if an image asset fails to load, the
    interface remains visually complete and polished. Never show an empty broken
    image frame.

### F. Banned Visual Clichés

-   ❌ No broken image frames or unstyled `<img>` tags.
-   ❌ No unsolicited hyper-saturated cyan/magenta neon or cyberpunk glow.
-   ❌ No glossy 3D pastel floating balloons, spheres, or jelly characters.
-   ❌ No airbrushed plastic wax figures or decorative lens flare glitter.

--------------------------------------------------------------------------------

## 4. Mandatory Domain Reference Routing

**CRITICAL REQUIREMENT**: You MUST identify the target domain of the user
request and read the corresponding domain reference file using `view_file`
BEFORE writing or modifying any frontend code. Do NOT rely on generic
assumptions—each reference document contains mandatory, non-negotiable layout
conventions, typographic pairings, color palettes, and interaction
specifications for its domain.

| Category Set  | Sub-Genres &        | Mandatory Reference File                                                                           |
| :------------ | :------------------ | :------------------------------------------------------------------------------------------------- |
| **E-Commerce & Retail** | Furniture, lighting, food/drink, beauty, fragrance, watches, jewellery, publishing, audio hardware, automotive retail | [`references/1_ecommerce_retail.md`](references/1_ecommerce_retail.md) |
| **Landing & Marketing** | Corporate agencies, product launches, lead generation, automotive/mobility marketing, digital marketing | [`references/2_landing_marketing.md`](references/2_landing_marketing.md) |
| **SaaS & Dashboards** | Enterprise dashboards, analytics, developer consoles, spreadsheets, batch normalization tools, task planners | [`references/3_saas_dashboard.md`](references/3_saas_dashboard.md) |
| **2D Games & Casual** | Card games (trick-taking, shedding, deck builders), board games (chess bots), word puzzles (word search for seniors), 2D trench defense | [`references/4_games_2d_casual.md`](references/4_games_2d_casual.md) |
| **3D Graphics & Spatial** | Three.js / WebGL scenes, 3D car racing, 1st-person 3D games (3D Snake), 3D product viewports, geometry models | [`references/5_threejs_3d_spatial.md`](references/5_threejs_3d_spatial.md) |
| **Education & Simulations** | EdTech, interactive simulations (Bohr effect, xylem/phloem, ratios, sacred geometry), grading rubrics | [`references/6_education_simulations.md`](references/6_education_simulations.md) |
| **Portfolio & Photography** | Editorial portfolios, showreels, photography galleries, writer tools, student achievement batch sites | [`references/7_portfolio_photography.md`](references/7_portfolio_photography.md) |
| **Science, Space & Biotech** | Lab instruments, telemetry, battery cycle spider charts, biotech process monitors, astronomy | [`references/8_science_space_biotech.md`](references/8_science_space_biotech.md) |
| **Museum & Editorial** | Commercial art dealers, museum exhibitions, non-profit annual reports, shareholder letters, broadsheets | [`references/9_museum_editorial_institutional.md`](references/9_museum_editorial_institutional.md) |
| **Mobile & Touch Apps** | Mobile-first PWAs, thumb navigation, sports stat trackers (shooting guard tracker), pet planners, habit tools | [`references/10_mobile_touch_apps.md`](references/10_mobile_touch_apps.md) |

--------------------------------------------------------------------------------

## 5. Pre-Flight Verification Checklist

Before completing your code, verify silently against this checklist:

1.  **Domain Reference Verified**: You have read the mandatory domain reference
    file in `references/` via `view_file` and applied its specific visual rules.
2.  **Working Handlers**: Every button, dropdown, tab, and card click has an
    active event handler (no dead clicks).
3.  **Top Bar Contract**: Exactly 3 zones (Brand title, 4–6 nav links, 1–2
    actions). Brand is a single text element.
4.  **Single-Line Controls**: All buttons, tags, and tabs are single-line with
    `whitespace-nowrap` and truncation safety.
5.  **Anti-Slop Cleanliness**: No `//` comment headers, no fake version tags
    ("SYNTHEX v4.8"), no bottom telemetry tickers, no hallucinated scorecards
    ("92/100 INNOVATION SCORE"), no low-opacity watermark text.
6.  **Zero-Pill Metadata**: Metadata uses unboxed text with `·` or `/`
    separators; no pill badge sandwiches on cards.
7.  **60-30-10 Color Discipline**: 60% neutral canvas, 30% structural surfaces,
    10% accent budget. No state signaled by color alone.
8.  **No Headline Orphans**: Display headlines use `text-wrap: balance` or
    max-width constraints to avoid isolated single-word trailing lines.
9.  **Motion & Interaction Budgets**: Routine feedback settles in $\le
    200\text{ms}$; only compositor properties (`transform`, `opacity`) are
    animated; zero-latency access to all primary content.
10. **15% Mobile Sticky Cap**: Aggregate height of fixed/sticky elements on
    mobile is $\le 15\%$ of viewport height.
11. **Claim-to-Proof Adjacency**: Proof metrics and testimonials are placed
    adjacent ($\le 1$ section) to the specific claim they support.
12. **Images Verified**: Visual assets generated via `generate_image` with
    proper aspect ratio and prompt formula; fallback containers in place; zero
    broken images.
13. **Spatial Math & Viewport**: Full 1440px desktop presence; single-level card
    elevation; container padding $\ge$ inner child gap.
14. **Tabular Numerals & States**: All numbers in tables, metrics, and lists use
    tabular figures (`tabular-nums`); loading, empty, and error states exist
    where data loads.
