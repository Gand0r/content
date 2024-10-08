---
title: "CloseEvent: wasClean property"
short-title: wasClean
slug: Web/API/CloseEvent/wasClean
page-type: web-api-instance-property
browser-compat: api.CloseEvent.wasClean
---

{{APIRef("Websockets API")}}{{AvailableInWorkers}}

The **`wasClean`** read-only property of the {{domxref("CloseEvent")}} interface returns `true` if the connection closed cleanly.

## Value

A boolean value. True if the connection closed cleanly, false otherwise.

## Examples

The following example prints the value of `wasClean` to the console.

```js
WebSocket.onclose = (event) => {
  console.log(event.wasClean);
};
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
