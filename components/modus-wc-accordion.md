---
tag: modus-wc-accordion
category: Navigation & Disclosure
storybook: https://trimble-oss.github.io/modus-wc-2.0/main/?path=/docs/components-accordion--docs
---

## Purpose

A lightweight container that groups one or more `modus-wc-collapse` items and coordinates their expand / collapse state.

## Attributes

- **`custom-class`**  
  • _Type_: `string`  
  • _Default_: empty string (`''`)  
  • _Notes_: adds a custom CSS class to the accordion’s inner wrapper, letting you override layout or spacing.  
  • _Reflected as prop_: **yes**:contentReference[oaicite:1]{index=1}

_(All other behaviour is inherited from the child `modus-wc-collapse` components you place inside the default slot.)_

## Events

- **`expandedChange`** — fires a `CustomEvent<{ expanded: boolean; index: number }>` each time a child collapse item toggles, reporting the item’s index and new state.:contentReference[oaicite:2]{index=2}

## Usage

```html
<modus-wc-accordion>
  <modus-wc-collapse collapse-id="item1" title="Item One">
    <div slot="content">Content for item one.</div>
  </modus-wc-collapse>

  <modus-wc-collapse collapse-id="item2" title="Item Two">
    <div slot="content">Content for item two.</div>
  </modus-wc-collapse>

  <modus-wc-collapse collapse-id="item3" title="Item Three">
    <div slot="content">Content for item three.</div>
  </modus-wc-collapse>
</modus-wc-accordion>

<script type="module">
  const accordion = document.querySelector("modus-wc-accordion");
  accordion.addEventListener("expandedChange", (e) => {
    console.log(
      "Item",
      e.detail.index,
      "is now",
      e.detail.expanded ? "open" : "closed"
    );
  });
</script>
```
