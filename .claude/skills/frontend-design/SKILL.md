---
name: frontend-design
description: Create distinctive, production-grade frontend interfaces with high design quality. Use this skill when the user asks to build web components, pages, or applications. Generates creative, polished code that avoids generic AI aesthetics.
---

This skill guides creation of distinctive, production-grade frontend interfaces that avoid generic "AI slop" aesthetics. Implement real working code with exceptional attention to aesthetic details and creative choices.

The user provides frontend requirements: a component, page, application, or interface to build. They may include context about the purpose, audience, or technical constraints.

## Design Thinking

Before coding, understand the context and commit to a BOLD aesthetic direction:
- **Purpose**: What problem does this interface solve? Who uses it?
- **Tone**: Pick an extreme: brutally minimal, maximalist chaos, retro-futuristic, organic/natural, luxury/refined, playful/toy-like, editorial/magazine, brutalist/raw, art deco/geometric, soft/pastel, industrial/utilitarian, etc. There are so many flavors to choose from. Use these for inspiration but design one that is true to the aesthetic direction.
- **Constraints**: Technical requirements (framework, performance, accessibility).
- **Differentiation**: What makes this UNFORGETTABLE? What's the one thing someone will remember?

**CRITICAL**: Choose a clear conceptual direction and execute it with precision. Bold maximalism and refined minimalism both work - the key is intentionality, not intensity.

Then implement working code (HTML/CSS/JS, React, Vue, etc.) that is:
- Production-grade and functional
- Visually striking and memorable
- Cohesive with a clear aesthetic point-of-view
- Meticulously refined in every detail.

## Frontend Aesthetics Guidelines

Focus on:
- **Typography**: Choose fonts that are beautiful, unique, and interesting. Avoid generic fonts like Arial and Inter; opt instead for distinctive choices that elevate the frontend's aesthetics; unexpected, characterful font choices. Pair a distinctive display font with a refined body font.
- **Color & Theme**: Commit to a cohesive aesthetic. Use CSS variables for consistency. Dominant colors with sharp accents outperform timid, evenly-distributed palettes.
- **Motion**: Use animations for effects and micro-interactions. Prioritize CSS-only solutions for HTML. Use Motion library for React when available. Focus on high-impact moments: one well-orchestrated page load with staggered reveals (animation-delay) creates more delight than scattered micro-interactions. Use scroll-triggering and hover states that surprise.
- **Spatial Composition**: Unexpected layouts. Asymmetry. Overlap. Diagonal flow. Grid-breaking elements. Generous negative space OR controlled density.
- **Backgrounds & Visual Details**: Create atmosphere and depth rather than defaulting to solid colors. Add contextual effects and textures that match the overall aesthetic. Apply creative forms like gradient meshes, noise textures, geometric patterns, layered transparencies, dramatic shadows, decorative borders, custom cursors, and grain overlays.

NEVER use generic AI-generated aesthetics like overused font families (Inter, Roboto, Arial, system fonts), cliched color schemes (particularly purple gradients on white backgrounds), predictable layouts and component patterns, and cookie-cutter design that lacks context-specific character.

Interpret creatively and make unexpected choices that feel genuinely designed for the context. No design should be the same. Vary between light and dark themes, different fonts, different aesthetics. NEVER converge on common choices (Space Grotesk, for example) across generations.

**IMPORTANT**: Match implementation complexity to the aesthetic vision. Maximalist designs need elaborate code with extensive animations and effects. Minimalist or refined designs need restraint, precision, and careful attention to spacing, typography, and subtle details. Elegance comes from executing the vision well.

## Project Design System (if any)

[CUSTOMIZE] If your project has an existing design system, document it here so
this skill respects it. Replace this whole section with your project's tokens
and conventions, or delete it for greenfield work. Examples of what to capture:

- Design tokens / CSS custom properties (color, spacing, typography scales)
- Required theme(s) and how to switch (e.g. light + dark)
- i18n requirement (e.g. all user-facing strings via a translation function)
- Component library to extend (e.g. shadcn/ui, Material UI, Chakra)
- Allowed font sources / curated font list
- Accessibility baseline (WCAG level, prefers-reduced-motion handling)

If none of the above is established yet, leave this section empty and design
from a clean slate.

### Documenting a new design system as `docs/DESIGN.md`

When a project needs its design system written down (extracted from an image,
from existing HTML/CSS, or defined from scratch), save it as `docs/DESIGN.md`
using YAML front matter for the objective values, followed by Markdown
sections explaining how to apply them:

```yaml
---
name: <system name>
colors:
  primary: '#...'
  surface: '#...'
  # ... full palette, semantic names not just "blue-500"
typography:
  headline-lg: { fontFamily: ..., fontSize: 24px, fontWeight: '700', lineHeight: 32px }
  body-md: { fontFamily: ..., fontSize: 14px, fontWeight: '400', lineHeight: 20px }
rounded:
  sm: 0.125rem
  DEFAULT: 0.25rem
spacing:
  base: 4px
  sm: 8px
  md: 16px
---
```

Follow with prose sections: Brand & Style, Colors (usage rules per color, not
just hex), Typography, Layout & Spacing, Elevation & Depth, Shapes, Components
(states: error, success, alert, loading, empty). Objective values in front
matter, rationale and application rules in prose — this keeps the doc usable
both as a lookup table and as guidance for building new screens consistently.

Remember: Claude is capable of extraordinary creative work. Don't hold back, show what can truly be created when thinking outside the box and committing fully to a distinctive vision.
