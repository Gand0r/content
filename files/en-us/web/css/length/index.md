---
title: <length>
slug: Web/CSS/length
page-type: css-type
browser-compat: css.types.length
sidebar: cssref
---

The **`<length>`** [CSS](/en-US/docs/Web/CSS) [data type](/en-US/docs/Web/CSS/CSS_Values_and_Units/CSS_data_types) represents a distance value. Lengths can be used in numerous CSS properties, such as {{Cssxref("width")}}, {{Cssxref("height")}}, {{Cssxref("margin")}}, {{Cssxref("padding")}}, {{Cssxref("border-width")}}, {{Cssxref("font-size")}}, and {{Cssxref("text-shadow")}}.

> [!NOTE]
> Although {{cssxref("&lt;percentage&gt;")}} values are usable in some of the same properties that accept `<length>` values, they are not themselves `<length>` values. See {{cssxref("&lt;length-percentage&gt;")}}.

## Syntax

The `<length>` data type consists of a {{cssxref("&lt;number&gt;")}} followed by one of the units listed below. As with all CSS dimensions, there is no space between the number and the unit literal. Specifying the length unit is optional if the number is `0`.

> [!NOTE]
> Some properties allow negative `<length>` values, while others do not.

The [specified value](/en-US/docs/Web/CSS/CSS_cascade/Value_processing#specified_value) of a length (_specified length_) is represented by its quantity and unit. The [computed value](/en-US/docs/Web/CSS/CSS_cascade/Value_processing#computed_value) of a length (_computed length_) is the specified length resolved to an absolute length, and its unit is not distinguished.

The `<length>` units can be relative or absolute. Relative lengths represent a measurement in terms of some other distance. Depending on the unit, this distance can be the size of a specific character, the [line height](/en-US/docs/Web/CSS/line-height), or the size of the {{Glossary("viewport")}}. Style sheets that use relative length units can more easily scale from one output environment to another.

> [!NOTE]
> Child elements do not inherit the relative values as specified for their parent; they inherit the computed values.

## Relative length units

CSS relative length units are based on font, container, or viewport sizes.

### Relative length units based on font

Font lengths define the `<length>` value in terms of the size of a particular character or font attribute in the font currently in effect in an element or its parent.

> [!NOTE]
> These units, especially `em` and the root relative `rem`, are often used to create scalable layouts, which maintain the vertical rhythm of the page even when the user changes the font size.

- `cap`
  - : Represents the "cap height" (nominal height of capital letters) of the element's {{Cssxref("font")}}.
- `ch`
  - : Represents the width or, more precisely, the {{Glossary("advance measure")}} of the glyph `0` (zero, the Unicode character U+0030) in the element's {{Cssxref("font")}}.
    In cases where determining the measure of the `0` glyph is impossible or impractical, it must be assumed to be `0.5em` wide by `1em` tall.
- `em`
  - : Represents the calculated {{Cssxref("font-size")}} of the element. If used on the {{Cssxref("font-size")}} property itself, it represents the _inherited_ font-size of the element.
- `ex`
  - : Represents the [x-height](https://en.wikipedia.org/wiki/X-height) of the element's {{Cssxref("font")}}. In fonts with the `x` letter, this is generally the height of lowercase letters in the font; `1ex ≈ 0.5em` in many fonts.
- `ic`
  - : Equal to the used {{Glossary("advance measure")}} of the "水" glyph (CJK water ideograph, U+6C34), found in the font used to render it.
- `lh`
  - : Equal to the computed value of the {{Cssxref("line-height")}} property of the element on which it is used, converted to an absolute length. This unit enables length calculations based on the theoretical size of an ideal empty line. However, the size of actual line boxes may differ based on their content.

### Relative length units based on root element's font

Root element font relative length units define the `<length>` value in terms of the size of a particular character or font attribute of the [root](/en-US/docs/Web/CSS/:root) element:

- `rcap`
  - : Equal to the "cap height" (nominal height of capital letters) of the root element's {{Cssxref("font")}}.
- `rch`
  - : Equal to the width or the {{Glossary("advance measure")}} of the glyph `0` (zero, the Unicode character U+0030) in the root element's {{Cssxref("font")}}.
- `rem`
  - : Represents the {{Cssxref("font-size")}} of the root element (typically {{HTMLElement("html")}}). When used within the root element {{Cssxref("font-size")}}, it represents its initial value. A common browser default is `16px`, but user-defined preferences may modify this.
- `rex`
  - : Represents the x-height of the root element's {{Cssxref("font")}}.
- `ric`
  - : Equal to the value of [`ic`](#ic) unit on the root element's font.
- `rlh`
  - : Equal to the value of [`lh`](#lh) unit on the root element's font. This unit enables length calculations based on the theoretical size of an ideal empty line. However, the size of actual line boxes may differ based on their content.

### Relative length units based on viewport

The **viewport-percentage length units** are based on four different viewport sizes: small, large, dynamic, and default. The allowance for the different viewport sizes is in response to browser interfaces expanding and retracting dynamically and hiding and showing the content underneath.

- **Small viewport units**
  - : When you want the smallest possible viewport in response to browser interfaces expanding dynamically, you should use the small viewport size. The small viewport size allows the content you design to fill the entire viewport when browser interfaces are expanded. Choosing this size might also possibly leave empty spaces when browser interfaces retract.

    For example, an element that is sized using viewport-percentage units based on the small viewport size, the element will fill the screen perfectly without any of its content being obscured when all the dynamic browser interfaces are shown. When those browser interfaces are hidden, however, there might be extra space visible around the element. Therefore, the small viewport-percentage units are "safer" to use in general, but might not produce the most attractive layout after a user starts interacting with the page.

    The small viewport size is represented by the `sv` prefix and results in the `sv*` viewport-percentage length units. The sizes of the small viewport-percentage units are fixed, and therefore stable, unless the viewport itself is resized.

- **Large viewport units**
  - : When you want the largest possible viewport in response to browser interfaces retracting dynamically, you should use the large viewport size. The large viewport size allows the content you design to fill the entire viewport when browser interfaces are retracting. You need to be aware that the content might get hidden when browser interfaces expand.

    For example, on mobile phones where screen real-estate is at a premium, browsers often hide part or all of the title and address bar after a user starts scrolling the page. When an element is sized using a viewport-percentage unit based on the large viewport size, the content of the element will fill the entire visible page when these browser interfaces are hidden. However, when these retractable browser interfaces are shown, they can hide the content that is sized or positioned using the _large_ viewport-percentage units.

    The large viewport unit is represented by the `lv` prefix and results in the `lv*` viewport-percentage units. The sizes of the large viewport-percentage units are fixed and therefore stable, unless the viewport itself is resized.

- **Dynamic viewport units**
  - : When you want the viewport to be automatically sized in response to browser interfaces dynamically expanding or retracting, you can use the dynamic viewport size. The dynamic viewport size allows the content you design to fit exactly within the viewport, irrespective of the presence of dynamic browser interfaces.

    The dynamic viewport unit is represented by the `dv` prefix and results in the `dv*` viewport-percentage units. The sizes of the dynamic viewport-percentage units are not stable, even when the viewport itself is unchanged.

    > [!NOTE]
    > While the dynamic viewport size can give you more control and flexibility, using viewport-percentage units based on the dynamic viewport size can cause the content to resize while a user is scrolling a page. This can lead to degradation of the user interface and cause a performance hit.

- **Default viewport units**
  - : The default viewport size is defined by the browser. The behavior of the resulting viewport-percentage unit could be equivalent to the viewport-percentage unit based on the small viewport size, the large viewport size, an intermediate size between the two, or the dynamic viewport size.

    > [!NOTE]
    > For example, a browser might implement the default viewport-percentage unit for height (`vh`) that is equivalent to the large viewport-percentage height unit (`lvh`). If so, this could obscure content on a full-page display while the browser interface is expanded. Currently, all default viewport units (`vh`, `vw`, etc.) are equivalent to their large viewport counterparts (`lvh`, `lvw`, etc.).

Viewport-percentage lengths define `<length>` values in percentage relative to the size of the initial [containing block](/en-US/docs/Web/CSS/CSS_display/Containing_block), which in turn is based on either the size of the {{Glossary("viewport")}} or the page area, i.e., the visible portion of the document. When the height or width of the initial containing block is changed, the elements that are sized based on them are scaled accordingly. There is a viewport-percentage length unit variant corresponding to each of the viewport sizes, as described below.

> [!NOTE]
> Viewport lengths are invalid in {{cssxref("@page")}} declaration blocks.

- `vh`
  - : Represents a percentage of the height of the viewport's initial [containing block](/en-US/docs/Web/CSS/CSS_display/Containing_block). `1vh` is 1% of the viewport height. For example, if the viewport height is `300px`, then a value of `70vh` on a property will be `210px`.

    The respective viewport-percentage units for small, large, and dynamic viewport sizes are `svh`, `lvh`, and `dvh`. `vh` is equivalent to `lvh`, representing the viewport-percentage length unit based on the large viewport size.

- `vw`
  - : Represents a percentage of the width of the viewport's initial [containing block](/en-US/docs/Web/CSS/CSS_display/Containing_block). `1vw` is 1% of the viewport width. For example, if the viewport width is `800px`, then a value of `50vw` on a property will be `400px`.

    For small, large, and dynamic viewport sizes, the respective viewport-percentage units are `svw`, `lvw`, and `dvw`.
    `vw` is equivalent to `lvw`, representing the viewport-percentage length unit based on the large viewport size.

- `vmax`
  - : Represents in percentage the largest of `vw` and `vh`.

    For small, large, and dynamic viewport sizes, the respective viewport-percentage units are `svmax`, `lvmax`, and `dvmax`.
    `vmax` is equivalent to `lvmax`, representing the viewport-percentage length unit based on the large viewport size.

- `vmin`
  - : Represents in percentage the smallest of `vw` and `vh`.

    For small, large, and dynamic viewport sizes, the respective viewport-percentage units are `svmin`, `lvmin`, and `dvmin`.
    `vmin` is equivalent to `lvmin`, representing the viewport-percentage length unit based on the large viewport size.

- `vb`
  - : Represents the percentage of the size of the initial [containing block](/en-US/docs/Web/CSS/CSS_display/Containing_block), in the direction of the root element's [block axis](/en-US/docs/Web/CSS/CSS_logical_properties_and_values).

    For small, large, and dynamic viewport sizes, the respective viewport-percentage units are `svb`, `lvb`, and `dvb`, respectively.
    `vb` is equivalent to `lvb`, representing the viewport-percentage length unit based on the large viewport size.

- `vi`
  - : Represents a percentage of the size of the initial [containing block](/en-US/docs/Web/CSS/CSS_display/Containing_block), in the direction of the root element's [inline axis](/en-US/docs/Web/CSS/CSS_logical_properties_and_values).

    For small, large, and dynamic viewport sizes, the respective viewport-percentage units are `svi`, `lvi`, and `dvi`.
    `vi` is equivalent to `lvi`, representing the viewport-percentage length unit based on the large viewport size.

### Container query length units

When applying styles to a container using container queries, you can use container query length units.
These units specify a length relative to the dimensions of a query container.
Components that use units of length relative to their container are more flexible to use in different containers without having to recalculate concrete length values.

If no eligible container is available for the query, the container query length unit defaults to the [small viewport unit](#small_viewport_units) for that axis (`sv*`).

For more information, see [Container queries](/en-US/docs/Web/CSS/CSS_containment/Container_queries).

- `cqw`
  - : Represents a percentage of the width of the query container. `1cqw` is 1% of the query container's width. For example, if the query container's width is `800px`, then a value of `50cqw` on a property will be `400px`.

- `cqh`
  - : Represents a percentage of the height of the query container. `1cqh` is 1% of the query container's height. For example, if the query container's height is `300px`, then a value of `10cqh` on a property will be `30px`.

- `cqi`
  - : Represents a percentage of the inline size of the query container. `1cqi` is 1% of the query container's inline size. For example, if the query container's inline size is `800px`, then a value of `50cqi` on a property will be `400px`.

- `cqb`
  - : Represents a percentage of the block size of the query container. `1cqb` is 1% of the query container's block size. For example, if the query container's block size is `300px`, then a value of `10cqb` on a property will be `30px`.

- `cqmin`
  - : Represents a percentage of the smaller value of either the query container's inline size or block size. `1cqmin` is 1% of the smaller value of either the query container's inline size or block size. For example, if the query container's inline size is `800px` and its block size is `300px`, then a value of `50cqmin` on a property will be `150px`.

- `cqmax`
  - : Represents a percentage of the larger value of either the query container's inline size or block size. `1cqmax` is 1% of the larger value of either the query container's inline size or block size. For example, if the query container's inline size is `800px` and its block size is `300px`, then a value of `50cqmax` on a property will be `400px`.

## Absolute length units

**Absolute length units** represent a physical measurement when the physical properties of the output medium are known, such as for print layout. This is done by anchoring one of the units to a **physical unit** or the **visual angle unit** and then defining the others relative to it. Physical units include `cm`, `in`, `mm`, `pc`, `pt`, `px`, and `Q`.The anchoring is done differently for low-resolution devices, such as screens, versus high-resolution devices, such as printers.

For low-dpi devices, the unit `px` represents the physical _reference pixel_; other units are defined relative to it. Thus, `1in` is defined as `96px`, which equals `72pt`. The consequence of this definition is that on such devices, dimensions described in inches (`in`), centimeters (`cm`), or millimeters (`mm`) don't necessarily match the size of the physical unit with the same name.

For high-dpi devices, inches (`in`), centimeters (`cm`), and millimeters (`mm`) are the same as their physical counterparts. Therefore, the `px` unit is defined relative to them (1/96 of `1in`).

> [!NOTE]
> Many users increase their {{Glossary("user agent")}}'s default font size to make text more legible. Absolute lengths can cause accessibility problems because they are fixed and do not scale according to user settings. For this reason, prefer relative lengths (such as `em` or `rem`) when setting `font-size`.

- `px`
  - : One pixel. For screen displays, it traditionally represents one {{glossary("device pixel")}} (dot). However, for _printers_ and _high-resolution screens_, one CSS pixel implies multiple device pixels. `1px` = `1in / 96`.
- `cm`
  - : One centimeter. `1cm` = `96px / 2.54`.
- `mm`
  - : One millimeter. `1mm` = `1cm / 10`.
- `Q`
  - : One quarter of a millimeter. `1Q` = `1cm / 40`.
- `in`
  - : One inch. `1in` = `2.54cm` = `96px`.
- `pc`
  - : One pica. `1pc` = `12pt` = `1in / 6`.
- `pt`
  - : One point. `1pt` = `1in / 72`.

## Interpolation

When animated, values of the `<length>` data type are interpolated as real, floating-point numbers. The {{glossary("interpolation")}} happens on the calculated value. The speed of the interpolation is determined by the [easing function](/en-US/docs/Web/CSS/easing-function) associated with the animation.

## Examples

### Comparing different length units

The following example provides you with an input field in which you can enter a `<length>` value (e.g., `300px`, `50%`, `30vw`) to set the width of a result bar that will appear below it once you've pressed the <kbd>Enter</kbd> or the <kbd>Return</kbd> key.

This allows you to compare and contrast the effects of different length units.

#### HTML

```html
<div class="outer">
  <div class="input-container">
    <label for="length">Enter width:</label>
    <input type="text" id="length" />
  </div>
  <div class="inner"></div>
</div>
<div class="results"></div>
```

#### CSS

```css
html {
  font-family: sans-serif;
  font-weight: bold;
  box-sizing: border-box;
}

.outer {
  width: 100%;
  height: 50px;
  background-color: #eee;
  position: relative;
}

.inner {
  height: 50px;
  background-color: #999;
  box-shadow:
    inset 3px 3px 5px rgb(255 255 255 / 50%),
    inset -3px -3px 5px rgb(0 0 0 / 50%);
}

.result {
  height: 20px;
  box-shadow:
    inset 3px 3px 5px rgb(255 255 255 / 50%),
    inset -3px -3px 5px rgb(0 0 0 / 50%);
  background-color: orange;
  display: flex;
  align-items: center;
  margin-top: 10px;
}

.result code {
  position: absolute;
  margin-left: 20px;
}

.results {
  margin-top: 10px;
}

.input-container {
  position: absolute;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  height: 50px;
}

label {
  margin: 0 10px 0 20px;
}
```

#### JavaScript

```js
const inputDiv = document.querySelector(".inner");
const inputElem = document.querySelector("input");
const resultsDiv = document.querySelector(".results");

inputElem.addEventListener("change", () => {
  inputDiv.style.width = inputElem.value;

  const result = document.createElement("div");
  result.className = "result";
  result.style.width = inputElem.value;
  const code = document.createElement("code");
  code.textContent = `width: ${inputElem.value}`;
  result.appendChild(code);
  resultsDiv.appendChild(result);

  inputElem.value = "";
  inputElem.focus();
});
```

#### Result

{{EmbedLiveSample('Comparing different length units', '100%', 700)}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Learn: Values and units](/en-US/docs/Learn_web_development/Core/Styling_basics/Values_and_units)
- [CSS values & units](/en-US/docs/Web/CSS/CSS_Values_and_Units) module
- [Box Model](/en-US/docs/Web/CSS/CSS_box_model)
