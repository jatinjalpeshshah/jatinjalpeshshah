# Vanguard OS Design System

> Master design specification for the Jatin Jalpesh Shah GitHub Profile environment.

---

## 1. DESIGN PHILOSOPHY

The overarching vision of the Vanguard OS design language is to communicate **Enterprise Cybersecurity, AI Security, Detection Engineering, and Threat Intelligence**. 

When a user visits the profile, it should not look like a generic developer portfolio, a gaming dashboard, or a cyberpunk hacker movie. It must feel like an authentic, authenticated session within a modern **Security Operations Center (SOC)**.

**Visual Inspiration:**
*   Microsoft Sentinel
*   CrowdStrike Falcon
*   Elastic Security
*   Palo Alto Cortex
*   Splunk Enterprise Security
*   SentinelOne

**Strict Anti-Patterns:**
*   Avoid RGB gradients and neon overload.
*   Avoid gaming aesthetics.
*   Avoid overly futuristic, illegible typography.
*   Avoid cluttered, unaligned widgets.
*   Avoid "hacker movie" tropes.

---

## 2. BRAND IDENTITY

Every visual asset must inherit the following core identity stack:

*   **Primary Brand:** `VANGUARD OS`
*   **Supporting Brand:** `CyberSentinel AI`
*   **Personal Identity:** `Jatin Jalpesh Shah`
*   **Designations:** `Cybersecurity Engineer` | `Security Researcher`

These elements serve as the visual signature on all SVG assets, typically placed in footers or breadcrumb headers to ground the component in a unified product ecosystem.

---

## 3. COLOR SYSTEM

The color palette is disciplined and strictly enforced. Do not invent random colors.

| Role | Color Name | HEX | RGB | Purpose & Usage |
| :--- | :--- | :--- | :--- | :--- |
| **Background** | Deep Charcoal | `#080C11` | `8, 12, 17` | Base layer for all SVGs, matches GitHub Dark. |
| **Panel Base** | Obsidian | `#0A0F19` | `10, 15, 25` | Solid background for primary UI panels. |
| **Primary/Accent** | Electric Blue | `#38BDF8` | `56, 189, 248` | Interfaces, active links, borders, and brand accents. |
| **Success/Online** | Cyber Green | `#10B981` | `16, 185, 129` | Online status, stable health, active monitoring. |
| **Warning/Alert** | Amber | `#F59E0B` | `245, 158, 11` | Research mode, alerts, non-critical warnings. |
| **Danger** | Crimson | `#EF4444` | `239, 68, 68` | Critical alerts, malware tags, offline status. |
| **Text Primary** | Bright White | `#F8FAFC` | `248, 250, 252` | Main titles, metric values, operator names. |
| **Text Muted** | Slate | `#94A3B8` | `148, 163, 184` | Subtitles, labels, secondary metrics, mission text. |
| **Text Dark** | Slate Dark | `#64748B` | `100, 116, 139` | Subtle background text, breadcrumbs, minor labels. |
| **Borders** | Slate Line | `#1E293B` | `30, 41, 59` | Standard borders around solid and glass panels. |
| **Hover/Glow** | Blue Alpha | `rgba(59, 130, 246, 0.15)` | `59, 130, 246` | Faint glows and interactive hover states. |

---

## 4. TYPOGRAPHY

SVGs must use standard system fonts to prevent stripping by GitHub's Camo proxy.

*   **Primary Font Family (Sans-Serif):** `-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif`
*   **Monospace Font Family (Telemetry/Metrics):** `ui-monospace, SFMono-Regular, Consolas, "Liberation Mono", Menlo, monospace`

**Typography Hierarchy:**
*   **Hero Titles:** 34px - 38px, Weight: 800, Spacing: 1px
*   **Metric Values:** 16px - 24px, Weight: 700
*   **Subtitles/Roles:** 14px, Weight: 600, Spacing: 2px, Color: `#94A3B8`
*   **Body/Mission:** 13px - 14px, Weight: 400, Line Height: 1.6
*   **Telemetry Labels:** 11px, Weight: 600, Spacing: 1px, Uppercase
*   **Tech Chips:** 11px, Weight: 600

*Recommendation:* Do not use `<foreignObject>` for critical text; rely on `<text>` and `<tspan>` for cross-browser SVG rendering.

---

## 5. GRID SYSTEM

The UI relies on strict alignment to maintain an enterprise feel.

*   **ViewBox:** Use panoramic responsive ratios (e.g., `0 0 1000 480` for Hero, `0 0 800 400` for Cards). Always set `<svg width="100%" height="100%">`.
*   **Responsive Behavior:** SVGs naturally scale proportionally. Maintain a safe margin of at least `s-4` (24px) around critical text elements to prevent clipping.

---

## 6. COMPONENT LIBRARY

Every component must follow its designated structural archetype.

*   **Hero Banner:** Identity left, Telemetry right, Stack bottom.
*   **Project Card:** (See Section 21 for comprehensive Blueprint).
*   **Metric Card:** Glass panel `rgba(255,255,255,0.03)`, 3px colored left-border accent, uppercase label, bold numeric value.
*   **Technology Badge:** Dark slate background `rgba(15,23,42,0.6)`, thin blue border, 4px radius, centered text.
*   **Dashboard Widget:** Solid obsidian background, defined header bar, top-right status blinker.
*   **Repository CTA:** Prominent right-aligned or bottom-aligned action area, typically using Electric Blue `#38BDF8` borders.

---

## 7. ICONOGRAPHY

Icons should be minimal and geometric.
*   **Style:** Line-art preferred. 1.5px to 2px stroke width.
*   **Allowed Families:** Lucide, Feather, Heroicons (SVG paths).
*   **Usage:** Only use icons when they actively aid navigation or status comprehension (e.g., `✓`, `●`, radar blips, server stacks). Avoid illustrative clipart.
*   **Security Icons:** Use standardized icons for nodes (circles), shields, and packet flows (dashed lines).

---

## 8. PANEL SYSTEM

The Vanguard OS aesthetic relies on layered depth.

*   **Solid Panels (`panel-primary`):** Base layer for dashboards. `#0A0F19`, `stroke="#1E293B"`.
*   **Glass Panels (`panel-glass`):** Used for overlays (metrics). `fill="rgba(255,255,255,0.03)"`, `stroke="rgba(59,130,246,0.15)"`.
*   **Corner Accents:** 2px stroke paths on the outer corners of major panels (Cyberpunk/HUD style, but kept minimal).
*   **Drop Shadows:** Use tokenized drop shadows (`shadow-medium`) to create floating depth. No excessive glow.
*   **Micro Shadows:** 1px offset for inner inset depths where necessary.

---

## 9. ANIMATION SYSTEM

Motion should communicate telemetry and live data, not distraction.

| Animation | Class | Duration | Description | Usage |
| :--- | :--- | :--- | :--- | :--- |
| **Pulse** | `.anim-pulse` | `a-normal` | Soft opacity transition (`1` to `0.4`). | Live monitoring dots, active statuses. |
| **Blink** | `.anim-blink` | `a-fast` | Step-end opacity (`1` to `0`). | Terminal cursors, LIVE indicators. |
| **Radar** | `.anim-radar` | `a-slow` | Infinite 360-degree rotation. | Large background sweeps only. |
| **Grid Drift** | `.anim-grid` | `a-background` | Linear X/Y translation offset. | Background depth. Barely perceptible. |
| **Scan Line** | `.anim-scan` | `a-slow` | Vertical linear translation. | Global SVG overlay for screen effect. |

*Rule:* Animations must remain subtle. Avoid fast flashing. Do not use JS or GIFs.

---

## 10. SVG STANDARDS

*   **Folder Structure:** `/assets/svg/`
*   **Naming:** kebab-case (e.g., `hero-banner.svg`, `phishguard-card.svg`)
*   **Optimization:** Group related elements in `<g>`. Use `<defs>` for gradients, filters, and patterns.
*   **Accessibility:** Use `<title>` and `<desc>` inside the SVG for screen readers.
*   **CSS Constraints:** Inject styles via inline `<style>` block. Do not rely on external stylesheets.
*   **File Size Target:** Under 20KB for standard components.

---

## 11. PROJECT CARD SPECIFICATION

*Superseded by Section 21: PROJECT TEMPLATE BLUEPRINT.*

---

## 12. HERO BANNER SPECIFICATION

*   **Status:** Finalized (`/assets/svg/hero-banner.svg`).
*   **Dimensions:** 1000x480.
*   **Zones:** Left (Identity/Metrics), Right (Telemetry Dashboard), Bottom (Categorized Tech Stack), Background (Dual-layer grid, Radar).
*   **Future Extensibility:** Metrics can be updated by altering text nodes.

---

## 13. FUTURE COMPONENT ROADMAP

| Priority | Component | Filename | Dependencies | Status |
| :--- | :--- | :--- | :--- | :--- |
| P0 | Hero Banner | `hero-banner.svg` | None | **✓ DONE** |
| P1 | CyberSentinel Card | `cybersentinel-card.svg` | Vanguard Design System | ⬜ Pending |
| P1 | PhishGuard Card | `phishguard-card.svg` | Vanguard Design System | ⬜ Pending |
| P2 | Portfolio Card | `portfolio-card.svg` | Vanguard Design System | ⬜ Pending |
| P2 | Get2Gather Card | `get2gather-card.svg` | Vanguard Design System | ⬜ Pending |
| P3 | Architecture Diag. | `architecture-diagram.svg` | Project architectures | ⬜ Pending |
| P3 | Skills Matrix | `skills-matrix.svg` | Vanguard Design System | ⬜ Pending |
| P4 | Timeline | `timeline.svg` | Vanguard Design System | ⬜ Pending |

---

## 14. QUALITY CHECKLIST

*Superseded by Section 23: DESIGN REVIEW CHECKLIST.*

---

## 15. DESIGN TOKENS

To ensure absolute consistency, every SVG must leverage the following conceptual design tokens. Hardcoded pixel values outside this system are prohibited.

**Spacing Tokens**
*   `s-1` = 4px
*   `s-2` = 8px
*   `s-3` = 16px
*   `s-4` = 24px
*   `s-5` = 32px
*   `s-6` = 48px

**Radius Tokens**
*   `r-xs` = 2px
*   `r-sm` = 4px
*   `r-md` = 8px
*   `r-lg` = 16px
*   `r-xl` = 24px

**Border Tokens**
*   `border-primary` = `#1E293B` (Slate Line)
*   `border-secondary` = `rgba(59, 130, 246, 0.15)` (Blue Alpha)
*   `border-success` = `#10B981` (Cyber Green)
*   `border-warning` = `#F59E0B` (Amber)

**Animation Tokens**
*   `a-fast` = 0.8s - 1.2s
*   `a-normal` = 2s - 3s
*   `a-slow` = 6s - 10s
*   `a-background` = 15s - 20s

**Opacity & Shadow Tokens**
*   `shadow-light` = `dx="0" dy="2" stdDeviation="4" flood-opacity="0.2"`
*   `shadow-medium` = `dx="0" dy="4" stdDeviation="6" flood-opacity="0.4"`
*   `shadow-heavy` = `dx="0" dy="8" stdDeviation="12" flood-opacity="0.6"`

---

## 16. INFORMATION HIERARCHY

The user's eye must seamlessly navigate every component following a strict Z-pattern or F-pattern hierarchy. 

*   **Level 1: Identity & Authentication** (Top Left) - E.g., "SECURITY OPERATIONS PLATFORM", Project Name.
*   **Level 2: Mission & Tagline** (Directly Below Level 1) - The "Why" of the component.
*   **Level 3: Primary Metrics / Telemetry** (Right Panel or Grid) - The empirical data proving the tagline.
*   **Level 4: Technology & Architecture** (Bottom or Center) - The "How". Categorized tech stacks, architecture graphs.
*   **Level 5: Supporting Information & CTA** (Footer) - System uptime, Vanguard OS signature, Repository Links.

---

## 17. DATA VISUALIZATION SYSTEM

Cybersecurity components frequently require data visualization. 

*   **Threat Metrics:** Use solid numbers against `panel-glass`. Do not use pie charts.
*   **Timeline Nodes:** Use `border-primary` lines connecting `r-xl` circular nodes. Active nodes fill with `#38BDF8`.
*   **Network Graphs:** Use `s-1` thickness dashed lines linking hexagonal nodes.
*   **Flow Diagrams / Detection Pipelines:** Horizontal left-to-right progression. Use chevron (`>`) connectors.
*   **Architecture Diagrams:** Group by isolated `panel-primary` containers representing servers or modules. 
*   **Progress Bars:** 4px height (`r-sm`). Background `#1E293B`, Foreground `#38BDF8` or `#10B981`.
*   **Severity Indicators:** Dot markers. `#EF4444` (Critical), `#F59E0B` (Warning), `#10B981` (Stable).

---

## 18. COMPONENT STATES

Reusable components implicitly represent state.

*   **Default:** `panel-glass` with `border-primary`.
*   **Hover/Active:** `border-secondary` (Blue Alpha) with `shadow-medium`.
*   **Loading/Processing:** Utilizes `a-normal` pulse animation on the border or a sweeping `scan` overlay.
*   **Online/Stable:** `border-success` accents, `.anim-blink` green dot.
*   **Warning/Critical:** `border-warning` or crimson accents. Alert text overrides muted slate.
*   **Disabled/Offline:** 50% global opacity on the component `<g>`, monochrome conversion (no accent colors).

---

## 19. ACCESSIBILITY

*   **Contrast:** All text (especially `#94A3B8` Slate) against `#080C11` background must pass WCAG AA minimum contrast.
*   **Readable Fonts:** Minimum font size `10px` for metadata, `13px` for body.
*   **Reduced Motion:** Animations must be slow and non-strobe to prevent motion sickness. 
*   **Color-Independence:** Do not rely solely on color for status. E.g., A green dot must also have the word "ONLINE" or "STABLE".
*   **Screen Readers:** The root `<svg>` must contain `<title>` and `<desc>`. Logical reading order must be maintained in the DOM (`<g>` elements ordered top-to-bottom, left-to-right).

---

## 20. PERFORMANCE STANDARDS

Enterprise SVGs must load instantaneously without layout shift.

*   **Max File Size:** `25KB` absolute limit per component.
*   **Max Animation Count:** Maximum of 4 distinct keyframes per file to prevent GPU thrashing.
*   **SVG Structure:** Use `<defs>` aggressively. If a grid, hexagon, or panel is used multiple times, define it once and `<use>` it.
*   **Avoid Duplicated Paths:** Do not inline the same complex icon multiple times.
*   **ID Naming:** IDs in `<defs>` must be unique per file (e.g., `id="hero-glow"`, `id="card-glow"`) to prevent cross-SVG conflicts when rendered on the same GitHub page.

---

## 21. PROJECT TEMPLATE BLUEPRINT

Every project card must share the exact same structural blueprint. Only colors, imagery, and text should differ.

1.  **Header:** Project Name (Level 1), Status Indicator (e.g., STABLE), Semantic Versioning.
2.  **Tagline:** One-sentence enterprise summary (Level 2).
3.  **Preview Area / Architecture Overview:** Central visual representation of the project interface, network graph, or backend flow. 
4.  **Feature Highlights:** 2x2 grid of key capabilities utilizing `panel-glass`.
5.  **Technology Stack:** Categorized chips (Security, AI, Frameworks) using tokenized `chip-bg`.
6.  **Metrics:** Key performance indicators (e.g., Uptime, Accuracy, Rules Loaded).
7.  **Repository CTA:** Actionable button styling linking to the repository, right-aligned.
8.  **Footer Branding:** `VANGUARD OS | [PROJECT_NAME]` signature.

---

## 22. FUTURE EXPANSION GUIDELINES

The design system is built to scale. Future assets must naturally fit into the Vanguard OS ecosystem:

*   **Research/Publication Cards:** Should prioritize text legibility and abstract network visualizations over UI previews.
*   **Timeline Components:** Vertical or horizontal. Must use tokenized nodes and dashed progression lines.
*   **Achievement Panels:** Certification or badge showcases should use `panel-primary` pedestals with subtle `shadow-light`.
*   **Dashboard Modules:** Small square or vertical widgets intended to be tiled together in a CSS grid or markdown table.

---

## 23. DESIGN REVIEW CHECKLIST

Every future SVG must pass this mandatory approval gate before being committed to production:

*   [ ] **Visual Consistency:** Matches Vanguard OS aesthetic. No neon, no gaming tropes.
*   [ ] **Typography:** Uses system font stacks. Correct hierarchy applied.
*   [ ] **Design Tokens:** Strict adherence to `s-*`, `r-*`, and predefined colors.
*   [ ] **Alignment:** Perfectly aligned on the internal grid.
*   [ ] **Animation:** Subtle, non-distracting, using approved tokens (`a-fast`, `a-normal`, etc.).
*   [ ] **Accessibility:** Passes contrast checks, includes `<title>` and `<desc>`.
*   [ ] **Performance:** `<defs>` utilized, unique IDs, file size < 25KB.
*   [ ] **GitHub Compatibility:** Tested in both Dark and Light mode contexts. No `<foreignObject>` bugs.
*   [ ] **Branding:** Includes Vanguard OS footer signature.
*   [ ] **Code Quality:** Clean indentation, logical `<g>` groupings.

---
*Vanguard OS Specification v1.1. Authored for Jatin Jalpesh Shah.*
