---
title: empty-cells
slug: Web/CSS/empty-cells
page-type: css-property
browser-compat: css.properties.empty-cells
sidebar: cssref
---

The **`empty-cells`** [CSS](/en-US/docs/Web/CSS) property sets whether borders and backgrounds appear around {{htmlelement("table")}} cells that have no visible content.

{{InteractiveExample("CSS Demo: empty-cells")}}

```css interactive-example-choice
empty-cells: show;
```

```css interactive-example-choice
empty-cells: hide;
```

```html interactive-example
<section class="default-example" id="default-example">
  <table class="transition-all" id="example-element">
    <tr>
      <th>Client Name</th>
      <th>Age</th>
    </tr>
    <tr>
      <td></td>
      <td>25</td>
    </tr>
    <tr>
      <td>Louise Q.</td>
      <td></td>
    </tr>
    <tr>
      <td>Owen B.</td>
      <td></td>
    </tr>
    <tr>
      <td>Stan L.</td>
      <td>71</td>
    </tr>
  </table>
</section>
```

```css interactive-example
th,
td {
  border: 2px solid #a19;
  padding: 0.25rem 0.5rem;
}
```

This property has an effect only when the {{cssxref("border-collapse")}} property is `separate`.

## Syntax

```css
/* Keyword values */
empty-cells: show;
empty-cells: hide;

/* Global values */
empty-cells: inherit;
empty-cells: initial;
empty-cells: revert;
empty-cells: revert-layer;
empty-cells: unset;
```

The `empty-cells` property is specified as one of the keyword values listed below.

### Values

- `show`
  - : Borders and backgrounds are drawn like in normal cells.
- `hide`
  - : No borders or backgrounds are drawn.

## Formal definition

{{cssinfo}}

## Formal syntax

{{csssyntax}}

## Examples

### Showing and hiding empty table cells

#### HTML

```html
<table class="table_1">
  <tr>
    <td>Moe</td>
    <td>Larry</td>
  </tr>
  <tr>
    <td>Curly</td>
    <td></td>
  </tr>
</table>
<br />
<table class="table_2">
  <tr>
    <td>Moe</td>
    <td>Larry</td>
  </tr>
  <tr>
    <td>Curly</td>
    <td></td>
  </tr>
</table>
```

#### CSS

```css
.table_1 {
  empty-cells: show;
}

.table_2 {
  empty-cells: hide;
}

td,
th {
  border: 1px solid gray;
  padding: 0.5rem;
}
```

#### Result

{{ EmbedLiveSample('Showing_and_hiding_empty_table_cells', '100%', '200') }}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{cssxref("border-collapse")}}
- [Learn: Styling tables](/en-US/docs/Learn_web_development/Core/Styling_basics/Tables)
- [CSS table](/en-US/docs/Web/CSS/CSS_table) module
