---
title: String.prototype.trim()
short-title: trim()
slug: Web/JavaScript/Reference/Global_Objects/String/trim
page-type: javascript-instance-method
browser-compat: javascript.builtins.String.trim
sidebar: jsref
---

The **`trim()`** method of {{jsxref("String")}} values removes whitespace from both ends of this string and returns a new string, without modifying the original string.

To return a new string with whitespace trimmed from just one end, use {{jsxref("String/trimStart", "trimStart()")}} or {{jsxref("String/trimEnd", "trimEnd()")}}.

{{InteractiveExample("JavaScript Demo: String.prototype.trim()")}}

```js interactive-example
const greeting = "   Hello world!   ";

console.log(greeting);
// Expected output: "   Hello world!   ";

console.log(greeting.trim());
// Expected output: "Hello world!";
```

## Syntax

```js-nolint
trim()
```

### Parameters

None.

### Return value

A new string representing `str` stripped of whitespace from both its beginning and end. Whitespace is defined as [white space](/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#white_space) characters plus [line terminators](/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#line_terminators).

If neither the beginning or end of `str` has any whitespace, a new string is still returned (essentially a copy of `str`).

## Examples

### Using trim()

The following example trims whitespace from both ends of `str`.

```js
const str = "   foo  ";
console.log(str.trim()); // 'foo'
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{jsxref("String.prototype.trimStart()")}}
- {{jsxref("String.prototype.trimEnd()")}}
