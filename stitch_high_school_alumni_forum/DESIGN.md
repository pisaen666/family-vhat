---
name: Scholar’s Scrapbook
colors:
  surface: '#fff9ed'
  surface-dim: '#e2dabf'
  surface-bright: '#fff9ed'
  surface-container-lowest: '#ffffff'
  surface-container-low: '#fcf3d8'
  surface-container: '#f7eed2'
  surface-container-high: '#f1e8cd'
  surface-container-highest: '#ebe2c8'
  on-surface: '#1f1c0b'
  on-surface-variant: '#424845'
  inverse-surface: '#35301e'
  inverse-on-surface: '#faf0d5'
  outline: '#727975'
  outline-variant: '#c2c8c3'
  surface-tint: '#4c6359'
  primary: '#152c24'
  on-primary: '#ffffff'
  primary-container: '#2b4239'
  on-primary-container: '#95aea2'
  inverse-primary: '#b2ccc0'
  secondary: '#ac3231'
  on-secondary: '#ffffff'
  secondary-container: '#fd6d67'
  on-secondary-container: '#6d000c'
  tertiary: '#002948'
  on-tertiary: '#ffffff'
  tertiary-container: '#00406a'
  on-tertiary-container: '#6caded'
  error: '#ba1a1a'
  on-error: '#ffffff'
  error-container: '#ffdad6'
  on-error-container: '#93000a'
  primary-fixed: '#cee9dc'
  primary-fixed-dim: '#b2ccc0'
  on-primary-fixed: '#082018'
  on-primary-fixed-variant: '#344c42'
  secondary-fixed: '#ffdad7'
  secondary-fixed-dim: '#ffb3ae'
  on-secondary-fixed: '#410004'
  on-secondary-fixed-variant: '#8b191d'
  tertiary-fixed: '#d0e4ff'
  tertiary-fixed-dim: '#9bcbff'
  on-tertiary-fixed: '#001d34'
  on-tertiary-fixed-variant: '#004a79'
  background: '#fff9ed'
  on-background: '#1f1c0b'
  surface-variant: '#ebe2c8'
typography:
  headline-lg:
    fontFamily: Bricolage Grotesque
    fontSize: 48px
    fontWeight: '800'
    lineHeight: 56px
    letterSpacing: -0.02em
  headline-md:
    fontFamily: Bricolage Grotesque
    fontSize: 32px
    fontWeight: '700'
    lineHeight: 40px
  headline-sm:
    fontFamily: Bricolage Grotesque
    fontSize: 24px
    fontWeight: '600'
    lineHeight: 32px
  body-lg:
    fontFamily: Work Sans
    fontSize: 18px
    fontWeight: '400'
    lineHeight: 28px
  body-md:
    fontFamily: Work Sans
    fontSize: 16px
    fontWeight: '400'
    lineHeight: 24px
  label-md:
    fontFamily: Courier Prime
    fontSize: 14px
    fontWeight: '400'
    lineHeight: 20px
  accent-handwritten:
    fontFamily: Bricolage Grotesque
    fontSize: 20px
    fontWeight: '400'
    lineHeight: 24px
rounded:
  sm: 0.125rem
  DEFAULT: 0.25rem
  md: 0.375rem
  lg: 0.5rem
  xl: 0.75rem
  full: 9999px
spacing:
  unit: 8px
  container-max: 1100px
  gutter: 24px
  margin-mobile: 16px
  margin-desktop: 40px
---

## Brand & Style

This design system is built on **Tactile Skeuomorphism** and a **Scrapbook Aesthetic**, designed to evoke the deep nostalgia of a high school classroom. The UI is not just a digital interface but a physical desktop—layering aged paper, wooden textures, and classroom artifacts like chalkboards and stationery.

The target audience is alumni reconnecting after years apart; therefore, the emotional response must be warm, communal, and personal. The design eschews modern clinical flatness in favor of "organic imperfection"—slight rotations on images, hand-drawn underlines, and textured surfaces that feel lived-in and cherished.

## Colors

The palette is derived directly from classic classroom materials to trigger sensory memory.

- **Primary (Chalkboard Green):** Used for main containers, headers, and navigation bars to provide a grounding, academic weight.
- **Neutral (Aged Paper):** A warm, cream-beige base used for the page background and content cards.
- **Secondary (Red Pen):** Reserved for corrections, highlights, notifications, and "teacher’s notes" accents.
- **Tertiary (Blue Ink):** Used for links and interactive elements, mimicking the look of ballpoint pen notes in a margins.
- **Surface (Desk Oak):** A rich, textured brown used for the outer framing of the layout to simulate a desk surface.

## Typography

The typography system relies on a contrast between structured "textbook" fonts and "handwritten" annotations.

- **Headlines:** Use **Bricolage Grotesque** for a quirky, characterful feel that bridges the gap between formal print and personal expression.
- **Body:** **Work Sans** provides high legibility for long-form forum discussions, ensuring the "notebook" feel remains functional.
- **Labels:** **Courier Prime** is used for metadata (dates, timestamps, categories) to mimic the look of a typewriter or early school records.
- **Accents:** Smaller handwritten-style notes should be placed at slight angles (2-3 degrees) to mimic margin scribbles.

## Layout & Spacing

The layout follows a **Fixed Grid** model that centers a "Notebook" or "Chalkboard" on a desk surface.

- **The Desktop Model:** On large screens, the content is contained within a 1100px wrapper. The background outside this wrapper should feature a subtle wood grain texture.
- **Asymmetry:** To reinforce the scrapbook feel, elements should not perfectly align to a strict grid. Use variable padding (e.g., 24px on the left, 32px on the right) within content cards.
- **Mobile Reflow:** On mobile, the "Desk" background disappears, and the "Paper" texture becomes the primary background. Margins reduce to 16px, and multi-column layouts (like side-by-side photos) stack vertically.

## Elevation & Depth

Depth is achieved through **Physical Layering** rather than traditional soft shadows.

- **Paper Stacks:** Use multiple borders or very tight, slightly offset solid shadows (1px or 2px) to suggest sheets of paper stacked on top of each other.
- **Artifacts:** High-priority items like "pinned" posts should feature a digital "Push-pin" or "Paperclip" graphic that appears to hold the element to the background.
- **Chalkboard Inset:** The chalkboard areas should feel "recessed" into a wooden frame, using inner shadows (darker green/black) to create a carved-in look.
- **Photography:** Photos should have white borders (Polaroid style) and a very slight ambient drop shadow (4% opacity black) to appear as if they are resting on the paper.

## Shapes

The shape language is primarily **Soft (0.25rem)**, mimicking the natural wear of paper corners.

- **Standard Elements:** Use `rounded-sm` for buttons and input fields.
- **The "Notebook":** Large containers should have slightly irregular rounding or a "torn edge" CSS mask on one side to mimic a spiral-bound notebook or a ripped sheet.
- **Interactive Elements:** Buttons should feel like physical objects (stamps or stickers). Avoid perfectly circular "pill" shapes unless they represent a specific object like a bottle cap or a pin.

## Components

- **Buttons:** Styled as "Ink Stamps" or "Duct Tape" strips. Use solid fills (Primary Green or Secondary Red) with a slight "grunge" texture overlay.
- **Input Fields:** Designed to look like ruled paper lines. The "border-bottom" is the primary visual cue, using a light blue or grey to mimic notebook ruling.
- **Cards:** The primary container is a "Sheet of Paper." It features a light cream background, a subtle paper grain texture, and a thin, slightly "wobbly" border.
- **Chips/Tags:** Styled as "Dymo Labels" (embossed plastic) or small "Post-it" notes with a slight rotation.
- **Navigation:** Top navigation resembles a row of tabs at the top of a file folder.
- **Modals:** Designed to look like an open "Yearbook" or a "Folder" overlaying the main desk area.