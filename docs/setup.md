# Modus Web Components — Setup

A minimal one-time boiler-plate that every HTML page using Modus Web Components needs.

---

## 1. CSS

```html
<!-- Modus component tokens & styles -->
<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/npm/@trimble-oss/moduswebcomponents/modus-wc-styles.css"
/>

<!-- Modus Icons -->
<link
  rel="preload"
  href="https://cdn.jsdelivr.net/npm/@trimble-oss/modus-icons@latest/dist/modus-outlined/fonts/modus-icons.css"
  as="style"
  crossorigin="anonymous"
/>
<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/npm/@trimble-oss/modus-icons@latest/dist/modus-outlined/fonts/modus-icons.css"
/>
```

---

## 2. JavaScript loader

```html
<script type="module">
  import { defineCustomElements } from "https://cdn.jsdelivr.net/npm/@trimble-oss/moduswebcomponents/loader/index.js";

  // registers all <modus-wc-*> tags once the module finishes loading
  defineCustomElements();
</script>
```

---

## 3. Theme attribute

The root `<html>` tag must carry a `data-theme` that matches one of the shipped themes:

```html
<html lang="en" data-theme="modus-classic-light"></html>
```

Available values: `modus-modern-light` · `modus-modern-dark` · `modus-classic-light` · `modus-classic-dark`.

---

## 4. Runtime theme switch helper

```html
<select
  onchange="document.documentElement.setAttribute('data-theme', this.value)"
>
  <option value="modus-modern-light">Modern Light</option>
  <option value="modus-modern-dark">Modern Dark</option>
  <option value="modus-classic-light">Classic Light</option>
  <option value="modus-classic-dark">Classic Dark</option>
</select>
```

Persist the user’s choice by writing the value to `localStorage` and re-applying it on `DOMContentLoaded` if desired.

---

## 5. Sanity check snippet

After the script loader runs, the custom elements are available:

```js
console.log(
  "Button defined:",
  customElements.get("modus-wc-button") !== undefined
);
```

If the log prints `true`, you’re ready to embed any `<modus-wc-*>` component.

---

## 6. Charts

Use Charts.js when building dashboards or when a chart is needed.
Load Chart.js once, then drop a <canvas> element and initialise.

<!-- Chart.js CDN -->
<script src="https://cdn.jsdelivr.net/npm/chart.js@4/dist/chart.umd.min.js"></script>

<!-- Example -->

```html
<canvas id="chartjs-bar" width="600" height="400"></canvas>

<script type="module">
  import { Chart } from "https://cdn.jsdelivr.net/npm/chart.js@4/dist/chart.umd.min.js";

  new Chart(document.getElementById("chartjs-bar"), {
    type: "bar",
    data: {
      labels: ["Q1", "Q2", "Q3", "Q4"],
      datasets: [
        {
          label: "2025 Revenue ($M)",
          data: [12, 18, 16, 21],
          backgroundColor: "var(--modus-primary, #0076FF)",
        },
      ],
    },
    options: {
      responsive: true,
      plugins: {
        legend: { position: "bottom" },
        tooltip: { mode: "index", intersect: false },
      },
    },
  });
</script>
```

## 7. Forms

Form Inputs Docs: https://trimble-oss.github.io/modus-wc-2.0/main/?path=/docs/documentation-form-inputs--docs

## 8. Modus Web Componenents Index

Below is a compact, LLM‑friendly index of every Modus Web Component. Each bullet lists the tag name, a short description, and a CDN URL.
modus-wc-accordion — collapsible accordion sections — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-accordion.md
modus-wc-alert — inline alert / notification banner — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-alert.md
modus-wc-autocomplete — text input with suggestion dropdown — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-autocomplete.md
modus-wc-avatar — circular or square user avatar image — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-avatar.md
modus-wc-badge — small status or count pill — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-badge.md
modus-wc-breadcrumbs — navigation path links — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-breadcrumbs.md
modus-wc-button — action button with variants & sizes — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-button.md
modus-wc-card — content container with header/body/actions — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-card.md
modus-wc-checkbox — binary checkbox form control — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-checkbox.md
modus-wc-chip — compact labelled pill with optional icon/dismiss — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-chip.md
modus-wc-collapse — show/hide content region — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-collapse.md
modus-wc-date — date picker input — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-date.md
modus-wc-divider — horizontal or vertical separator line — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-divider.md
modus-wc-icon — Modus vector icon renderer — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-icon.md
modus-wc-input-feedback — helper or error message element — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-input-feedback.md
modus-wc-input-label — floating label wrapper for inputs — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-input-label.md
modus-wc-loader — animated loading spinner — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-loader.md
modus-wc-menu-item — single selectable item inside menu — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-menu-item.md
modus-wc-menu — list of menu items with keyboard nav — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-menu.md
modus-wc-modal — dialog overlay — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-modal.md
modus-wc-navbar — top application bar with menus & profile — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-navbar.md
modus-wc-number-input — numeric input with step buttons — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-number-input.md
modus-wc-pagination — page navigation control — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-pagination.md
modus-wc-progress — linear or radial progress indicator — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-progress.md
modus-wc-radio — mutually‑exclusive radio button — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-radio.md
modus-wc-rating — star / heart / smiley rating input — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-rating.md
modus-wc-select — dropdown single‑select list — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-select.md
modus-wc-skeleton — grey loading placeholder block — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-skeleton.md
modus-wc-slider — range slider for numeric input — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-slider.md
modus-wc-stepper — visual workflow steps indicator — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-stepper.md
modus-wc-switch — on/off toggle switch — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-switch.md
modus-wc-table — data grid with sorting & pagination — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-table.md
modus-wc-tabs — tabbed navigation & panels — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-tabs.md
modus-wc-text-input — single‑line text input field — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-text-input.md
modus-wc-textarea — multi‑line text input — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-textarea.md
modus-wc-theme-switcher — light/dark theme toggle — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-theme-switcher.md
modus-wc-time-input — time picker input — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-time-input.md
modus-wc-toast — transient stacked notifications — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-toast.md
modus-wc-toolbar — simple horizontal toolbar layout — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-toolbar.md
modus-wc-tooltip — hover/focus helper text bubble — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-tooltip.md
modus-wc-typography — semantic text wrapper with Modus sizing — https://cdn.jsdelivr.net/gh/your-org/modus-docs/modus-wc-typography.md
