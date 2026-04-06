# Design System Document: The Sonic Monolith

## 1. Overview & Creative North Star
**Creative North Star: "The Digital Curator"**
This design system is built to evoke the precision of a high-end recording studio and the soul of an art gallery. We move beyond the "template" look by embracing **Organic Brutalism**—a style characterized by massive, authoritative typography, vast negative space, and intentional asymmetry. The UI does not just hold content; it frames it as a premium artifact. By leveraging high-contrast serif headings against a dark, tonal abyss, we create a sensory experience that feels both rhythmic and silent.

---

## 2. Colors
Our palette is rooted in the "Abyssal Black" of a soundproofed studio, punctuated by "Electric Accents" that represent the energy of sound waves.

### The Color Tokens
*   **Background (Base):** `#121315` (Deep Charcoal)
*   **Primary (The Glow):** `#F2CA50` / `#D4AF37` (Metallic Gold) — Used for high-value CTAs.
*   **Secondary (The Pulse):** `#00F1FE` (Neon Blue) — Used for technical indicators and interactive highlights.
*   **Tertiary (The Mood):** `#D49CFF` (Aurora Purple) — Used for creative accents and soft depth.

### Core Color Rules
*   **The "No-Line" Rule:** 1px solid borders are strictly prohibited for sectioning. We define boundaries through **Background Shifts**. To separate sections, move from `surface` to `surface-container-low`.
*   **Surface Hierarchy & Nesting:** Use surface tiers to create "nested" depth. A `surface-container-highest` card should sit atop a `surface-container-low` section. This mimics the physical layering of sound equipment.
*   **The "Glass & Gradient" Rule:** Floating elements must use **Glassmorphism**. Apply `surface` colors at 60% opacity with a `24px` backdrop-blur. 
*   **Signature Textures:** For main CTAs, use a subtle linear gradient from `primary` (#F2CA50) to `primary-container` (#D4AF37) at a 135-degree angle to provide a metallic, light-catching sheen.

---

## 3. Typography
The typography is an exercise in editorial authority. We utilize a high-contrast pairing: a sharp, traditional Serif for emotional impact and a hyper-clean Sans-Serif for technical clarity.

*   **Display & Headlines (Noto Serif TC):** Sophisticated and sharp. For Traditional Chinese characters, increase `letter-spacing` to `0.05em` and `line-height` to `1.4` to ensure the complex strokes breathe.
*   **Body & Labels (Inter):** Modern and neutral. Body text should maintain a tracking of `-0.01em` for a premium, "tight" editorial feel.

### Typography Scale
*   **Display-LG (3.5rem / Noto Serif):** Reserved for hero titles and singular brand moments.
*   **Headline-MD (1.75rem / Noto Serif):** Section headers. Always use ample padding-top to separate from previous content.
*   **Body-LG (1rem / Inter):** Primary reading. High line-height (1.6) is mandatory for readability against dark backgrounds.
*   **Label-MD (0.75rem / Inter):** All-caps with `0.1em` letter-spacing for "technical metadata" or studio specs.

---

## 4. Elevation & Depth
In this system, elevation is a product of light and layering, not shadows.

*   **The Layering Principle:** Stacking `surface-container` tiers creates a "soft lift." 
    *   *Lowest:* Background context.
    *   *High:* Interactive elements or highlighted content.
*   **Ambient Shadows:** If an element must float (e.g., a modal or dropdown), use an extra-diffused shadow: `offset: 0 20px, blur: 40px, color: rgba(0, 0, 0, 0.4)`. Never use pure black shadows; use a tinted version of the surface color.
*   **The "Ghost Border" Fallback:** If a container lacks sufficient contrast, use a **Ghost Border**: `outline-variant` (#4D4635) at 15% opacity.
*   **Glassmorphism:** Use `backdrop-filter: blur(12px)` on all floating cards to allow the "neon" accents of the background to bleed through, softening the interface.

---

## 5. Components

### Buttons
*   **Primary:** Metallic Gold gradient. On hover, apply a `scale(1.05)` transform and a `box-shadow: 0 0 20px rgba(212, 175, 55, 0.4)`. 
*   **Secondary (Ghost):** Ghost Border with `0.5rem` roundedness. On hover, the border opacity shifts from 20% to 100%.

### Cards
*   **The Studio Card:** No borders. Uses `surface-container-low` background. 
*   **Interaction:** On hover, the background shifts to `surface-container-high` with a smooth `300ms` ease-in-out transition. Forbid the use of divider lines; use `2rem` of internal padding to separate header from content.

### Inputs
*   **Field Style:** Minimalist bottom-border only or a deep `surface-container-lowest` inset.
*   **Focus State:** The bottom border animates from `outline` to `secondary` (Neon Blue) with a subtle outer glow.

### Audio Visualizer (Context Specific)
*   **The Pulse:** Use `tertiary` (Aurora Purple) for waveform visualizations, utilizing a `linear-gradient` that fades to transparent at the bottom.

---

## 6. Do's and Don'ts

### Do:
*   **Do** use asymmetrical margins. For example, a headline might be offset 10% from the left grid line to create visual tension.
*   **Do** use "Breathing Room." If you think you have enough padding, double it.
*   **Do** ensure all Traditional Chinese text has increased line-height to prevent "ink-clogging" on dark screens.

### Don't:
*   **Don't** use pure `#000000` for text; it causes "smearing" on OLED screens. Use `on-surface` (#E3E2E5).
*   **Don't** use standard dividers. If content needs to be separated, use a `64px` or `128px` vertical gap.
*   **Don't** use harsh, fast animations. All transitions should mimic the physical world—smooth, weighted, and intentional (`cubic-bezier(0.23, 1, 0.32, 1)`).