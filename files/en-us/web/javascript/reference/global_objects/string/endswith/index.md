---
title: String.prototype.endsWith()
short-title: endsWith()
slug: Web/JavaScript/Reference/Global_Objects/String/endsWith
page-type: javascript-instance-method
browser-compat: javascript.builtins.String.endsWith
sidebar: jsref
---

The **`endsWith()`** method of {{jsxref("String")}} values determines whether a string ends with the characters of this string, returning `true` or `false` as appropriate.

{{InteractiveExample("JavaScript Demo: String.prototype.endsWith()")}}

```js interactive-example
const str1 = "Cats are the best!";

console.log(str1.endsWith("best!"));
// Expected output: true

console.log(str1.endsWith("best", 17));
// Expected output: true

const str2 = "Is this a question?";

console.log(str2.endsWith("question"));
// Expected output: false
```

## Syntax

```js-nolint
endsWith(searchString)
endsWith(searchString, endPosition)
```

### Parameters

- `searchString`
  - : The characters to be searched for at the end of `str`. Cannot [be a regex](/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp#special_handling_for_regexes). All values that are not regexes are [coerced to strings](/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#string_coercion), so omitting it or passing `undefined` causes `endsWith()` to search for the string `"undefined"`, which is rarely what you want.
- `endPosition` {{optional_inline}}
  - : The end position at which `searchString` is expected to be found (the index of `searchString`'s last character plus 1). Defaults to `str.length`.

### Return value

**`true`** if the given characters are found at the end of the string, including when `searchString` is an empty string; otherwise, **`false`**.

### Exceptions

- {{jsxref("TypeError")}}
  - : Thrown if `searchString` [is a regex](/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp#special_handling_for_regexes).

## Description

This method lets you determine whether or not a string ends with another string. This method is case-sensitive.

## Examples

### Using endsWith()

```js
const str = "To be, or not to be, that is the question.";

console.log(str.endsWith("question.")); // true
console.log(str.endsWith("to be")); // false
console.log(str.endsWith("to be", 19)); // true
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Polyfill of `String.prototype.endsWith` in `core-js`](https://github.com/zloirock/core-js#ecmascript-string-and-regexp)
- [es-shims polyfill of `String.prototype.endsWith`](https://www.npmjs.com/package/string.prototype.endswith)
- {{jsxref("String.prototype.startsWith()")}}
- {{jsxref("String.prototype.includes()")}}
- {{jsxref("String.prototype.indexOf()")}}
- {{jsxref("String.prototype.lastIndexOf()")}}
