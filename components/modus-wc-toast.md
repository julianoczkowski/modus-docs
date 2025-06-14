---
tag: modus-wc-toast
category: Feedback & Messaging
storybook: https://trimble-oss.github.io/modus-wc-2.0/main/?path=/docs/components-toast--docs
---

## Purpose

Shows brief, self‑dismissing notifications that stack in one of nine screen positions. The toast component only handles _placement_ and _lifetime_; put an alert or any HTML inside its default slot for the actual message.

## Attributes

- **`custom-class`**
  • _Type_: `string` – default `''`
  • _Notes_: adds a CSS class to the toast container for margins, borders or animations.
  • _Reflected_: **yes**

- **`delay`**
  • _Type_: `number` _(milliseconds)_ – default `undefined` _(toast stays until removed)_
  • _Notes_: auto‑dismisses the toast after the given time. Set `0` to make it disappear immediately.
  • _Reflected_: **yes**

- **`position`**
  • _Type_: one of
  `"top-start" | "top-center" | "top-end" |
 "middle-start" | "middle-center" | "middle-end" |
 "bottom-start" | "bottom-center" | "bottom-end"`
  • _Default_: **`"top-end"`**
  • _Notes_: determines which corner/edge of the nearest _positioned_ ancestor the toast anchors to.
  • _Reflected_: **yes**

## Slots

- **_(default)_** — content of the toast (usually a `modus-wc-alert`, but any HTML works).

## Events

_None — the component does not emit custom events; listen to the slotted content (e.g. `dismissClick` from an alert) if you need callbacks._

## Usage

```html
<!-- 🔹 Container to illustrate placement -->
<div style="height:200px;position:relative;border:1px solid #ccc;padding:1rem;">
  <!-- Default toast (top‑end) -->
  <modus-wc-toast aria-label="Success toast">
    <modus-wc-alert
      alert-title="Changes saved!"
      variant="success"
    ></modus-wc-alert>
  </modus-wc-toast>
</div>

<!-- Auto‑dismiss after 3 s at bottom‑center -->
<modus-wc-toast position="bottom-center" delay="3000">
  <modus-wc-alert alert-title="Upload finished" variant="info"></modus-wc-alert>
</modus-wc-toast>

<!-- Different positions -->
<modus-wc-toast position="top-start">
  <modus-wc-alert alert-title="Top‑start" variant="warning"></modus-wc-alert>
</modus-wc-toast>
<modus-wc-toast position="middle-center">
  <modus-wc-alert alert-title="Middle" variant="error"></modus-wc-alert>
</modus-wc-toast>

<!-- Multiple stacked toasts (same position) -->
<div
  style="height:250px;position:relative;border:1px dashed #aaa;padding:1rem;"
>
  <modus-wc-toast position="top-end" delay="4000">
    <modus-wc-alert
      alert-title="First toast"
      variant="success"
    ></modus-wc-alert>
  </modus-wc-toast>
  <modus-wc-toast position="top-end" delay="5000">
    <modus-wc-alert alert-title="Second toast" variant="info"></modus-wc-alert>
  </modus-wc-toast>
</div>

<!-- Custom container styling via class -->
<style>
  .shadowy-toast {
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
  }
</style>
<modus-wc-toast position="top-center" custom-class="shadowy-toast" delay="6000">
  <modus-wc-alert alert-title="Styled container"></modus-wc-alert>
</modus-wc-toast>
```

### Pattern notes

- **Positioning context:** the toast uses `position:absolute`; ensure its nearest ancestor has `position:relative` (or `fixed`) so the coordinates make sense.
- **Auto‑dismiss vs manual:** combine `delay` with a dismissible `modus-wc-alert` so users can also close the toast early.
- **Stack order:** toasts stack automatically in render order; newer toasts appear closer to the anchor corner.
- **Accessibility:** keep slotted alerts short and meaningful; screen‑readers will announce them as live‑region updates.
- **Removal:** programmatically remove the toast element (`toast.remove()`) or let `delay` expire; no additional cleanup needed.
- **Global toast portal:** for app‑wide notifications, render all `modus-wc-toast` instances inside a fixed, top‑level container so they overlay every page.
