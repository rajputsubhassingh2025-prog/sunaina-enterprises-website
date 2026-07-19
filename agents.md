# AI Agent Guidelines (AGENTS.md)

Welcome, fellow agent! This document defines the architecture, design principles, conventions, and engineering constraints for **Sunaina Enterprises** website. Please read and respect these rules before modifying any code.

## 🏛️ System Architecture

This project is a high-performance, single-page, static marketing website designed to showcase a wholesale and distribution business. It has zero external dependencies or framework overhead, leading to near-instant loading times.

### 📁 Files and Roles

1. **`index.html`**: Contains the semantic HTML structural components.
   - Built with distinct landmark elements (`header`, `section`, `footer`) and clear `id` selectors for deep linking and scroll tracking.
   - Houses two **Netlify Forms** (`retailer-application` and `general-contact`), complete with standard attributes like `data-netlify="true"`, hidden `form-name` keys, and spam-filtering honeypots.
2. **`style.css`**: Consolidates all layout, styling, transitions, and responsive behavior.
   - Designed around CSS Custom Properties (`:root` variables) for modular theme support (using deep royal corporate navy and warm amber/gold colors).
   - Enforces specific z-index stacking layers to prevent conflicts with floating headers, nav menus, or modal targets.
3. **`script.js`**: Drives all client-side logic, interactivity, and submission handshakes.
   - Designed to run completely vanilla; do not introduce external framework packages (such as React, Vue, jQuery, etc.) unless specifically requested.
   - Combines scroll animations, mobile menu drawer states, and asynchronous AJAX submission pipelines.
4. **`logo.svg`**: Self-contained inline-compatible vector logo combining monogram emblem and text typography.

---

## 🎨 Design Philosophy & Guardrails

The site's visual language was intentionally designed under the **"Refined/Trustworthy Corporate"** theme to represent a reliable distribution entity.

### 🚫 Forbidden Patterns (AI Tells to Avoid)
- **No generic purple/blue gradients on pure white**: Maintain the deep corporate navy (`#0f2240`), gold (`#dfa634`), and warm eggshell/cream background (`#faf9f6`) colors.
- **No standard 3-column symmetric card grids**: The services grid has a featured center card (`service-card.featured`) with contrasting brand colors and customized badges to create visual weight and flow.
- **No boring map iframe or broken image placeholders**: The map is represented as a sleek CSS vector visualization (concentric pulsing circles, a floating physical-style pointer badge, and abstract grids) which loads instantly and preserves clean aesthetics.

---

## 🔒 Form Conventions & Netlify Integration

This site implements two AJAX-powered **Netlify Forms**. If you need to add or edit fields, follow these rules:

1. **Keep HTML Names Sync'd**: Every input must have a valid `name` attribute that uniquely identifies it.
2. **Ajax Submission Header**: Submissions must go via `POST` with `Content-Type: application/x-www-form-urlencoded`.
3. **Include `form-name`**: You MUST include the hidden `<input type="hidden" name="form-name" value="form-name">` field inside the form HTML. The JS submission payload reads this field via `FormData()`.
4. **Honeypot Support**: Maintain the silent honeypot field (`bot-field` input inside a hidden container) to filter automated spam without bothering the human user.
5. **No Full Reloads**: Always use the AJAX handler in `script.js` which transitions the wrapper element into a success card rather than performing standard page redirects.

---

## 📝 Coding and Styling Style Guide

- **BEM/Structured CSS**: Keep classes organized logically. Group section styles together under distinct CSS comments.
- **Transform-only animations**: For performance, animate only `transform`, `opacity`, or properties that do not trigger paint/layout reflows (e.g., never animate `height` or `top`).
- **Responsive-first**: Always test mobile displays. Menu transitions are handled via sliding drawers on screens $\le 768\text{px}$.
- **Access Web-Safe Assets**: Do not use hardcoded or broken image URLs. If images are required, write inline SVGs or generate/embed local vector formats.
