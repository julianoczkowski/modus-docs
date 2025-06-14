---
tag: modus-wc-alert
category: Feedback & Messaging
storybook: https://trimble-oss.github.io/modus-wc-2.0/main/?path=/docs/components-alert--docs
---

## Purpose

Displays contextual status messages—error, warning, success, info—optionally with a dismiss button, custom icon, and action content.

## Attributes

- **`alert-title`**
  • _Type_: `string` **(required)**
  • _Default_: _none_
  • _Notes_: headline text of the alert.
  • _Reflected as prop_: **yes**

- **`alert-description`**
  • _Type_: `string`
  • _Default_: _none_
  • _Notes_: longer descriptive text displayed under the title.
  • _Reflected as prop_: **yes**

- **`variant`**
  • _Type_: `"info" | "success" | "warning" | "error"`
  • _Default_: `"info"`
  • _Notes_: sets colour scheme and default icon.
  • _Reflected as prop_: **yes**

- **`dismissible`**
  • _Type_: `boolean`
  • _Default_: `false`
  • _Notes_: shows an “X” button that fires `dismissClick`.
  • _Reflected as prop_: **yes**

- **`icon`**
  • _Type_: `string` (Modus icon name)
  • _Default_: auto-selected by `variant`
  • _Notes_: overrides variant icon when supplied.
  • _Reflected as prop_: **yes**

- **`role`**
  • _Type_: `"alert" | "log" | "marquee" | "status" | "timer"`
  • _Default_: `"status"`
  • _Notes_: ARIA live-region semantics.
  • _Reflected as prop_: **yes**

- **`custom-class`**
  • _Type_: `string`
  • _Default_: empty string
  • _Notes_: extra CSS class on the host element for custom spacing / layout.
  • _Reflected as prop_: **yes**

## Events

- **`dismissClick`** — emitted when the dismiss button is pressed (payload: `CustomEvent<void>`).

## Usage

```html
<!-- Default (info) -->
<modus-wc-alert
  alert-title="New message!"
  alert-description="You have 3 new messages."
>
</modus-wc-alert>

<!-- Variant examples -->
<modus-wc-alert
  variant="success"
  alert-title="Success!"
  alert-description="Operation completed."
></modus-wc-alert>
<modus-wc-alert
  variant="warning"
  alert-title="Heads-up!"
  alert-description="Check the details."
></modus-wc-alert>
<modus-wc-alert
  variant="error"
  alert-title="Error!"
  alert-description="Something went wrong."
></modus-wc-alert>

<!-- Dismissible -->
<modus-wc-alert
  dismissible
  alert-title="Dismiss me"
  alert-description="Click the X to close."
></modus-wc-alert>

<!-- Custom icon -->
<modus-wc-alert
  icon="help"
  variant="info"
  alert-title="Need help?"
  alert-description="Visit our docs."
></modus-wc-alert>

<!-- Action button slot -->
<modus-wc-alert
  alert-title="New messages"
  alert-description="You have 3 unread messages."
>
  <modus-wc-button slot="button" color="secondary" variant="outlined" size="sm">
    View
  </modus-wc-button>
</modus-wc-alert>

<!-- Custom content slot -->
<modus-wc-alert variant="success">
  <div slot="content">
    <strong>Well done!</strong> You successfully read this important alert
    message.
  </div>
</modus-wc-alert>
```

### Slot support

The component supports a **`button`** slot for action elements and a **`content`** slot when you omit `alert-title` / `alert-description` and provide fully custom markup instead.

### Pattern notes

- **Dismiss logic:** Listen for `dismissClick` to remove the element or update application state.
- **Icons:** Pass any Modus icon name to `icon`; leave blank to use the variant’s default.
- **ARIA:** Set `role="alert"` for interruptive messages that should be announced immediately.
- **Live updates:** Because the component is a live region, DOM changes inside it will be announced by screen readers.
