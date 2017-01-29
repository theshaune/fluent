---
variations: ['-primary', '-secondary']
states:     ['disabled', ':hover', ':active', ':focus']
---

## Buttons

The standard commonly used button.

### Basic usage

::: demo one
```html
<button {{states}} class="button {{variations}}">Default Button</button>
```
:::

### Variations

::: demo Two
```html
<button class="button">Default Button</button>
<button class="button -primary">Primary Button</button>
<button class="button -secondary">Secondary Button</button>
```
:::

### States

```html
<button disabled class="button">Default Button</button>
<button disabled class="button -primary">Primary Button</button>
<button disabled class="button -secondary">Secondary Button</button>
```