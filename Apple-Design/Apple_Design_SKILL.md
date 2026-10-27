---
name: apple-design
version: 2.0.0
description: A complete, Apple-inspired web UI/UX design and implementation skill. Apply automatically when creating, designing, implementing, auditing, or improving a website or web application. Covers design tokens, color systems, typography, layout, responsive CSS, components and states, accessibility, interaction design, motion, performance, and quality assurance. Use Apple's design principles as inspiration, not as a requirement to imitate Apple branding.
---

# Apple Design — Complete Web UI/UX Skill

## 0. Purpose and activation rules

This skill defines how an AI should plan, design, implement, review, and improve modern websites and web applications. It combines the original fluid-interaction guidance with a complete visual design system, current CSS capabilities, accessibility requirements, performance practices, and a repeatable quality process.

### 0.1 When to apply this skill

Apply this skill automatically whenever the user asks to create, build, design, code, prototype, review, redesign, or improve any of the following:

- a website, landing page, homepage, portfolio, business site, campaign page, blog, or online publication;
- a web app, dashboard, SaaS interface, admin interface, form flow, settings page, or interactive product UI;
- a component, navigation, card system, modal, sheet, carousel, menu, form, or other web UI pattern;
- an Apple-inspired interface, modern visual system, design system, interaction, gesture, or animation.

A prompt such as **“Create a website about [topic]”** is sufficient to activate the skill. Do not ask the user to mention this file or repeat its rules.

### 0.2 How to interpret a short request

When the user gives a topic but few design details:

1. Infer a coherent visual direction from the topic, audience, intended action, and tone.
2. Use sensible defaults for layout, typography, colors, responsive behavior, navigation, accessibility, and interactions.
3. Do not block progress with a long questionnaire. Ask a question only when an essential unresolved fact prevents a useful implementation. Otherwise, make a reasonable assumption and proceed.
4. Do not assume every site needs glassmorphism, dramatic gradients, animated hero sections, cards, or Apple-like chrome. Choose only elements that support the content and purpose.
5. Do not invent company facts, testimonials, statistics, certifications, customer logos, legal claims, or product capabilities. Use clearly marked, specific placeholders only where source information is genuinely missing.
6. If the request is for a working website, create working implementation code, not merely a visual description. If file-generation tools are available, deliver the requested complete files.
7. If the user provides an existing project or code, inspect it first and preserve its stack, architecture, branding, and working behavior unless a change is requested. Avoid unrelated refactors and new dependencies.

### 0.3 Default implementation policy

Unless the user or existing project specifies otherwise:

- Use semantic HTML, modern CSS, and vanilla JavaScript for a self-contained page or small site.
- Follow the existing framework and conventions in an existing project; do not introduce a new framework solely for convenience.
- Use mobile-first responsive layout and progressive enhancement.
- Keep design tokens centralized and reusable.
- Separate structure, styling, and behavior when the project format supports separate files.
- Include all files required for the requested result. Do not replace important implementation with “...” or unexplained pseudocode.
- Avoid unnecessary dependencies, trackers, external scripts, remote fonts, or network calls.
- Do not claim to have tested a browser, screen reader, build, or performance metric unless that test was actually performed. State unverified items transparently.

### 0.4 Design intent: Apple-inspired, not Apple-copied

Use Apple's widely recognizable design strengths as principles: clarity, restraint, hierarchy, purposeful motion, spatial consistency, strong typography, deliberate materials, and immediate feedback. Do not mechanically copy a specific Apple product page or imply that a site is affiliated with Apple. Adapt the principles to the user's brand, subject matter, audience, and requirements.

### 0.5 Rule categories

Every recommendation in this skill belongs to one of these categories:

- **Requirement:** Must be satisfied for the requested functionality, accessibility target, safety, or technical correctness.
- **Default recommendation:** Preferred starting point for a high-quality design; adjust only for a reason.
- **Contextual option:** Use only when it improves the actual experience and is supported by the target environment.

Do not turn aesthetic preferences into technical mandates. Do not describe a recommendation as a legal requirement unless the applicable rule and scope support that claim.

---

## 1. Design foundations and decision-making

Design the interface around the user's task. Visual polish is not a substitute for clarity, useful content, predictable behavior, or accessibility.

Use the following principles to assess each significant decision:

1. **Purpose:** Every feature, effect, and element must serve a clear objective. Remove visual decoration that competes with the content or action.
2. **Agency:** Keep the user in control. Make actions predictable, allow recovery where possible, and provide Undo for reversible mistakes when practical. Reserve confirmation dialogs for genuinely destructive or irreversible actions.
3. **Responsibility:** Respect privacy, security, consent, and user settings. Collect only necessary information. Communicate risks and outcomes plainly.
4. **Familiarity:** Use recognizable patterns and consistent behavior. Controls that look alike should behave alike. Depart from familiar conventions only when the benefit is clear and testable.
5. **Flexibility:** Support different screens, input types, text sizes, languages, abilities, and levels of expertise. Prefer adaptable layouts to one fixed composition.
6. **Simplicity, not simplistic minimalism:** Reduce cognitive load, not necessary information. An interface that hides essential options behind obscure interactions is not simple.
7. **Craft:** Ensure alignment, spacing, typography, contrast, iconography, motion, and error handling are deliberate and consistent.
8. **Delight:** Add moments of refinement only after usability, legibility, accessibility, and reliability work. Delight is not a justification for friction.

### 1.1 Visual hierarchy

Each page or viewport should make these answers easy to identify:

- What is this page or product?
- What is the most important information?
- What can I do here?
- What happens if I activate the primary action?
- Where can I go next, and how do I return?

Create hierarchy through type scale, layout, whitespace, contrast, grouping, and placement. Do not rely on color or animation alone.

### 1.2 Restraint and consistency

- Establish a small set of visual rules and use them consistently.
- Prefer a few clear levels of emphasis instead of many competing accent treatments.
- Avoid using a different radius, shadow, gradient, spacing value, or animation curve for every component.
- Use whitespace to signal grouping and priority, not merely to make the page look sparse.
- Do not add a card around every content block. Use grouping, dividers, background regions, and open layout where appropriate.
- Do not use animated movement, translucent surfaces, or decorative graphics when they make content harder to read or interactions harder to predict.

---

## 2. Design-token architecture

Treat the design system as a coherent set of tokens, not as scattered literal values. The token system must cover color, type, spacing, sizing, radius, border, shadow, motion, layers, and responsive behavior.

### 2.1 Token layers

Use three conceptual layers:

1. **Primitive tokens:** Raw scales such as neutral-100, blue-600, space-4, radius-3, or shadow-2.
2. **Semantic tokens:** Role-based tokens such as `--color-text-primary`, `--surface-page`, `--border-subtle`, or `--color-danger`.
3. **Component tokens:** Tokens for component-specific variations when necessary, such as `--button-primary-bg` or `--dialog-shadow`.

Components should normally consume semantic tokens, not scattered primitive values. Component tokens should be introduced only when they solve a real need; do not over-tokenize one-off decorations.

### 2.2 Centralize tokens

Store reusable values in CSS custom properties, a theme configuration, or the project's native token system. Keep token names descriptive and stable. Do not duplicate the same conceptual value under several unrelated names.

Example structure (illustrative values only; create a palette appropriate to each project):

```css
:root {
  /* Color primitives */
  --palette-neutral-0: #ffffff;
  --palette-neutral-50: #f7f8fa;
  --palette-neutral-100: #eef1f4;
  --palette-neutral-200: #dce2e8;
  --palette-neutral-400: #9aa7b5;
  --palette-neutral-600: #596675;
  --palette-neutral-800: #27313d;
  --palette-neutral-950: #111820;

  /* Semantic colors */
  --color-text-primary: var(--palette-neutral-950);
  --color-text-secondary: var(--palette-neutral-600);
  --color-text-inverse: var(--palette-neutral-0);
  --surface-page: var(--palette-neutral-0);
  --surface-subtle: var(--palette-neutral-50);
  --surface-raised: var(--palette-neutral-0);
  --border-default: var(--palette-neutral-200);

  /* Spacing */
  --space-1: 0.25rem;
  --space-2: 0.5rem;
  --space-3: 0.75rem;
  --space-4: 1rem;
  --space-6: 1.5rem;
  --space-8: 2rem;
  --space-12: 3rem;
  --space-16: 4rem;

  /* Shape */
  --radius-xs: 0.25rem;
  --radius-sm: 0.5rem;
  --radius-md: 0.75rem;
  --radius-lg: 1rem;
  --radius-xl: 1.5rem;
  --radius-pill: 999px;

  /* Typography */
  --font-sans: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  --font-mono: ui-monospace, SFMono-Regular, Consolas, monospace;
  --text-xs: 0.75rem;
  --text-sm: 0.875rem;
  --text-md: 1rem;
  --text-lg: 1.125rem;

  /* Focus */
  --focus-width: 3px;
  --focus-offset: 3px;

  /* Timing */
  --duration-fast: 120ms;
  --duration-normal: 200ms;
  --duration-slow: 320ms;
  --ease-standard: cubic-bezier(0.2, 0, 0, 1);
}
```

This is a starting structure, not a mandatory palette or complete token library. Generate the full set needed by the actual page and validate the color pairings. Never assume that example colors meet contrast requirements without checking them.

### 2.3 Token governance

- Name tokens by role, not appearance alone. Prefer `--color-text-muted` over `--gray-600` in component styles.
- Define tokens once and reuse them. Avoid magic numbers scattered across stylesheets.
- Keep the number of scale steps finite and purposeful.
- Permit a documented exception only where a component has a genuine special need.
- Document the intended use and contrast pairing of semantic color tokens.
- Make tokens adaptable to light/dark themes and user preferences where themes are supported.
- If a project already has a token system, extend it rather than creating a competing naming convention.

---

## 3. Color system and color samples

A professional color system contains a palette, semantic roles, component states, theme mappings, and verified contrast combinations. A list of brand hex values alone is not a color system.

### 3.1 Build a purposeful palette

Define colors in families appropriate to the brand:

- **Brand/primary scale:** Main brand hue and lighter/darker steps for backgrounds, borders, controls, and emphasis.
- **Accent scale:** Secondary hue for distinct but restrained emphasis, if needed.
- **Neutral scale:** Page backgrounds, elevated surfaces, body text, subdued text, separators, disabled controls, and overlays.
- **Feedback scales:** Success, warning, danger/error, and information.
- **Data-visualization colors:** Distinguishable categorical colors and accessible sequential/diverging scales when charts are needed.

Do not require every site to use every family. Use only the colors that have a clear role.

### 3.2 Required semantic roles

At minimum, consider definitions for:

- page background and alternate section background;
- raised surface, overlay surface, and inverse surface;
- primary, secondary, muted, inverse, and disabled text;
- primary, secondary, subtle, hover, active, and disabled controls;
- default, subtle, strong, and focus borders;
- link, link-hover, and visited link when visited-state differentiation is useful;
- focus indicator;
- success, warning, danger, and informational foreground/background pairs;
- selection, highlight, and scrim/overlay;
- chart series and data emphasis when applicable.

### 3.3 Color states and palette samples

Create clear palette samples in design documentation or a reference page. Each sample should include:

- token name;
- color value;
- intended role;
- foreground/background combinations allowed;
- computed contrast ratio where relevant;
- light/dark theme mapping, if supported.

A palette swatch is only a visual reference; the implementation must consume the corresponding tokens.

### 3.4 Contrast and color meaning

Use WCAG 2.2 AA as the default accessibility baseline unless the user specifies a stronger or legally applicable target.

- Normal text: at least 4.5:1 contrast.
- Large text: at least 3:1 contrast. Use WCAG definitions for what counts as large text; do not infer this solely from a designer's visual impression.
- Necessary non-text graphical information and control boundaries: generally at least 3:1 against adjacent colors where the criterion applies.
- Never communicate status using color alone. Pair color with text, iconography, shape, pattern, or another visible indicator.
- Do not assume that a translucent foreground passes contrast. Evaluate the worst plausible background behind it, or use a sufficiently opaque surface.
- Test hover, active, disabled, selected, error, and focus states, not only the default state.
- Disabled elements have specific WCAG exceptions, but remain as legible and understandable as practical.

### 3.5 Light and dark themes

When both themes are included:

- Map semantic tokens separately for each theme; do not simply invert all colors.
- Recheck contrast independently in each theme.
- Preserve state differentiation and brand recognizability.
- Provide a clear manual theme control if the product exposes one, and use the system preference as a sensible default where appropriate.
- Avoid flash-of-wrong-theme when theme state is persisted, while respecting privacy and architecture constraints.
- Ensure charts, images, illustrations, logos, borders, and shadows remain appropriate in both themes.

### 3.6 Translucency and color blending

Glass, blur, vibrancy, and translucent overlays are contextual options, not required style elements.

- Use them only where separation, hierarchy, or spatial continuity benefits from translucency.
- Verify contrast on varying content behind the surface.
- Provide a sufficiently opaque fallback and honor `prefers-reduced-transparency` when supported.
- Do not stack several translucent layers if the combined effect weakens legibility.
- Prefer solid surfaces for dense text, high-stakes forms, long tables, and content that must remain consistently readable.
- Do not place critical text directly over an unpredictable image without a reliable contrast treatment.

---

## 4. Typography system

Typography must be specified as a complete hierarchy, not only as advice about optical sizing or letter spacing.

### 4.1 Font selection

- Prefer a system font stack when it fits the design and helps performance. Use a custom font only when it adds meaningful brand or readability value.
- If a custom font is used, define licensing/source requirements, supported weights, fallbacks, loading strategy, and subset/character coverage.
- Avoid loading many font families and weights without reason.
- Do not assume that SF Pro or another Apple system font is available as a web font on every platform. Use appropriate system fallbacks and respect licensing.
- Use a monospace family for code or tabular technical data only where that improves clarity.

### 4.2 Typography tokens

Define named text roles for the actual site, including where relevant:

- display/hero;
- H1, H2, H3, H4, H5, H6;
- lead/intro paragraph;
- body/default;
- body-small;
- label/form label;
- button;
- navigation;
- caption/metadata;
- legal/help text;
- code/tabular numbers.

For every role, define font family, size, weight, line-height, letter-spacing, and text transformation if any. Typography role names should describe function, not force the same HTML element in every context.

### 4.3 Scale and line length

- Use a consistent scale rather than arbitrary sizes on every element.
- Use `rem` or `em` for most text sizing so user font preferences can be respected.
- Use `clamp()` for fluid display sizes where it improves the result, with a sensible minimum and maximum.
- Keep headings visually distinct without skipping the semantic heading structure.
- Constrain long-form text to a comfortable measure; around 60–75 characters per line is a useful starting point, not a rigid rule for every language or interface.
- Give body copy more generous line-height than large display headings in most cases.
- Dense UI can use tighter rhythm, but must remain readable and must not clip localized or zoomed text.
- Recheck line wraps for long words, dates, prices, translated text, and larger text settings.

### 4.4 Optical sizing and variable fonts

- Use `font-optical-sizing: auto` when the chosen variable or optical font supports it.
- Use `font-variation-settings` or high-level properties such as `font-weight` only when the font supports the relevant axes and the design benefits from the control.
- Common axes may include weight (`wght`), width (`wdth`), slant (`slnt`), italic (`ital`), and optical size (`opsz`); availability differs by font.
- Prefer standard high-level CSS properties when they express the intended choice. Avoid unnecessary low-level axis values that override accessible/user-friendly behavior.
- Tracking should vary with type size and the chosen typeface. Large display text often benefits from modest negative tracking; small all-caps labels may need positive tracking. Treat these as design decisions, not universal constants.

### 4.5 Text wrapping

- Consider `text-wrap: balance` for short headings, short callouts, and brief lead text to avoid awkward line distribution.
- Consider `text-wrap: pretty` for selected long-form paragraphs where better line endings outweigh the potential extra layout work.
- Do not apply `balance` indiscriminately to long article content; browser balancing is intended for a limited number of lines and can behave differently across engines.
- Always test translations, narrow screens, larger text, and content that changes dynamically.
- Use robust widths and max-width constraints rather than relying on manual `<br>` elements to force a particular wrap, except where a line break is editorially intentional.

### 4.6 Font rendering

Do not use `-webkit-font-smoothing: antialiased` as a universal “Retina” or quality fix. It is non-standard and platform-specific, and may make text appear thinner. Prefer a suitable typeface, font weight, size, contrast, and browser-native rendering. Introduce non-standard rendering properties only for a tested, documented, platform-specific reason.

### 4.7 Semantic hierarchy

- Use native heading elements in a logical outline. Do not choose heading levels merely to obtain a visual size.
- Use paragraphs for prose, lists for grouped items, and labels tied to form controls.
- Ensure emphasis remains meaningful without color or font weight alone.
- Avoid long passages set entirely in uppercase or italics.

---

## 5. Layout, spacing, grid, shape, and elevation

### 5.1 Spacing scale

Define a finite spacing scale and use it consistently for padding, margin, gap, section rhythm, and component internals. A 4px or 8px base can be useful, but no particular base is mandatory.

- Use small spacing values for closely related items.
- Use larger values to separate distinct groups and page sections.
- Prefer `gap` for layout relationships when it is clearer than margins on individual children.
- Avoid arbitrary one-off spacing values unless they solve a documented optical or layout issue.
- Use `clamp()` for fluid spacing only when gradual scaling improves the experience. Do not make every spacing token fluid by default.

Example:

```css
:root {
  --space-section: clamp(3rem, 7vw, 7rem);
  --space-page-inline: clamp(1rem, 4vw, 3rem);
}

.section {
  padding-block: var(--space-section);
}

.container {
  width: min(100%, 76rem);
  padding-inline: var(--space-page-inline);
  margin-inline: auto;
  box-sizing: border-box;
}
```

### 5.2 Content width and page grid

- Set deliberate max-widths for reading content, dashboards, and wide visual compositions.
- Use a consistent page container, inline padding, grid gaps, and section spacing.
- Choose columns from content needs; do not use a twelve-column grid as decoration when a simpler grid suffices.
- Use CSS Grid for two-dimensional alignment and Flexbox for one-dimensional arrangements.
- Use Subgrid when nested content genuinely needs to align with parent tracks, such as repeated cards with aligned headings/actions. Do not add it just because it exists.
- Ensure the design works between breakpoints, not only at named device widths.

### 5.3 Radius hierarchy

Define a coherent radius scale for small controls, standard controls/cards, larger surfaces, and pills/circular controls. The relationship should remain consistent across the interface. Do not give every card a giant radius by default; fit radius to the product's tone and component size.

### 5.4 Borders and separators

- Define semantic border tokens for subtle separators, default outlines, stronger boundaries, and focus rings.
- Do not rely on pale borders alone to distinguish important controls if contrast is insufficient.
- Use dividers when they clarify grouping; use whitespace where a line would add unnecessary noise.
- Border thickness and color should remain consistent across components.

### 5.5 Elevation and shadow tokens

Use elevation sparingly to communicate layering, overlap, and interactive priority—not to decorate every surface. Where useful, define a small scale such as `shadow-1` through `shadow-4`, with deliberate changes in blur, spread, offset, and opacity.

- A card sitting in normal document flow may need no shadow.
- Floating menus, popovers, sheets, and dialogs may need stronger separation.
- Shadow and background must remain visible in light and dark themes.
- Do not use shadow as the only indicator of boundaries or focus.
- Multi-layer shadows can create a more natural result but are a design option, not a universal Apple rule.

### 5.6 Layer order

Create a documented z-index/layer scale for ordinary content, sticky navigation, menus/popovers, backdrops, dialogs, and emergency notices. Avoid random values such as `z-index: 999999` spread through the code. Define which layers establish stacking contexts and how nested overlays behave.

---

## 6. Responsive and adaptive UI

Build the smallest usable layout first, then expand where content and interaction benefit from the available space. Responsive design is not merely shrinking desktop UI.

### 6.1 Required behavior

- Prevent horizontal overflow at narrow widths, except in components where horizontal scrolling is intentional and usable.
- Preserve content order and primary action priority across viewport sizes.
- Ensure navigation works with touch, keyboard, and pointer input.
- Reflow cards, columns, tables, forms, and media according to content needs.
- Support zoom and larger text without clipping controls, hiding information, or creating overlapping fixed elements.
- Test long labels, localization, empty/loading/error states, and data with realistic lengths.

### 6.2 Media and container queries

- Use media queries when the viewport or user/device preference should control presentation.
- Use Container Queries (`@container`) when a reusable component should adapt to the width of its own layout container rather than the overall viewport.
- Name containers when that improves clarity.
- Provide a reasonable layout that still works without optional enhancements if the project's browser support requires a fallback.
- Avoid a proliferation of arbitrary breakpoints; define breakpoints where the layout starts to fail or where the content can use more space.

### 6.3 Adaptive components

Specify what changes for narrow containers: stacking order, image ratio, text size, internal padding, button width, action placement, content density, and optional secondary details. Prefer a deliberate component adaptation over scaling every dimension proportionally.

### 6.4 Sticky and fixed elements

- Use sticky/fixed positioning only when it materially improves navigation or task continuity.
- Account for safe areas, scroll position, focus visibility, zoom, and overlays.
- Never obscure headings or focused controls behind sticky UI.
- Avoid fixed mobile footer actions that hide form content or browser controls.

---

## 7. Component system and interaction states

Design components as reusable patterns with clear anatomy, variants, sizes, accessibility behavior, and state rules. Do not allow visually similar components to acquire inconsistent dimensions or behaviors.

### 7.1 Component specification

For each recurring component, define as appropriate:

- purpose and when to use it;
- semantic HTML element or ARIA pattern;
- anatomy and content order;
- variants and sizes;
- typography, color, spacing, radius, border, and elevation tokens;
- normal, hover, focus, active/pressed, selected, disabled, loading, success, and error states where applicable;
- keyboard and pointer behavior;
- responsive behavior;
- reduced-motion behavior;
- error and empty-state behavior;
- testing requirements.

### 7.2 Components to consider

Use only what the task needs, but consider the following inventory:

- buttons, links, icon buttons, segmented controls;
- text inputs, textareas, selects, checkboxes, radio groups, switches, date fields;
- navigation, mobile navigation, breadcrumbs, tabs, pagination;
- cards, lists, tables, badges, tags, status indicators;
- accordions, tooltips, popovers, menus, dialogs, sheets;
- alerts, toasts, inline feedback, progress indicators, skeletons;
- search, filters, sorting, empty states, confirmation and Undo patterns;
- charts or data visualizations when the content requires them.

### 7.3 Button and link rules

- Use `<button>` for actions and `<a>` for navigation.
- Provide clear labels that describe the action or destination.
- Make primary, secondary, tertiary, and destructive variants visually distinct but consistent.
- Do not use color alone to distinguish destructive actions.
- Define pressed and focus states; do not let pointer `:active` replace visible keyboard focus.
- Give icon-only controls an accessible name and a sufficiently large target.
- Avoid disabled controls when explaining why an action cannot be performed inline would be more helpful; when disabled is necessary, explain the condition.
- Ensure links are distinguishable from surrounding text without relying only on color where that is needed for recognition.

### 7.4 Forms and validation

- Associate every form control with a programmatic label.
- Keep instructions near the field they explain.
- Validate data at an appropriate time and identify errors in plain language.
- Explain how to fix an error; do not rely on a red border alone.
- Preserve correctly entered data when possible after errors.
- Use the correct input type and autocomplete attributes where applicable.
- Show loading, success, and failure states for submitted forms.
- Do not erase entries automatically without a clear reason.
- Avoid exposing personal or sensitive input unnecessarily in status messages or logs.

### 7.5 Dialogs, popovers, and menus

- Use native HTML or established accessible patterns where practical.
- Keep the relationship to the trigger clear.
- Manage focus on open and restore it appropriately on close.
- Support Escape where consistent with the pattern and avoid trapping users unexpectedly.
- For modal dialogs, prevent interaction with background content while open and make the modal boundary clear.
- Avoid placing a focusable element behind an overlay that appears to be modal.
- Do not use a dialog for every confirmation; avoid unnecessary interruptions.
- Match enter/exit paths when spatial continuity is useful, but do not prioritize animation over clarity or speed.

### 7.6 Feedback and status

Represent status in a way the user can see and, where needed, assistive technology can announce. Distinguish progress, completion, warning, error, and neutral information. Messages should be specific, concise, placed near the affected content, and persistent long enough to be understood. Nonessential toast messages should not be the only place where important information is available.

---

## 8. Information architecture and page patterns

A visually polished page can still fail if users cannot understand its structure or next action. Design page architecture around user intent and content relationships.

### 8.1 Common page types

Choose and adapt patterns for the actual request, for example:

- homepage or landing page;
- product/service detail page;
- editorial/article page;
- search results or listing page;
- contact, registration, checkout, or multi-step form;
- dashboard, admin, or data-heavy interface;
- login, settings, account, and permissions pages;
- not-found, error, offline, and access-denied pages.

Each page does not need a separate template if a shared pattern serves its purpose. Avoid forcing the same hero, card grid, or CTA structure onto every page.

### 8.2 Page composition

Identify:

1. the page's primary purpose;
2. the main audience and task;
3. the key information that supports the task;
4. the primary action and appropriate secondary actions;
5. navigation and orientation cues;
6. trust, privacy, or evidence information needed to make a decision;
7. the most useful next step after completion.

Use actual meaningful content. Do not fill a page with generic marketing copy, repeated slogans, invented metrics, or placeholder sections solely to make it look complete.

### 8.3 Navigation and wayfinding

- A user should be able to tell where they are, what options are available, and how to return.
- Use specific labels rather than vague section names when the destination can be named plainly.
- Highlight the current section or route accessibly.
- Keep navigation structure consistent across pages.
- Avoid hover-only menus and inaccessible nested menus.
- For mobile navigation, provide clear open/close behavior and keyboard support.

---

## 9. Images, iconography, and data visualization

### 9.1 Images and media

- Select media that serves the content, helps recognition, or adds meaningful atmosphere.
- Define aspect ratios, crop behavior, `object-fit`, and focal-point behavior for repeated media types.
- Use responsive image sources and appropriate formats when the project supports them.
- Set dimensions or aspect ratios to reduce layout shifts.
- Avoid remote imagery with uncertain availability or licensing in production code. Do not fabricate asset URLs.
- Use descriptive alternative text for informative images; empty alt text for decorative images; avoid restating adjacent text.
- Provide captions, transcripts, or equivalent access for meaningful audio/video content as appropriate.
- Keep text legible when placed over images using a controlled overlay or solid surface.

### 9.2 Icons

- Use a consistent icon family, style, stroke/fill treatment, and optical size.
- Align icons to the visual center and font metrics, not just the element box.
- Choose familiar metaphors and avoid ambiguous icons for critical actions.
- Provide visible text for ambiguous actions and accessible names for icon-only controls.
- Decorative icons should not create redundant screen-reader announcements.
- Avoid mixing emoji, filled icons, line icons, and custom illustrations without a deliberate system.

### 9.3 Data visualization

- Use chart types that fit the data and user question.
- Ensure series remain distinguishable without color alone; use labels, shapes, line styles, or direct annotations as appropriate.
- Validate text and graphical contrast, including grid lines and focusable chart controls.
- Provide units, scales, legends, and meaningful empty/error states.
- Avoid decorative 3D effects that make values harder to compare.

---

## 10. Accessibility requirements

Accessibility is part of the design and implementation, not a final cosmetic pass. Use WCAG 2.2 AA as the default target when applicable, while recognizing that the site's legal obligations depend on its context and jurisdiction. This skill is not a substitute for a formal legal compliance assessment.

### 10.1 Semantics and structure

- Use native HTML elements before custom ARIA widgets.
- Maintain meaningful heading hierarchy, landmarks, lists, labels, buttons, and links.
- Ensure every control has an accessible name, role, state, and value as applicable.
- Use ARIA only to convey semantics or state that native HTML does not already provide. Incorrect ARIA can make the interface less accessible.
- Do not use `aria-hidden="true"` on focusable content or on a parent containing active focus.
- If a custom component behaves like a known widget, implement the complete keyboard and focus behavior—not only its ARIA attributes.

### 10.2 Keyboard and focus

- All functionality must be available by keyboard, unless a specific exception legitimately applies.
- Preserve a visible focus indicator. Never remove outlines without providing an equivalent visible indicator.
- Use `:focus-visible` to apply a carefully designed keyboard-focus ring while retaining visible focus for relevant input methods.
- Ensure focus is not hidden by sticky headers, fixed footers, popovers, or dialogs.
- Maintain a logical tab order and do not use positive `tabindex` values as a layout mechanism.
- Manage focus when opening/closing modal UI and when dynamic updates would otherwise disorient users.

Example:

```css
:where(a, button, input, select, textarea, [tabindex]):focus-visible {
  outline: var(--focus-width, 3px) solid var(--color-focus, #245fdb);
  outline-offset: var(--focus-offset, 3px);
}
```

This is a pattern, not an automatically compliant color choice. Choose and test the actual focus color and offset against all adjacent surfaces.

### 10.3 Pointer and touch targets

- WCAG 2.2 AA generally requires a target of at least 24 × 24 CSS pixels, subject to the criterion's spacing and other exceptions.
- Use 44 × 44 CSS pixels as a practical design target for important touch interactions when the layout permits. This is a recommended web design target, not a universal WCAG 2.2 AA minimum and not the same unit as Apple's 44-point recommendation for native interfaces.
- Keep nearby targets separated so users do not activate an unintended control.
- Provide a non-dragging single-pointer alternative for drag-operated functionality unless the dragging action is essential or an applicable exception applies.
- Do not make a required action depend solely on hover, precise multi-touch, device tilt, sound, vibration, or color perception.

### 10.4 Screen readers and live updates

- Use native controls and labels before `aria-*` attributes.
- Use `aria-expanded`, `aria-controls`, `aria-pressed`, `aria-selected`, `aria-current`, or other state attributes only where they match the component's actual behavior.
- Use live regions for meaningful asynchronous status updates, not every animation frame or every keystroke.
- Choose `aria-live="polite"` or assertive announcements according to urgency, and avoid repeated announcements.
- Manage the accessibility tree of modal/background layers carefully. Do not conceal the active dialog or leave focusable background controls available behind a modal.
- Ensure drag/drop and reorder operations expose a usable keyboard or button-based alternative and announce the result clearly where needed.

### 10.5 Motion, transparency, contrast, and text resizing

Respect user preferences where supported:

- `prefers-reduced-motion: reduce`: reduce large/continuous motion, parallax, spring overshoot, and nonessential transitions; preserve necessary state feedback.
- `prefers-reduced-transparency: reduce`: use more opaque backgrounds and reduce blur/translucency when supported.
- `prefers-contrast: more`: strengthen boundaries and foreground/background distinction where supported.
- Support browser zoom and text enlargement without lost content or functionality.
- Test contrast in all interaction states, themes, and overlay compositions.

### 10.6 Accessibility testing

Automated checks are useful but insufficient. Include manual keyboard testing and, for relevant production work, screen-reader testing. Do not report WCAG conformance based only on passing an automated scanner.

---

## 11. Modern CSS and browser capabilities

Use modern CSS where it makes the design clearer, more robust, or easier to maintain. Feature availability changes, so check current support for the project's browser targets before relying on a feature. Prefer progressive enhancement over brittle polyfills.

### 11.1 Container Queries

Use `container-type: inline-size` and `@container` when a component should adapt to its containing layout rather than the viewport. Provide a reasonable base layout and, where required, a fallback. Avoid unnecessary query nesting and container contexts.

### 11.2 Subgrid

Use `subgrid` when nested grids need to align rows or columns with a parent grid. Typical examples include card collections with aligned titles, body content, and actions. Retain a graceful fallback if the supported browser range requires it.

### 11.3 Fluid sizing with `clamp()`

Use `clamp(min, preferred, max)` to control fluid typography, spacing, and container dimensions where a gradual change is helpful. Set a meaningful minimum and maximum. Do not scale every property by viewport width, and test at zoomed and narrow sizes.

### 11.4 Text wrapping

Use `text-wrap: balance` selectively for short display headings and `text-wrap: pretty` selectively for body copy where improved line endings are worth the cost. Avoid forced line breaks as a substitute for responsive typography.

### 11.5 Scroll-driven and scroll-triggered animations

CSS scroll timelines may be used for small, progressive visual treatments such as a reading progress indicator or a carefully restrained reveal. They are not an automatic replacement for JavaScript, Intersection Observer, or gesture physics.

- Check browser support and supply an acceptable no-animation/static fallback.
- Honor reduced-motion preferences.
- Never make content visibility, navigation, or essential state comprehension depend on the animation.
- Avoid parallax or large-scale effects that distract, cause discomfort, or degrade scrolling.
- Measure performance in the target environment.

### 11.6 Viewport and safe-area units

Use modern viewport units such as `svh`, `lvh`, or `dvh` where they solve mobile browser-chrome sizing problems. Consider safe-area insets for fixed/edge-to-edge UI. Provide a fallback where target browser support demands it.

### 11.7 CSS architecture

- Use logical properties such as `margin-inline`, `padding-block`, and `inset-inline-start` where appropriate for writing-mode and localization flexibility.
- Consider CSS Cascade Layers (`@layer`) when the project needs an explicit precedence structure.
- Use `:where()` to reduce selector specificity for reusable rules and `:focus-visible` for suitable focus states.
- Use `@supports` for optional enhancements when an unsupported value could materially affect the result.
- Avoid excessive selector specificity, blanket `!important`, and unnecessary global selectors.
- Prefer native layout features over JavaScript calculations when they meet the requirement.
- Do not use a CSS capability solely because it is new; justify it by the problem it solves.

### 11.8 Variable fonts and system rendering

Use variable font axes only when available in the selected font and tested across the target environment. Do not force non-standard font-smoothing properties globally. Native text rendering is the default unless a tested platform-specific need justifies an exception.

---

## 12. Performance, rendering, and resilience

Performance is part of UX. A visually polished page that shifts, blocks input, consumes excessive resources, or delays content is not finished.

### 12.1 Animation performance

- Prefer `transform` and `opacity` for common motion when possible; they are often cheaper to animate than layout-affecting properties.
- Do not assume a property is performant without profiling the actual page.
- Avoid animating layout-intensive properties across many elements during continuous gestures.
- Keep per-frame JavaScript work small and schedule visual work with `requestAnimationFrame` where appropriate.
- Handle interruption, cancellation, and cleanup for event listeners, observers, animation instances, and timers.

### 12.2 `will-change`

`will-change` is a hint for likely near-future changes, not a general speed switch. Do not apply it permanently to large numbers of elements. Add it only when profiling identifies a benefit, limit it to elements that are about to animate, and remove it when no longer needed where practical.

### 12.3 Containment and `content-visibility`

- Consider `contain` and `content-visibility: auto` for large, independent content regions or long lists when measurement shows a benefit.
- Understand their effects on layout, paint, intrinsic sizing, accessibility tooling, sticky positioning, and focus navigation before applying them broadly.
- Provide intrinsic size estimates where appropriate to reduce layout shifts.
- Do not hide important content from assistive technology or make focused content unavailable through careless use of visibility/containment.
- Profile real content; these properties are not automatically beneficial for every component.

### 12.4 Images, fonts, and content shifts

- Set width/height or an aspect ratio for media to reserve layout space.
- Avoid unnecessary font files and use suitable fallbacks to reduce layout shifts.
- Lazy-load below-the-fold media when appropriate; do not lazy-load the primary above-the-fold hero image by default without reason.
- Avoid autoplaying large video backgrounds unless the request demands them and accessible alternatives are provided.
- Keep critical content available if remote resources fail.

### 12.5 Resource economy

- Avoid adding libraries when native functionality is enough.
- Avoid permanent animation loops when no useful information is conveyed.
- Respect reduced data, battery, and motion contexts where practical.
- Avoid loading third-party services, analytics, fonts, or scripts without a reason and any necessary privacy review.

### 12.6 Resilience

Ensure the page degrades sensibly if optional CSS, JavaScript, fonts, images, or API responses fail. Core content and navigation should remain understandable. Never rely on a decorative animation to expose essential information.

---

## 13. Interaction design and complete state handling

A site must be designed for normal, loading, empty, success, failure, and interrupted states—not only the ideal screenshot.

### 13.1 State inventory

For applicable components and page regions, account for:

- initial/loading;
- loaded/default;
- hover, focus, active/pressed;
- selected/expanded/collapsed;
- disabled or unavailable;
- empty/no results;
- validation error;
- server or network failure;
- success/completion;
- partial completion;
- interrupted/cancelled;
- permission denied or authentication required;
- unsaved changes and recovery.

Do not implement all states on every component. Select those relevant to the actual workflow and document the reason where a state is intentionally not applicable.

### 13.2 Feedback timing and clarity

- Show acknowledgement as soon as a meaningful interaction begins, when the user needs it.
- For asynchronous work, communicate progress or continued processing instead of leaving the interface apparently frozen.
- Confirm meaningful completion, but do not generate noisy feedback for every minor pointer movement.
- Place validation errors near the affected input and summarize form errors when the form is long.
- Preserve the user's work when possible after an error or network interruption.
- Use specific labels such as “Save changes” rather than generic “OK” when the consequence needs clarity.

### 13.3 Undo and destructive actions

Prefer Undo for reversible actions. Confirm only actions whose consequences are substantial, hard to reverse, or genuinely ambiguous. Clearly label the destructive action, and do not make the safe path visually or spatially obscure.

---

## 14. Security, privacy, and trust in interface design

Although this is a design skill, UI decisions can create security and privacy problems.

- Do not request personal data that the task does not need.
- Do not expose secrets, tokens, private fields, or sensitive data in URLs, visible logs, or error messages.
- Make permissions and consent meaningful, timely, and specific; avoid dark patterns and coercive consent flows.
- Explain why a permission or data field is required when the reason is not obvious.
- Show a clear distinction between a local demo and a production-connected form or service.
- Do not pretend that a frontend-only form sends, stores, authenticates, or securely processes data without a real backend implementation.
- If the requested feature has security implications, call out the missing backend/security requirements instead of implying that visual UI is enough.
- Make session, permission, upload, delete, payment, and irreversible-action states clear.

---

## 15. Website-building workflow

When asked to create a site, follow this sequence internally and deliver the useful result directly.

### Step 1 — Understand the brief

Identify the topic, audience, primary user goal, primary conversion/action, likely content, brand constraints, target devices, and existing implementation constraints. If some details are missing, make conservative assumptions rather than asking a long list of questions.

### Step 2 — Define the visual direction

Choose a coherent visual approach: restrained or expressive, editorial or application-like, light or dark, image-led or typography-led. Explain the decision briefly only when it helps the user; otherwise implement it consistently.

### Step 3 — Build the visual system

Define semantic color tokens, typography roles, spacing, content widths, border/radius/elevation rules, motion preferences, and the component states required for the page. Include a palette and visual references in the implementation or documentation when useful.

### Step 4 — Structure the information

Create the page hierarchy, navigation, section order, meaningful copy, primary and secondary actions, and responsive content order before adding decorative effects.

### Step 5 — Implement semantic, responsive UI

Build the layout with semantic HTML and modern CSS. Use components consistently. Add JavaScript only when needed for real behavior. Use appropriate CSS techniques, progressive enhancement, and project-native architecture.

### Step 6 — Integrate interaction and motion

Specify what changes on pointer-down, click/tap, keyboard focus, selection, loading, success, and failure. Motion must support cause/effect and preserve control. Do not animate merely to display technical sophistication.

### Step 7 — Run a design and behavior review

Check visual hierarchy, color/contrast, type, spacing, responsive behavior, focus, semantics, state handling, and performance. Where tools allow, inspect the produced output rather than relying only on code review.

### Step 8 — Deliver complete files and an honest status

List the created/changed files. Include complete contents or downloadable artifacts when supported. Explain necessary setup and identify any integrations, assets, or tests that remain unverified. Do not claim production readiness if key backend, security, browser, or accessibility checks have not been performed.

---

## 16. Quality assurance checklist

Use this checklist before considering a website implementation complete. Mark an item as not applicable only when its absence is justified by the requested scope.

### Visual system

- [ ] Color roles and states are tokenized and consistent.
- [ ] Required text/background and UI contrast pairs have been checked.
- [ ] Typography has a deliberate hierarchy and readable line lengths.
- [ ] Spacing, widths, radii, borders, shadows, and layer order are consistent.
- [ ] Icons and image treatments use a coherent visual language.
- [ ] The design has clear hierarchy without unnecessary decoration.

### Layout and responsive behavior

- [ ] The main layout works at narrow, medium, and wide widths.
- [ ] No unintended horizontal overflow occurs.
- [ ] Text, images, cards, forms, tables, and navigation reflow sensibly.
- [ ] Larger text and browser zoom do not hide content or functionality.
- [ ] Sticky/fixed elements do not obscure focus or content.
- [ ] Container queries and advanced CSS have appropriate fallbacks for the target environment.

### Components and interactions

- [ ] All controls have a clear purpose and accessible label.
- [ ] Button, link, form, menu, dialog, and navigation states are complete.
- [ ] Loading, empty, success, error, and no-permission states are handled where relevant.
- [ ] Keyboard interaction and focus movement are logical.
- [ ] Dragging interactions have suitable alternatives where required.
- [ ] Critical actions are clear; destructive actions are appropriately protected.
- [ ] Animation is interruptible where the interaction requires it.

### Accessibility

- [ ] Semantic HTML is used correctly.
- [ ] Keyboard focus is visible and not obscured.
- [ ] Contrast and target sizes meet the chosen baseline.
- [ ] Information is not conveyed by color alone.
- [ ] Reduced-motion preferences are respected.
- [ ] Form errors and asynchronous updates are accessible.
- [ ] Images, media, custom widgets, and icon-only controls have appropriate accessibility handling.
- [ ] Accessibility is not claimed as verified solely because automated checks passed.

### Performance and robustness

- [ ] Fonts, images, and scripts are not loaded unnecessarily.
- [ ] Animation targets suitable properties and listeners/observers are cleaned up.
- [ ] `will-change`, containment, and `content-visibility` are used only with a reason.
- [ ] Layout shifts and avoidable rendering work have been considered.
- [ ] Core content remains usable if optional enhancement fails.
- [ ] External dependencies and network requirements are documented.

### Delivery integrity

- [ ] The requested files are complete and correctly named.
- [ ] The code does not contain unexplained omissions or fake integrations.
- [ ] Existing project conventions and branding have been preserved.
- [ ] Tests actually performed are distinguished from tests not performed.

---

## 17. Motion and fluid interaction — original core principles retained

The following section preserves the original skill's detailed motion design guidance and integrates it into the broader website standard. Use it for gestures, drag/swipe interactions, sheets, drawers, carousels, directly manipulated objects, and other motion where physical continuity improves the interaction. It is not a requirement to use advanced motion on every website.

How Apple builds interfaces that stop feeling like a computer and start feeling like an extension of you. This knowledge comes from Apple's WWDC design talks — chiefly *Designing Fluid Interfaces* (WWDC 2018) — distilled and translated into the web platform (CSS, Pointer Events, `requestAnimationFrame`, spring libraries like Motion/Framer Motion).

The through-line: **an interface feels alive when motion starts from the current on-screen value, inherits the user's velocity, projects momentum forward, and can be grabbed and reversed at any instant.** Springs are the tool that makes all of this natural, because they are inherently interruptible and velocity-aware.

## The Core Idea

> "When we align the interface to the way we think and move, something magical happens — it stops feeling like a computer and starts feeling like a seamless extension of us."

An interface is fluid when it behaves like the physical world: things respond instantly, move continuously, carry momentum, resist at boundaries, and can be redirected mid-motion. Everything below is a way to get closer to that.

Apple frames design as serving four human needs: **safety/predictability, understanding, achievement, and joy.** Every rule here serves one of them.

## 1. Response — kill latency

The moment lag appears, the feeling of directness "falls off a cliff." Response is the foundation everything else is built on.

- **Respond on pointer-down, not on release.** Highlight a button the instant it's pressed. Waiting for `click`/touch-up to show feedback feels dead.
- **Be vigilant about every latency.** Audit debounces, artificial timers, transition waits, and the ~300ms tap delay. Anything on the input path that isn't essential is a regression.
- **Feedback must be continuous *during* the interaction, not just at the end.** For a drag, slider, or drawer, update the UI 1:1 with the pointer the whole way through — never animate only when the gesture completes.

```css
/* Define the transition on the base element so press and release both animate. */
.button {
  transition: transform 100ms ease-out;
}

.button:active {
  transform: scale(0.97);
}
```

## 2. Direct manipulation — 1:1 tracking

> "Touch and content should move together."

When the user drags something, it must stay glued to the finger — and respect the offset from *where they grabbed it*. Snapping to the element's center on grab breaks the illusion immediately.

- Use Pointer Events with `setPointerCapture` so tracking continues even when the pointer leaves the element's bounds.
- Track a short **velocity/position history** (last few `pointermove` events), not just the current point — you'll need velocity at release.

```js
el.addEventListener('pointerdown', (e) => {
  el.setPointerCapture(e.pointerId);
  const grabOffset = e.clientY - el.getBoundingClientRect().top; // respect where they grabbed
  // ...track position + timestamp history for velocity
});
```

## 3. Interruptibility — the single most important principle

> "The thought and the gesture happen in parallel."

Every animation must be interruptible and redirectable at any moment. A user must be able to grab a moving element mid-flight and reverse it without waiting for the animation to finish. A closing modal the user grabs again should follow the finger — not finish closing first, then reopen.

- **Never lock out input during a transition.**
- **Always animate from the *presentation* (current) value, never the target value.** On interrupt, read the element's live on-screen transform and start the new animation from there. Starting from the logical/target value causes a visible jump.
- For continuous direct manipulation, prefer an animation system that can be retargeted from the current presentation value and velocity. CSS transitions and keyframes are still appropriate for simple state changes, but are usually not sufficient by themselves for gesture-driven motion that must be grabbed and reversed mid-flight.
- **When a gesture reverses, blend velocity — don't hard-cut it.** Replacing one animation with another at a reversal creates a velocity discontinuity, a "brick wall." Spring libraries that carry velocity through a re-target avoid it. (This is what iOS's *additive animations* do natively; on the web, choose a spring library that re-targets from the current velocity.)
- **Decompose 2D motion into independent X and Y springs.** A single spring on a 2D distance desyncs when X and Y have different velocities.

## 4. Behavior over animation — use springs

> "Think of animation as a conversation between you and the object, not something prescribed by the interface."

A pre-scripted, fixed-duration animation can't respond to new input. A spring can — new input just changes the target, and the motion stays continuous. Reach for springs for anything a user can touch.

Apple deliberately replaced the physics triplet (mass/stiffness/damping) with two designer-friendly parameters. Think in these:

- **Damping ratio** — controls overshoot. `1.0` = critically damped, no bounce, smooth settle. `< 1.0` = overshoots and oscillates. Lower = bouncier.
- **Response** — how quickly the value reaches the target, in seconds. Lower = snappier. **This is not "duration"** — a spring has no fixed duration; its settle time emerges from the parameters.

**Defaults:**
- Start most UI at **damping `1.0`** (critically damped) — graceful and non-distracting.
- Add bounce (**damping ~`0.8`**) **only when the gesture itself carried momentum** (a flick, a throw, a drag release). Overshoot on a menu that just faded in feels wrong; overshoot on a card you flicked feels right.

**Concrete values Apple ships:**

| Interaction | Damping | Response |
| --- | --- | --- |
| Move / reposition (e.g. PiP) | `1.0` | `0.4` |
| Rotation | `0.8` | `0.4` |
| Drawer / sheet | `0.8` | `0.3` |

**Web mapping (Motion / Framer Motion):** spring APIs differ. Parameters such as `bounce`, `duration`, `damping`, and `stiffness` are not a universal, exact translation of Apple's damping/response pair. Verify the behavior against the library's current documentation and tune by interaction. A safe house style is a critically damped or non-bouncy motion by default; reserve overshoot for momentum-driven interactions where it adds useful feedback.

```js
import { animate } from 'motion';

// Critically damped default (no overshoot)
animate(el, { y: 0 }, { type: 'spring', bounce: 0, duration: 0.4 });

// Momentum interaction — a little bounce, only because a flick preceded it
animate(el, { y: target }, { type: 'spring', bounce: 0.2, duration: 0.4 });
```

## 5. Velocity handoff — the seam between drag and animation

When a gesture ends, the animation must **continue at the finger's exact velocity**, so there's no visible seam between dragging and animating. This is the detail that most separates "fluid" from "fine."

Pass the pointer's release velocity as the spring's initial velocity. Some spring APIs want **relative** velocity — normalize it by the remaining distance to the target:

```
relativeVelocity = gestureVelocity / (targetValue − currentValue)
```

Example: element at `y=50`, target `y=150` (100px to go), finger moving 50px/s → initial spring velocity = `50 / 100 = 0.5`. Framer Motion / Motion take absolute px/s velocity directly (`velocity` option), so you usually hand it the raw value.

## 6. Momentum projection — animate to where the gesture is *going*

> "Take a small input and make a big output."

Don't snap to the nearest boundary from the *release point*. Use velocity to **project the resting position** — exactly like scroll deceleration — then snap to the target nearest that projected point. This is what makes a flick feel like it throws the element.

Apple's exact projection function (from the *Designing Fluid Interfaces* sample code):

```js
// decelerationRate ≈ 0.998 for normal scroll feel; 0.99 for snappier
function project(initialVelocity /* px/s */, decelerationRate = 0.998) {
  return (initialVelocity / 1000) * decelerationRate / (1 - decelerationRate);
}

const projectedEndpoint = currentPosition + project(releaseVelocity);
const target = nearestSnapPoint(projectedEndpoint);   // choose target from the projection
animateSpringTo(target, { velocity: releaseVelocity }); // then hand off velocity (§5)
```

Note: the physics-textbook `v²/(2·decel)` is *not* what Apple ships — use the exponential-decay form above. This is the standard behavior in good bottom-sheets and carousels (Vaul, Embla).

## 7. Spatial consistency — symmetric paths, anchored origins

> "If something disappears one way, we expect it to emerge from where it came."

- **Enter and exit along the same path.** A panel that slides in from the right must dismiss to the right. In-from-right / out-the-bottom feels disconnected and confusing.
- **Anchor interactions to their source.** A menu, popover, or sheet should originate from the element that triggered it — set `transform-origin` to the trigger, so the spatial relationship between button and content is obvious. (This is the same origin-awareness point as popovers scaling from their trigger, not their center.)
- **Mirror the easing on reversible transitions** so the outbound path matches the return path (use inverse cubic-bézier control points for the two directions).

## 8. Hint in the direction of the gesture

Humans predict a final state from a trajectory. Intermediate motion should telegraph where things are going — Control Center modules "grow up and out toward your finger." Make the in-between frames point at the outcome, not just interpolate blindly to it.

## 9. Rubber-banding — soft boundaries

At an edge, resist progressively instead of stopping hard. A hard stop reads as "frozen"; continuous resistance reads as "responsive, but there's nothing more here." Apply damping that increases the further past the boundary the user drags.

```js
// The further past the bound, the less the element follows — real things slow before they stop
function rubberband(overshoot, dimension, constant = 0.55) {
  return (overshoot * dimension * constant) / (dimension + constant * Math.abs(overshoot));
}
```

## 10. Gesture design details (the "feel" checklist)

- **Tap:** highlight on touch-*down* (instant), commit on touch-*up*. Add ~10px of hysteresis/hit padding around the target, and allow cancel-by-dragging-away and back.
- **Drag/swipe:** require a small movement threshold (hysteresis, ~10px) before committing to a direction, then track 1:1.
- **Detect all plausible gestures in parallel from the first move**, then confidently cancel the losers once intent is clear. Avoid recognizers that only report a *final* state (`swipeleft`-type events) — they throw away the continuous tracking you need for feedback.
- **Minimize disambiguation delays.** Double-tap detection unavoidably delays single taps; only pay that cost where double-tap truly exists.

## 11. Frame-level smoothness

Smoothness is about *what's in the frames*, not just the frame rate.

- Keep the per-frame positional change below the perception threshold to avoid strobing.
- For very fast motion, a subtle **motion blur / stretch** encodes speed and reads better than a hard sharp streak.
- `requestAnimationFrame` is the web's display-synced clock (Apple uses `CADisplayLink`). Animate only compositor-friendly properties — `transform` and `opacity` — and hint with `will-change` where motion is imminent.

## 12. Materials & depth — translucency conveys hierarchy

Apple uses translucent materials as a floating functional layer that brings structure without stealing focus. On the web, approximate with `backdrop-filter`.

- Consider translucent nav/toolbars/sheets (`backdrop-filter: blur()` + a semi-transparent background) when content continuity and a floating layer genuinely help. Opaque surfaces are often better for dense content, weak contrast conditions, and predictable accessibility.
- **Material weight can encode hierarchy:** darker/heavier materials may separate structural regions; lighter materials may draw attention to interactive elements. Avoid stacking translucent surfaces when contrast and separation deteriorate.
- **Bigger surfaces should read as thicker:** stronger blur + a deeper shadow than small chips. Consider context-aware shadow — heavier over busy/text content for separation, lighter over plain backgrounds.
- **Dim to focus, separate to keep flow.** A modal task pairs the surface with a dimming scrim and pushes the background back/down. A parallel, non-blocking panel uses translucency and offset *without* a scrim so the flow isn't broken. For stacked sheets, progressively dim and push back each parent layer.
- **Vibrancy keeps text legible over changing backgrounds.** Over blurred/translucent surfaces, don't use flat gray text — use higher-contrast, slightly heavier weight, and a small letter-spacing bump. Put color on a solid layer, not the translucent foreground.
- **Scroll edge effects, not hard dividers.** Instead of a 1px border under a sticky header, fade a small blur/gradient mask where content meets floating chrome — only where floating UI actually overlaps content.
- **Materialize, don't just fade.** For glass/blur surfaces, animate blur radius and scale together on enter/exit, so the surface reads as a real material arriving rather than a plain opacity fade.

```css
.toolbar {
  background: rgba(255, 255, 255, 0.6);
  backdrop-filter: blur(20px) saturate(180%);
  border-top: 1px solid rgba(255, 255, 255, 0.4); /* bright top edge = light catching the material */
}
```

## 13. Multimodal feedback — motion + sound + haptics

Three rules for combining senses (from *Designing Audio-Haptic Experiences*):

1. **Causality** — it must be obvious what caused the feedback. Trigger it on the actual causal event (the toggle flipping, the item snapping home), and match its character to the action's physicality.
2. **Harmony** — the visual, the sound, and the haptic must fire on the **same frame**. Latency between them destroys the illusion. Don't let a CSS transition lag the audio/haptic (Vibration API).
3. **Utility** — add feedback only where it earns its place. Reserve haptics/sound for meaningful moments (success, error, commit, snap). Over-feedback trains users to ignore all of it.

## 14. Reduced motion & accessibility

Reduced motion doesn't mean *no* feedback — it means a gentler, non-vestibular equivalent. Respond to three independent signals and bake them into your components:

- **`prefers-reduced-motion: reduce`** — replace slides/springs/parallax with short opacity **cross-fades or static transitions**. Drop elastic/overshoot. Keep opacity/color changes that aid comprehension.
- **`prefers-reduced-transparency: reduce`** — make translucent surfaces frostier/solid: raise background opacity, drop the blur.
- **`prefers-contrast: more`** — near-solid backgrounds with a defined, contrasting border.

Also: avoid full-viewport moving backgrounds, slow looping oscillations (near 0.2 Hz / one cycle per 5s), and abrupt brightness jumps (ease dark↔light theme changes). Make large moving objects semi-transparent while they travel, and fade big surfaces out during a large reposition and back in once settled.

```css
@media (prefers-reduced-motion: reduce) {
  .sheet { transition: opacity 200ms ease; transform: none !important; }
}
@media (prefers-reduced-transparency: reduce) {
  .toolbar { background: white; backdrop-filter: none; }
}
```

## 15. Typography — optical sizing, tracking, leading

Apple designs type to change shape with size; the same discipline applies on the web. (From *The Details of UI Typography*, WWDC 2020.)

- **Tracking (letter-spacing) is size-specific — never one value for all sizes.** Large display text wants *negative* tracking (letters read too far apart as they grow); small text wants slightly *positive* tracking for legibility. A fixed `letter-spacing` is wrong somewhere. Tighten headings, leave body near `0`.
- **Leading (line-height) tracks size inversely.** Tight on large headings, looser on body copy. Increase it for scripts with tall ascenders/descenders; tighten it for dense, information-heavy UI.
- **Build hierarchy from weight + size + leading as a set,** not size alone. Emphasize with weight — it adds presence without taking more space.
- **Respect the user's text-size setting** (Dynamic Type). Scale layout *with* the text — spacing in `rem`/`em`, not fixed px — so a larger font doesn't break the layout.
- **Default to the platform's system font** before a custom face; it already ships optical sizing, tracking tables, and legibility tuning. Override only with a reason.

```css
:root { font: 100%/1.5 system-ui, sans-serif; } /* body: system font, comfortable leading */

.display {
  font-size: clamp(2rem, 5vw, 4rem);
  line-height: 1.05;        /* tight leading for large text */
  letter-spacing: -0.02em;  /* negative tracking as it grows */
  font-optical-sizing: auto;
}
```

## 16. Design foundations — the eight principles

The motion and craft above serve Apple's eight design principles (*Principles of Great Design*, WWDC 2026). Use these as the names you reason with:

1. **Purpose.** Make with intention; decide what *not* to build. Every feature asks for the user's time, attention, and trust — spend that budget only where it pays off.
2. **Agency.** Keep people in control: offer choices, don't force a single path. Back it with forgiveness — easy undo for slips, a confirmation dialog only for genuinely destructive, irreversible actions (use sparingly; overusing it trains people to click through).
3. **Responsibility.** Act in the user's interest. Privacy: ask at the right moment, only for what's needed, transparently. Safety: anticipate misuse and harm — especially with AI (an allergy-aware recipe app must not suggest a harmful ingredient). Add previews, confirmations, disclaimers; cut a feature whose risk outweighs its value.
4. **Familiarity.** Build on what people already know. Use metaphors that are neither too literal nor too abstract (a trash can means delete), and honor their physics. Be consistent: things that look the same must behave the same and live in the same place (close is always top-left on macOS) so people can predict what happens next. Only break a familiar pattern if you can prove it's better — then test it, don't assume.
5. **Flexibility.** Design for different contexts, devices, and the full range of abilities. Adapt to the platform (iPhone = quick touch; desktop = deep workflows with precise pointer control) and to the situation. Design inclusively (age, language, expertise, accessibility). When no single layout fits everyone, let people personalize — rearrange controls, hide what they don't use.
6. **Simplicity — not minimalism.** Strip the unnecessary so the core purpose shines; burying everything in one place looks minimal but isn't simple. Be concise (plain language, no jargon, fewer steps) and clear (use hierarchy — order, spacing, contrast — so the most important thing is the most obvious). Every element earns its place; sometimes *adding* context simplifies (a video scrubber that shows time remaining). Show the common path first, advanced options one level deeper.
7. **Craft.** Uncompromising attention to detail builds trust. Beautiful typography, colors that adapt to light/dark, clear iconography, and responsive animations that give immediate, natural feedback. Nothing is random — every spacing, timing, and alignment value is a deliberate choice you can defend. Jittery scroll, misaligned icons, and layouts that break on rotation read as carelessness. Craft needs iteration and longevity — keep evolving the design as features and hardware change.
8. **Delight.** The result of getting the other seven right, not confetti tacked on top. Decide the emotion you want people to feel (calm, confident, excited) and reinforce it in every decision.

Tactical rules that serve these:

- **Feedback comes in four kinds:** status, completion, warning, error. Confirm meaningful actions, expose ongoing status, warn before problems, validate inline (not on submit).
- **Wayfinding.** Every screen should answer: Where am I? Where can I go? What's there? How do I get out? Never trap the user.
- **Grouping & mapping.** Proximity implies relationship; place a control near what it affects and arrange controls to mirror what they change. If you need a label to explain a control, the mapping is weak.
- **Direct, specific labels beat safe generic ones.** Name nav items for their contents ("Progress", "Library"), not vague umbrellas ("Home"). Specificity creates predictability.

## 17. Process

- **Prototype interactively — an interactive demo is worth "a million static designs."** You discover the interface by building and playing with it; a working prototype also sets a concrete bar that prevents a mediocre final implementation.
- **Design interaction and visuals together.** "You shouldn't be able to tell where one ends and the other begins." Motion is not a layer added after the pixels.
- **Test with real people in real context**, and review motion with fresh eyes — play it in slow motion / frame-by-frame to catch what's invisible at full speed.

## Quick Reference

| Need | Technique | Concrete value |
| --- | --- | --- |
| Default UI spring | Critically damped, no overshoot | `damping 1.0`, `response 0.3–0.4` |
| Momentum / flick spring | Under-damped, slight bounce | `damping ~0.8`, `response 0.3–0.4` |
| Gesture → spring velocity | Hand off release velocity | `gestureVelocity / (target − current)` if normalized |
| Flick landing point | Project momentum | `current + (v/1000)·d/(1−d)`, `d ≈ 0.998` |
| Interrupt cleanly | Start from presentation (live) value | read the on-screen transform |
| Avoid reversal "brick wall" | Carry velocity through re-target | spring that blends velocity |
| Reversible transition | Mirror the easing curve | inverse cubic-bézier |
| Decide reverse vs. commit | Use velocity **sign**, not position | at release |
| 1:1 drag | Pointer Events + capture | respect the grab offset |
| Feedback | On pointer-down, continuous | never only at the end |
| Boundary | Rubber-band, don't hard-stop | progressive resistance |
| Translucent chrome | `backdrop-filter` layer | content scrolls under |
| Type tracking | Size-specific, never fixed | tighten large text (`-0.02em`), body near `0` |
| Reduced motion | Cross-fade, not slide/spring | `@media (prefers-reduced-motion)` |

---

## 18. Implementation reference: CSS patterns

These patterns are examples, not universal requirements. Adapt colors, sizing, breakpoints, and motion to the actual project and verify supported browsers.

### 18.1 Focus, reduced motion, and reduced transparency

```css
:root {
  --focus-ring: #245fdb;
  --focus-width: 3px;
  --focus-offset: 3px;
}

:where(a, button, input, select, textarea, [tabindex]):focus-visible {
  outline: var(--focus-width) solid var(--focus-ring);
  outline-offset: var(--focus-offset);
}

@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    scroll-behavior: auto !important;
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}

@media (prefers-reduced-transparency: reduce) {
  .translucent-surface {
    background: var(--surface-raised, #fff);
    -webkit-backdrop-filter: none;
    backdrop-filter: none;
  }
}
```

The broad reduced-motion rule is a fallback pattern and may need refinement in a project with essential animations. Preserve meaningful state feedback and avoid disabling essential transitions indiscriminately.

### 18.2 Container query example

```css
.card-list-item {
  container: card / inline-size;
}

.card-content {
  display: grid;
  grid-template-columns: 1fr;
  gap: var(--space-4, 1rem);
}

@container card (min-width: 34rem) {
  .card-content {
    grid-template-columns: 8rem minmax(0, 1fr);
    align-items: start;
  }
}
```

Provide a sensible base layout for browsers or contexts where container queries are unavailable if those environments are in scope.

### 18.3 Fluid type example

```css
.page-title {
  font-size: clamp(2.25rem, 1.5rem + 3.2vw, 4.75rem);
  line-height: 1.02;
  letter-spacing: -0.035em;
  text-wrap: balance;
  max-width: 16ch;
}

.article-copy {
  max-width: 70ch;
  font-size: 1rem;
  line-height: 1.65;
}

@supports (text-wrap: pretty) {
  .article-copy {
    text-wrap: pretty;
  }
}
```

Values are illustrative. Test font metrics, translation, content length, browser zoom, and the actual chosen typeface before adopting them.

### 18.4 Progressive enhancement for scroll-driven motion

```css
.reading-progress {
  transform: scaleX(0);
  transform-origin: left center;
}

@supports (animation-timeline: scroll()) {
  .reading-progress {
    animation: reading-progress linear both;
    animation-timeline: scroll(root block);
  }

  @keyframes reading-progress {
    to { transform: scaleX(1); }
  }
}

@media (prefers-reduced-motion: reduce) {
  .reading-progress {
    animation: none;
  }
}
```

When the feature is unsupported, the decorative progress animation may be absent; essential reading or navigation must still work.

---

## 19. Deliverable rules for the AI using this skill

When the user asks for a website or UI, do not respond only with general design suggestions. Produce the requested artifact at the requested level of completeness.

If the request is a code implementation:

- state the files created or modified;
- keep each file complete and name it before presenting its contents when using chat-based code delivery;
- when a downloadable artifact can be generated, provide a valid link to the actual created file;
- include working semantic markup, tokens, responsive layout, relevant states, and interaction behavior;
- do not add backend-dependent functionality unless the backend exists or is clearly implemented as part of the task;
- clearly identify setup steps and unverified assumptions;
- do not add unrelated features or rewrite unrelated parts of an existing project.

If the request is a design review:

- distinguish confirmed defects, usability risks, accessibility risks, and subjective design preferences;
- prioritize findings by severity and user impact;
- provide precise fixes and, when useful, corrected code;
- do not invent findings about files or browser behavior that have not been inspected.

If the user only asks for a visual concept or prototype, match that requested deliverable instead of forcing a full production stack. If the user requests an image, produce an image where appropriate; otherwise, a website request defaults to a functional web implementation, not a static illustration.

---

## 20. Reference sources and standards

Consult current authoritative documentation when selecting browser features, accessibility criteria, or framework APIs. Browser support and standards can change; verify compatibility for the project's actual target environment.

- [W3C — Web Content Accessibility Guidelines (WCAG) 2.2](https://www.w3.org/TR/WCAG22/)
- [W3C WAI — Understanding Target Size (Minimum)](https://www.w3.org/WAI/WCAG22/Understanding/target-size-minimum)
- [Apple — Human Interface Guidelines](https://developer.apple.com/design/human-interface-guidelines/)
- [MDN — CSS Container Queries](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Containment/Container_queries)
- [MDN — CSS Subgrid](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Grid_layout/Subgrid)
- [MDN — CSS Scroll-Driven Animations](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Scroll-driven_animations)
- [MDN — `text-wrap`](https://developer.mozilla.org/en-US/docs/Web/CSS/text-wrap)
- [MDN — `will-change`](https://developer.mozilla.org/en-US/docs/Web/CSS/will-change)
- [MDN — `content-visibility`](https://developer.mozilla.org/en-US/docs/Web/CSS/content-visibility)
- [U.S. Web Design System — Design Tokens](https://designsystem.digital.gov/design-tokens/)

Use references to verify technical facts; do not copy examples blindly. Apply the least complex technique that satisfies the design, accessibility, performance, and maintenance requirements.
