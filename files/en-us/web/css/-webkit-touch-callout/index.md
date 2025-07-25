---
title: -webkit-touch-callout
slug: Web/CSS/-webkit-touch-callout
page-type: css-property
status:
  - non-standard
browser-compat: css.properties.-webkit-touch-callout
sidebar: cssref
---

{{Non-standard_header}}

The `-webkit-touch-callout` [CSS](/en-US/docs/Web/CSS) property controls the display of the default callout shown when you touch and hold a touch target.

When a target is touched and held on iOS, Safari displays a callout information about the link. This property allows disabling that behavior.

## Syntax

```css
/* Keyword values */
-webkit-touch-callout: default;
-webkit-touch-callout: none;

/* Global values */
-webkit-touch-callout: initial;
-webkit-touch-callout: inherit;
-webkit-touch-callout: revert;
-webkit-touch-callout: revert-layer;
-webkit-touch-callout: unset;
```

### Values

- `default`
  - : The default callout is displayed.
- `none`
  - : The callout is disabled.

## Formal definition

{{CSSInfo}}

## Formal syntax

{{CSSSyntaxRaw(`-webkit-touch-callout = default | none`)}}

## Examples

### Turn off touch callout

```css
.example {
  -webkit-touch-callout: none;
}
```

## Specifications

Not part of any standard. Apple has a [description in the Safari CSS Reference](https://developer.apple.com/library/archive/documentation/AppleApplications/Reference/SafariCSSRef/Articles/StandardCSSProperties.html#//apple_ref/doc/uid/TP30001266-_webkit_touch_callout).

## Browser compatibility

{{Compat}}

## See also

- [WebKit CSS extensions](/en-US/docs/Web/CSS/WebKit_Extensions)
- [-webkit-touch-callout in the Apple developer documentation](https://developer.apple.com/library/archive/documentation/AppleApplications/Reference/SafariCSSRef/Articles/StandardCSSProperties.html#//apple_ref/doc/uid/TP30001266-_webkit_touch_callout)
