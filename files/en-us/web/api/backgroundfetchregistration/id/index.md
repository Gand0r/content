---
title: "BackgroundFetchRegistration: id property"
short-title: id
slug: Web/API/BackgroundFetchRegistration/id
page-type: web-api-instance-property
status:
  - experimental
browser-compat: api.BackgroundFetchRegistration.id
---

{{APIRef("Background Fetch API")}}{{SeeCompatTable}}{{AvailableInWorkers}}

The **`id`** read-only property of the {{domxref("BackgroundFetchRegistration")}} interface returns a copy of the background fetch's `ID`.

## Value

A string.

## Examples

Logging the this part to the console returns the identifier set when registering the fetch. In this case, `"my-fetch"`.

```js
console.log(bgFetch.id); // "my-fetch"
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
