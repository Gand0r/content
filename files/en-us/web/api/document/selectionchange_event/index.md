---
title: "Document: selectionchange event"
short-title: selectionchange
slug: Web/API/Document/selectionchange_event
page-type: web-api-event
browser-compat: api.Document.selectionchange_event
---

{{APIRef}}

The **`selectionchange`** event of the [Selection API](/en-US/docs/Web/API/Selection) is fired when the current {{domxref("Selection")}} of a {{domxref("Document")}} is changed.

This event is not cancelable and does not bubble.

The event can be handled by adding an event listener for `selectionchange` or using the `onselectionchange` event handler.

> [!NOTE]
> This event is not quite the same as the `selectionchange` events fired when the text selection in an {{HTMLElement("input")}} or {{HTMLElement("textarea")}} element is changed. See the {{domxref("HTMLInputElement.selectionchange_event", "selectionchange")}} event of `HTMLInputElement` for more details.

## Syntax

Use the event name in methods like {{domxref("EventTarget.addEventListener", "addEventListener()")}}, or set an event handler property.

```js-nolint
addEventListener("selectionchange", (event) => { })

onselectionchange = (event) => { }
```

## Event type

A generic {{domxref("Event")}}.

## Examples

```js
// addEventListener version
document.addEventListener("selectionchange", () => {
  console.log(document.getSelection());
});

// onselectionchange version
document.onselectionchange = () => {
  console.log(document.getSelection());
};
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("Node/selectstart_event", "selectstart")}}
- {{domxref("Document.getSelection()")}}
- {{domxref("Selection", "Selection")}}
