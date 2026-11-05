---
name: mito-industry-page-template
description: Template, rules, and lessons learned for building Mito's tool-focused "by industry" landing pages (mito.ai/industries/[industry]) — the 7-section structure, what belongs in each section, the site's visual design tokens, and copywriting rules distilled from building the Fashion version end-to-end. Use whenever building or reviewing an industry landing page (Beauty, Sports, Automotive, Travel, Corporate, E-commerce, Music, etc.), or when asked to replicate/adapt the Fashion template for another industry.
---

# Mito industry landing page template

Built and iterated live with the page owner on the Fashion version, starting from a structure-draft artifact styled to match mito.ai. Read this skill before building a new industry version — most of the hard calls below came from real back-and-forth, not first guesses, so don't re-derive them from scratch.

## Where this fits in the bigger picture

A product marketing site can be organized on **two axes**:
- **By industry** — Fashion/Beauty/Luxury, E-commerce, Media/Entertainment/Broadcast, Sports, Tech/SaaS, Music, Agencies, Filmmakers, Corporate comms.
- **By application** — the job-to-be-done axis, cutting across industries.

This skill covers the **industry** page template specifically — one page per industry, following the same 7-section skeleton, with content swapped per vertical.

**Framing shift that changed everything:** these pages are **tool-focused** (what a customer can achieve *with mito.ai directly* — its models, features, canvas), not **studio-focused** (MITO Films producing *for* a client). Existing sales material is often framed around the services side rather than the product. Mine it for reusable *content* (examples, already-approved copy), but restructure the framing entirely around the tool.

## The 7 sections, in order

### 01 — Hero
Industry-language eyebrow + headline + subhead + dual CTA (primary: self-serve "start creating"; secondary: "talk to sales"). **Visual = an existing real Mito project** (looped/cropped video or still), not new production — this is a recurring theme: reuse what's already been shot/produced rather than commissioning new hero content. Never fabricate a hero visual; placeholder it clearly (`[ hero visual — loop a real project, e.g. X ]`) until a real asset is chosen.

**Subhead rule (added after reviewing Artlist's sports page, which frames its subhead as create-what + with-what + to-what-end):** the subhead should read as **"Create [what output] with [Mito's two real levers] to [2-3 concrete outcomes]."** Not a mood statement — a sentence that names the deliverable, the mechanism, and the payoff in one line. The two levers are always **the AI platform and creative direction/craft** (use the company's own approved framing for these, not a new pair invented per page) — don't invent a different pair of levers per industry. The 2-3 outcomes should be industry-specific and concrete (Sports: "launch players, celebrate legends, and keep fans watching all season" — not generic filler like "keep evolving"). Example (Sports): *"Create sports content with MITO's AI platform and creative direction, to launch players, celebrate legends, and keep fans watching all season."* Fashion's original subhead ("From one product, model, or campaign idea, any brand touchpoint can keep evolving — without a reshoot") predates this rule and doesn't follow it — worth revisiting if Fashion's hero gets touched again, but not retrofitted automatically just because this rule exists.

### 02 — Why Mito (capabilities — the "why")
A **navigable list** (Lovart's "One brief in, a whole campaign out" pattern: click a point on the left, one visual updates on the right — build this with real click behavior, not a static mock, using plain JS). **Exactly 4 items, no more** — this axis drifts fast if not capped.

**The hard rule, learned the hard way through two rounds of de-duplication:** 02 holds only **universal, industry-agnostic capability themes** — a principle like "multiplication," "adaptation," "unbounded creativity," "post-production flexibility," just worded for the industry. It does **not** name:
- A specific finished deliverable a client would ask for by name (that's section 03's job — "Market & segment adaptation" as a deliverable duplicated "One campaign, all audiences" as a capability until one was cut).
- A specific Mito product/tool name (Character Builder, Director, Canvas) — naming tools here is redundant with section 04 and breaks the pure-value register Flora uses. Caught once: "Character Builder holds a model... steady" got rewritten to describe the *value* (fidelity enabling dynamic format transformation) with no tool name.

**Titling rule:** don't invent generic descriptive titles ("A few shots, a full campaign") — they read as placeholder-y and tend to repeat words across the list (a real failure mode: three titles all containing "shoot" reads monotonous). Instead:
1. Check whether Mito already has **approved slide copy** covering the same idea (an existing slide that already names the same capability themes with punchy titles) — reuse those titles verbatim if the idea matches. Lower risk, proven, on-voice.
2. If nothing exists, write short declarative fragments matching the brand's actual voice as it appears in approved material. Short. Confident. Present tense. Not a feature description.

Copy should **lead with the customer's actual pain**, not the capability in isolation — e.g. "Reimagine shoots" opens with "A traditional shoot is rigid — a different season, background, or crop usually means new post-production hours or a full reshoot," *then* Mito as the fix. Problem before solution, every time.

### 03 — What you can do (deliverables — the "what")
A **horizontal scroll carousel** (Lovart's "More design tools" pattern: photo + short title + one line, arrows to scroll). Not capped at a fixed count — this list is meant to feel abundant (Luma's `/use-case` hub proves the "many specific things" approach works for showing breadth) but every single card must pass one test:

> **Can you point to a specific thing that gets made, or is it a genre/style/audience descriptor wearing a deliverable's clothes?**

Real failures caught and fixed against this test:
- "E-commerce content" (a bucket) → split into **360° product views**, **On-model photography, every angle**, **Lighting, tone & mood adjustment**, **Packaging & label mockups** (four specific outputs, matching the granularity Luma/Flora actually use — see their real cards: "Product visuals in all angles," "Explore packaging & label mockups").
- "Social native content" (a style descriptor) → **"Vertical video for social feeds"** (the actual concrete output, with a real past project as precedent).
- "Commercials" (a genre label) → **"Hero film + every cutdown"** (the two things actually delivered: master + cutdown versions).
- "Visual worlds & brand identity" (one abstract card trying to do two jobs) → split into **"Visual mood boards"** (lightweight, early-stage output) and **"A full brand world"** (full-scope output).
- "Market & segment adaptation" — removed entirely from 03 once it was confirmed as a straight duplicate of 02's "One campaign, all audiences."

Each card gets a still/thumbnail from a **real existing Mito project**, never a new shoot — same reuse principle as the hero.

### 04 — Features (labels only, grouped)
**This is not a deep tour.** Two failed attempts before landing here: first a flat pill row (Artlist's Music/SFX/Footage pattern) plus a detailed 8-card grid with descriptions (Runway's "Apps for everything" pattern) — too heavy. Second attempt used a 4-column pill grid, but the CSS had a real scoping bug (`.pill-row .pill-outline` doesn't match markup using `.pill-row-inline` — always make `.pill-outline`/similar base classes **standalone**, not scoped to a specific parent, if they'll be reused in different containers) and rendered as unstyled flat text.

**Final pattern: horizontal divider rows** (same visual rhythm as the rest of the page — label left, pills flowing right, `border-top` dividers), **grouped into clusters, labels only, no descriptions.** The grouping itself does clarity work — "Director" alone means nothing even to someone in the industry, but "AI Director" sitting under a "Creative AI" heading next to "Character Builder" reads clearly without a description. Same fix for "My Assets" → "Asset library" (a clearer noun).

Groups used for Fashion (adjust content per industry, keep the grouping logic):
- **Workspace** — Canvas, Storyboard, Timeline
- **Creative AI** — AI Director, Character Builder
- **Control** — Camera & motion, Speed & pacing, Reference-guided generation
- **Library & models** — Asset library, Every model, one place

Source the actual feature list from the **company knowledge-base skill** — it has the confirmed, live-product feature set (Canvas, Storyboard, Director, Timeline, My Assets/Generations, the model roster, named example workflows). Don't invent features to match a competitor's granularity — Runway's specific "Apps" (Remove from Video, Relight Scene, etc.) are inspiration for *style*, not a list to copy; only include what Mito actually confirmed. If a feature goes in on request but is not confirmed in the source material, flag it rather than presenting it as equally certain.

### 05 — Made with Mito (proof strip, optional)
Light strip of real project stills, no captions beyond the client/project name. **No testimonials or quotes** — explicit decision, revisit later if that changes. Mirrors mito.ai's own real "Made with Seedance 2.5" strip pattern (seen live on `mito.ai/seedance-2-5/`).

### 06 — Built for enterprise (goes last, right before the closing CTA)
**Exactly 4 blocks** — a 5th ("Multiplayer by design") got merged into "Workflows for all productions" once it was clear multiplayer collaboration is the *vehicle* for the unified workflow, not a separate idea. When a block's copy covers two ideas (collaboration + end-to-end workflow), **open with whatever the block's own title promises first** — a real fix: leading with "Real-time collaboration" under the title "Workflows for all productions" read as a mismatch, since the title never set up collaboration; reordered so "End-to-end in one workflow" opens (matching the title), then collaboration follows as the second beat. Keep both ideas as clearly separate sentences/beats, don't blend them into one clause where one idea reads subordinate to the other.

The 4 blocks (titles are stable, content is Fashion-flavored but the *shape* transfers):
1. **Workflows for all productions** — end-to-end + real-time collaboration (see above).
2. **The latest AI, always** — new models added within days of release (only state a turnaround the company has documented).
3. **Scalable & boundless** — uses **Director's canonical description verbatim** (from the company knowledge base): *"workspace aware, with project memory, knowledge bases, references and context, collaborating with you under shared intelligence."* Don't paraphrase this — reuse the exact phrasing every time Director is described anywhere.
4. **Safe & secure** — tag chips, not prose. **Verify every claim against the company's own compliance documentation** before shipping any security claim:
   - State only what the compliance documentation confirms for the company itself (never generalize from what is typical for the industry).
   - **Don't name the underlying infrastructure vendor** — generalize (e.g. "Regional data residency options"). Infrastructure-vendor detail doesn't belong on a customer-facing page.
   - **Don't borrow a sub-processor's certification.** If a vendor holds a certification for its own service, that is not the company's certification.
   - If a claim (e.g. SSO) isn't mentioned in the docs at all, mark it `[TBD — not found in doc]` and get a direct answer rather than inferring either way.
   - Logo wall: **never fabricate one** — placeholder it until there are confirmed, approved public logos.

### 07 — Closing CTA
Standard: self-serve primary CTA + demo/enterprise secondary CTA. Mirrors mito.ai's own real closing pattern ("Start exploring on the canvas").

## Visual system — matches the real mito.ai site

Pulled by inspecting `mito.ai/seedance-2-5/` directly (computed styles), not guessed:
- **Font:** `"Monument Grotesk"` first in the stack (licensed, won't load in an artifact — fall back to `-apple-system, "Helvetica Neue", Arial, sans-serif`, which is visually close).
- **Background:** near-white, `oklch(0.98 0 0)`. **Text:** near-black, `oklch(0.205 0 0)`.
- **Accent (the coral dot after headlines, e.g. "MITO.")**: `oklch(0.58 0.22 22.216)` — this is a real, confirmed brand signature, use it as the period after every major `h2`/`h1` (`<span class="accent-dot">.</span>`).
- **Announcement-bar lime:** `oklch(0.93 0.21 122)` — bright chartreuse-lime, used for top promo bars, not much else.
- **Buttons:** solid black pill (`background: var(--text)`) for primary, outlined pill for secondary. `border-radius: 8px` on buttons specifically (not fully rounded).
- **Cards:** light gray placeholder blocks (`oklch(0.94 0 0)`) for imagery, white card body, minimal border, no heavy shadows.
- Full working CSS (light + dark mode via `oklch()`, which modern browsers support natively) is in the reference artifact — copy the `<style>` block wholesale for a new industry rather than rebuilding tokens from scratch.

## Competitor patterns actually used as inspiration (and where)

- **Lovart** — the navigable-list value-prop pattern (section 02); the minimal image+one-line-caption gallery style (informed section 03's brevity); the light feature-card row (informed, then was simplified further for, section 04).
- **Flora** — pure value-language register for section 02 (no tool names); "one system for your entire creative operation" framing.
- **Luma** — the "many specific things" breadth approach for section 03 (their `/use-case` hub has 71+ granular cards); the enterprise 2x2 block layout (informed section 06's shape before it went back to 4 blocks); real client-logo wall pattern (section 06 placeholders the logo wall until approved logos exist).
- **Runway** — 3-value-prop-under-a-headline pattern (validates section 02's shape); "Apps for everything" granularity as a *style* reference for section 04 (not a content source — those specific apps are Runway's, not Mito's).
- **Artlist** — pill-row-of-categories pattern (Music/SFX/Footage/...) — informed section 04's first (later replaced) attempt; logo wall directly in the hero.

## Content sourcing checklist (in priority order)

1. **Company knowledge-base skill** — company facts, confirmed platform features, Director's canonical description, and which client projects are public, fictional or internal.
2. **The project database** — the master, most-current list of real productions. Check each project's visibility (Public/Private/Unlisted) before reusing it as public-facing proof; Private means don't surface it externally.
3. **Existing by-industry sales decks** — a good source of already-written, approved slide copy Mine them for reusable titles/copy, but remember they may be services-framed, not tool-framed.
4. **Compliance documentation** (read-only) — the only source of truth for section 06's security claims. Don't infer compliance status from anywhere else.
5. **The site-structure doc** — check whether an industry/application combination is already scoped elsewhere.

## Process notes

- This whole template was built as a **structure draft artifact** (placeholder visuals in brackets, annotation notes above every section explaining the rule and citing what changed) — keep building new industries the same way before writing final copy. The annotation notes aren't disposable scaffolding; they're what makes the rules replicable without re-litigating them each time.
- When the owner is live-editing the doc or Figma file this content is pulled from, **re-fetch current state before editing** — content shifts between turns.
- Never fabricate a capability, certification, or client logo to fill a gap — placeholder it and flag it explicitly instead. Every `[TBD]` in the reference artifact exists because something was checked and came back unconfirmed, not because it was skipped.

## Implementation learnings — building the Fashion page in the real codebase (`mito-site`)

Everything above is about drafting the structure/content. These are the lessons from actually shipping it as code (`src/config/industries.ts`, `src/components/patterns/HorizontalCarousel.tsx`, `EnterpriseBlockGrid.tsx`, `ProofStrip.tsx`, `NavigableFeatureList.tsx`) across a long iterative session, PR'd as `feat/fashion-hero1-video`.

### Media assets almost always need cropping AND compressing — check both, in that order
Raw phone/AI-gen exports routinely arrive (`industry-fashion-*.png/.jpg/.mov`, sometimes 5000px+ wide or 20MB+). Before converting format, **always run `ffmpeg -vf cropdetect=24:2:0 -frames:v 60 -f null -` on video and eyeball a frame from image assets** — several assets had pillarbox/letterbox bars baked into the pixels (a "vertical" video was actually 3840×2160 with the real content only ~2160×2138 centered; a "lighting" video had black bars top/bottom hiding a square 720×720 inside a 720×900 frame). `object-cover` in CSS can't fix baked-in bars — it just crops the visible frame, bars and all. Crop first with the detected values, *then* scale/compress.
- Compression recipe that worked repeatedly: `ffmpeg -vf "scale=720:-2" -c:v libx264 -crf 28 -preset slow -an -movflags +faststart` — strips audio (decorative autoplay/loop/muted videos never need it), consistently landed clips at 60KB–600KB regardless of a 3–20MB source.
- Images: `sharp-cli -i <src> -o <dir> -f webp -q 80 resize <width>` (not `--width`, the flag doesn't exist on this CLI — width is a positional arg to the `resize` subcommand). Target ~2x the card's display width, not the source's native resolution.
- The raw/unconverted source files are worth leaving in place uncommitted (don't `git add` them) — they get referenced again in later turns (e.g. asking for a crop fix days after the first conversion), and having the original around avoids a second generation-loss re-encode. Only the converted, correctly-sized file goes in the commit.
- Filenames assets are saved under don't always match a config field 1:1 — e.g. the request said "the packaging one" and "the lighting one" meaning specific existing `HorizontalCarouselItem`s; always grep the config for the current `media` path before assuming which file replaces which.

### `HorizontalCarousel` (section 03) — settled shape after several rounds
- Card: `w-[280px]`, `aspect-[5/6]`. Went to `w-[340px]`/`aspect-[4/5]` once ("make the boxes bigger so the blur covers less") and back again later ("bring the boxes back to the size these had before") — the smaller size read better once the text/blur panel itself got fixed (below), so don't assume bigger is the fix for a blur-proportion complaint; shrinking the panel is the other lever.
- Text overlay pattern (replaced the old below-image title+description layout): image fills the whole card; a `flex flex-col justify-end` panel of **fixed height** (`h-28`) sits `absolute bottom-0`, with a `bg-gradient-to-t from-background/85 via-background/60 to-transparent` + `backdrop-blur-md`. Title `line-clamp-1`, description `line-clamp-2` with an explicit `min-h-10` — **both clamps are required**, not just line-clamp, or a short caption leaves the panel shorter than a long one and titles stop lining up across cards. This was a specific, named ask ("title and subtitle must always be at the same height") — solve it with fixed container height + line-clamp + min-height together, not any one alone.
- Added a `mediaPosition?: "center" | "top"` field (maps to `object-top`/`object-center`) for when the aspect ratio mismatch between source video and card crops into a subject's head — cheaper and more correct than re-shooting/re-cropping the source video itself.
- Keep the list's media types **alternating image/video** — two autoplaying videos back-to-back reads worse than the same content spaced out. When reordering per a content request, check the resulting sequence for accidental back-to-back videos even if the user's ask didn't mention it explicitly (they will notice, and it's a one-line fix to interleave while already touching the array).

### `EnterpriseBlockGrid` (section 06) — photos are optional, and "no photo" is a valid final state
The component originally always rendered an image box (`h-28`), falling back to a "No screenshot yet" placeholder when `media` was absent. After actually sourcing 4 photos for it, the call ended up being **no photos at all** — text + tags only, with the visual interest carried by an interactive hover state instead: `shadow-sm` at rest, `hover:-translate-y-1 hover:shadow-2xl hover:border-foreground/40` on hover (a lift + deepening shadow + border highlight, nothing else — resist the urge to add more once "something cool, but nothing more than that" has been said explicitly). When `media` is omitted, skip the image container **entirely** rather than rendering the "No screenshot yet" placeholder — a permanently-empty placeholder box reads as unfinished, whereas no box + a good hover state reads as an intentional design choice.

### `ProofStrip` (section 05) — optional "Play" link to source video
Added an optional `videoUrl` per item: a small frosted pill, `absolute right-2 top-2`, `border-white/30 bg-white/20 backdrop-blur-md text-white`, with a filled `PlayIcon`, linking out (`target="_blank" rel="noopener noreferrer"`) to the project's real video. `bg-white/20`/`border-white/30` are the one sanctioned way to get a translucent glass chip without inventing a new token — the design-system rule against hardcoded colors explicitly exempts white/black-with-opacity for this kind of universal overlay.

### Section numbers in conversation don't always match this doc's canonical numbering
People refer to sections as "section 03", "section 04" etc. in casual conversation, but their mental numbering has drifted from this skill's canonical 1–7 (Hero, Why, Deliverables, Features, Proof, Enterprise, CTA) at least once — confirm which section before making a destructive change (e.g. "remove the photos for section 04" turned out to mean the Enterprise grid, not the canonical section 4/Features, which doesn't even have photos). A quick disambiguating question beats guessing wrong on a content-removal request.

### Small process/tooling notes
- The repo enforces PR-only merges to `main` (see the project's own `CLAUDE.md`) — do all work on a feature branch (`feat/...`), commit incrementally per logical change (easier to narrate back what shipped), and only push + open the PR once the user actually asks for it to go live.
- `pnpm` isn't always on `PATH` in a fresh shell even when the project uses it — `corepack pnpm <cmd>` works without needing a global install/symlink (useful when `corepack enable` itself fails on a permissions error).
- Local git identity may be unconfigured (commits fall back to `<user>@<hostname>`) — worth a heads-up to the user the first time, not a blocker.
- A browser automation tab can get into a state where `<video>` elements never leave `readyState 0` (autoplay silently not progressing) even for previously-confirmed-working files — verify against the actual file (`ffprobe`, and an HTTP HEAD request for status/content-type/size) before assuming a code regression, and don't burn many retries re-poking the same tab once file-level checks come back clean.
