# Cruz Andina — Design System

Cruz Andina is a brand for **astrología terapéutica y autoconocimiento** (therapeutic astrology and self-knowledge). The visual system combines clean editorial layout, high-contrast serif typography, a vivid 4-hue brand palette sampled directly from the logo, and poetic/contemplative imagery — deliberately avoiding new-age clichés (chakras, crystals, tarot decoration, glowing auras, zodiac-as-decoration, stock wellness photography).

## Sources
All source material was provided as uploads (no Figma file, codebase, or slide deck was attached):
- `Cruz Andina astrología terapéutica_LOGO copia.pdf` → `assets/logo/cruz-andina-logo.pdf`
- `Cruz-Andina-astrología-terapéutica-ICONO.png` → `assets/logo/cruz-andina-icono.png`
- `Cruz-Andina-astrología-terapéutica-moodboard.png` → `assets/brand/moodboard.png`
- `Cruz-Andina-astrología-terapéutica-perfil.jpg` (full logo lockup, used as a social profile image) → `assets/logo/cruz-andina-lockup.jpg`

No product screens, live site, or app code were provided, so there is no existing UI to recreate 1:1. The `ui_kits/website/` folder is an original editorial-site recreation built from the brand assets and moodboard art direction, not a copy of an existing product.

## Content fundamentals
- **Language**: Spanish, second person informal ("tú"), warm and direct — never clinical or corporate.
- **Voice**: contemplative, poetic, grounded — astrology as metaphor and "puente" (bridge), not prophecy. From the moodboard: *"La astrología como un puente entre lo invisible y tu experiencia en la Tierra."* / *"Lo invisible toma forma."* / *"Hay un propósito en todo lo que sientes."*
- **Tone**: sophisticated, never solemn; spiritual, never esoteric; short declarative sentences mixed with one longer poetic line per section.
- **Casing**: sentence case throughout, no ALL-CAPS body copy. Eyebrow labels (small category tags above headlines) are the one place for uppercase + wide letter-spacing.
- **Vocabulary**: recurring conceptual words from the brand's own framework — Conciencia, Sanación, Evolución, Integración, Propósito, Sabiduría Ancestral, Amor — plus the 6-step journey: Invisible → Experiencia → Relación → Transformación → Propósito → Integración.
- **Emoji**: never used.
- No exclamation points, no hard-sell CTAs — invite ("Reservar sesión"), don't push.

## Visual foundations
- **Color**: a vivid 4-family, 3-step brand palette (blue / green / red / gold) sampled directly from the 12 zodiac tiles of the chakana logo — see `tokens/colors.css`. Backgrounds are a cool off-white paper, never beige/sepia/earthy. Neutrals (ink/paper) support composition; they never dominate it. One deep-ink "inverse" section per page is enough for contrast — don't over-use dark sections.
- **Type**: serif display (Ivy Ora Display) for headlines and big statements — tall, high-contrast, expressive curves; bold weight for hero headlines, medium for section headings, italic for a secondary emphasis line; sans (Urbanist) for everything functional — nav, body copy, labels, buttons. Never mix them the other way (no sans headlines, no serif body paragraphs).
- **Spacing**: generous negative space; a 4px-based scale (`--space-1`…`--space-10`) but editorial sections lean on the larger end (48–96px section padding) — density is not the goal.
- **Imagery**: real photography, color intervention on a real scene, contemplative gouache/ink illustration, or an immersive physical phenomenon — see `guidelines/art-direction-*.html` for the 4 families, rules and correct/incorrect examples. Color must live inside a real material, light or surface — never as a flat decorative gradient. No stock wellness photography, no literal zodiac-symbol decoration, no glowing/mystical effects, no CGI.
- **Backgrounds**: flat paper or ink only. Decorative UI gradients are not part of the system — any gradient-like effect must come from a real photographed phenomenon (light, water, refraction), never from CSS as decoration.
- **Corners & shadows**: flat-first. Small/straight radii (2–6px), pill only on buttons/tags. Shadows are almost unused — a 1px hairline border separates surfaces; `--shadow-lift` is reserved for functional overlays (menus/modals), never decoration. See `guidelines/radii-shadow.html`.
- **Motion**: fast, quiet transitions only (140–220ms, standard ease) on color/background for hover — no bounce, no scale-pop, no slide-ins.
- **Hover/press**: hover darkens or moves one step deeper in the same hue family (e.g. `blue-500` → `blue-900`); no lightening, no opacity-fade hovers. No visible "press" treatment beyond the browser default (this is an editorial/marketing system, not a dense app).
- **Borders**: single 1px hairlines in `--border-subtle` for structural dividers (header, footer) only — never as a decorative left-accent bar on cards.
- **Transparency/blur**: essentially unused; the one photographic treatment is `mix-blend-mode: luminosity` at low opacity behind color gradients (see Hero), not a blur/glass effect.
- **Color vibe of imagery**: cool-leaning and saturated where color appears; b&w/monochrome photography is welcome for the "poetic photography" register, but avoid warm sepia/grain nostalgia filters.

## Iconography
- The **only** brand mark is the chakana (Andean cross) built from 12 tiles — one per zodiac sign — each tile a solid color from the 4 brand hue families, with the sign's glyph in white. Source files: `assets/logo/cruz-andina-icono.png` (icon alone) and `assets/logo/cruz-andina-lockup.jpg` (icon + wordmark, used as social profile image). A vector original also exists at `assets/logo/cruz-andina-logo.pdf`.
- **Never** redraw, recolor, simplify, or reconstruct the mark — always use the source files above.
- No general-purpose icon system (no icon font, no UI iconography) was supplied. The moodboard shows a small set of custom line-icon glyphs (circles/rings representing Conciencia, Sanación, Evolución, etc.) but no source files for them exist — treat those as reference-only, not an asset to copy or imitate. If the UI needs a functional icon (e.g. a chevron, a close button), use plain typographic/geometric shapes (an "×", an arrow character) rather than inventing a new icon style.
- Emoji: never used, anywhere.

## Components
Standard editorial primitives, authored from scratch (no source codebase/Figma defined an inventory):
- **Button** — pill CTA, variants `primary`/`accent`/`secondary`/`ghost`.
- **Tag** — small pill label in one of the 4 brand hues, used for topics/signs.
- **Card** — editorial article/offering card (image, eyebrow, serif title, excerpt).
- **SectionHeading** — eyebrow + serif headline pairing used to open sections.

## Second pass — brand system expansion (Aug 2026)
Building on the same palette, chakana mark, fonts and voice, this pass turned the system from a generic editorial UI kit into a fuller Cruz Andina brand system.

**Conserved:** chakana mark and its rules, 4-hue palette, cool neutrals, Ivy Ora Display + Urbanist, generous negative space, editorial direction, contemplative voice.

**Changed:** removed the decorative gradient rectangle standing in for photography (Hero, JournalGrid, `EditorialLanding` template) — replaced with `<image-slot>` placeholders per the new Art Direction rules; flattened radii/shadows system-wide (hairline borders instead of card shadows); reduced the visual weight/framing of the core components section (now explicitly "secondary infrastructure").
**Added sections:** `guidelines/art-direction-*.html` (4 imagery families + Do/Don't), `guidelines/composition-system.html`, `guidelines/social-*.html` (5 social formats), expanded `guidelines/brand-mark.html` (clear space, min size, icon vs. lockup, don't-repeat) and `guidelines/type-scale.html` (full Hero→eyebrow hierarchy).
**Needs human validation:** all `<image-slot>` placeholders are unfilled — real photography/illustration/color-intervention shots need to be sourced or shot per the new Art Direction rules before this reads as a finished brand, not a kit; the social formats are composition principles, not locked templates, and should be sanity-checked against actual Instagram/Reels crops once real imagery exists.

## Index
- `styles.css` — root stylesheet, imports everything below.
- `tokens/` — `colors.css`, `typography.css`, `spacing.css`, `fonts.css` (Google Fonts import), `base.css`.
- `guidelines/` — foundation specimen cards (Colors, Type, Spacing, Brand) shown in the Design System tab.
- `components/core/` — Button, Tag, Card, SectionHeading (`.jsx` + `.d.ts` + `.prompt.md` each) and their showcase card.
- `ui_kits/website/` — editorial homepage recreation (`index.html` + section `.jsx` files).
- `templates/editorial-landing/` — a starting-point template (`EditorialLanding.dc.html`) consuming projects can copy.
- `assets/logo/`, `assets/brand/` — logo files and the source moodboard.
- `SKILL.md` — Claude Code–compatible skill wrapper for this design system.

## Caveats
- No Figma, codebase, or slide deck was attached, and `CA_Imagine amor.pdf` mentioned in the brief was never actually uploaded — only the 4 files listed above exist in `uploads/`. If that file or a codebase/Figma link exists, please attach it and I'll extend this system.
- Fonts: **Ivy Ora Display** (headlines) and **Urbanist** (body/UI) are both self-hosted from the files you provided — see `assets/fonts/` and `@font-face` rules in `tokens/fonts.css`. No externally-loaded fonts remain.-host, share them and I'll swap in local `@font-face` rules.
- The moodboard's 7-swatch "Paleta de color" (Tierra/Claridad/Sol/Naturaleza/Conciencia/Fuerza/Transformación) reads earthier than the 12-color logo palette; per your brief I prioritized the vivid logo-derived hues and kept neutrals cool, not warm/earthy. Flag it if you actually want those 7 named tones represented as tokens too.
- The website UI kit is an original composition (no real site existed to copy) — treat it as one strong direction, not a locked recreation.
