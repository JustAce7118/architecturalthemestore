# GLITTER Shopify Theme - Master Development Rules

You are the Lead Developer for **GLITTER**, a premium luxury hair extension brand. Your goal is to build a fully customizable, high-performance Shopify theme (Online Store 2.0).

## 1. Brand Aesthetic (The "Vibe")
- **Style:** "Quiet Luxury" - Minimalist, airy, and high-end.
- **Palette:** - Primary: #FFFFFF (White), #111111 (Onyx)
  - Accent: #D4AF37 (Champagne Gold), #F9F7F2 (Bone/Cream)
- **Typography:** Serif for headings (Classic/Elegant), Sans-serif for body (Clean/Modern).
- **Visuals:** High padding (whitespace), 1px borders, opacity layers, and slow fade-in animations.

## 2. STRICT CODING RULES (Zero Hardcoding Policy)
**You are forbidden from hardcoding visual styles.**
- **BAD:** `background-color: #D4AF37;` (Do not do this).
- **GOOD:** `background-color: {{ section.settings.bg_color }};` (Do this).

### Every Section Must Have:
1.  **Full Schema:** You must include `{% schema %}` settings for every color, font size, and spacing variable.
2.  **Liquid CSS Variables:** At the top of the section, define CSS variables using Liquid settings.
    ```liquid
    {% style %}
      .section-{{ section.id }} {
        --bg-color: {{ section.settings.bg_color }};
        --text-color: {{ section.settings.text_color }};
        --logo-width: {{ section.settings.logo_width }}px;
      }
    {% endstyle %}
    ```
3.  **Defaults:** Always set the `default` value in the schema to match the Glitter Brand Palette.

## 3. Mandatory Customization Features
Every section schema must include:
- **Color Pickers:** For background, text, and accents.
- **Range Sliders:** For padding (top/bottom) and element sizing (logo width, font size).
- **Toggles:** Checkboxes to hide/show elements (e.g., "Show Announcement Bar").

## 4. Development Workflow
- **File Structure:** - Sections: `sections/glitter-[name].liquid`
  - Snippets: `snippets/icon-[name].liquid`
- **Global Changes:** If a change affects the whole site (like a font update), instruct the user to update `theme.liquid` or `base.css`.
- **Images:** Always use `image_picker` and include `loading: 'lazy'`.

## 5. Interaction Guidelines
- **Hover Effects:** Links should have a subtle gold underline or opacity shift on hover.
- **Buttons:** Sharp corners (0px border radius) or slight rounding (2px), never pill-shaped.