---
title: clearTimeout() global function
short-title: clearTimeout()
slug: Web/API/clearTimeout
page-type: web-api-global-function
browser-compat: api.clearTimeout
---

{{APIRef("HTML DOM")}}{{AvailableInWorkers}}

The global **`clearTimeout()`** method cancels a timeout previously established
by calling {{domxref("setTimeout()")}}.

If the parameter provided does not identify a previously established action,
this method does nothing.

## Syntax

```js-nolint
clearTimeout(timeoutID)
```

### Parameters

- `timeoutID`
  - : The identifier of the timeout you want to cancel. This ID was returned by the
    corresponding call to `setTimeout()`.

It's worth noting that the pool of IDs used by {{domxref("setTimeout()")}} and {{domxref("Window.setInterval", "setInterval()")}} are shared, which means you can technically use `clearTimeout()` and {{domxref("Window.clearInterval", "clearInterval()")}} interchangeably. However, for clarity, you should avoid doing so.

### Return value

None ({{jsxref("undefined")}}).

## Examples

Run the script below in the context of a web page and click on the page once. You'll
see a message popping up in a second. If you click the page multiple times in
one second, the alert only appears once.

```js
const alarm = {
  remind(aMessage) {
    alert(aMessage);
    this.timeoutID = undefined;
  },

  setup() {
    if (typeof this.timeoutID === "number") {
      this.cancel();
    }

    this.timeoutID = setTimeout(
      (msg) => {
        this.remind(msg);
      },
      1000,
      "Wake up!",
    );
  },

  cancel() {
    clearTimeout(this.timeoutID);
  },
};
window.addEventListener("click", () => alarm.setup());
```

## Notes

Passing an invalid ID to `clearTimeout()` silently does nothing; no
exception is thrown.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("setTimeout()")}}
- {{domxref("Window.clearInterval()")}} and {{domxref("WorkerGlobalScope.clearInterval()")}}
- {{domxref("Window.cancelAnimationFrame()")}} and {{domxref("DedicatedWorkerGlobalScope.cancelAnimationFrame()")}}
