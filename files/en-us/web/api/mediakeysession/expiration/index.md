---
title: "MediaKeySession: expiration property"
short-title: expiration
slug: Web/API/MediaKeySession/expiration
page-type: web-api-instance-property
browser-compat: api.MediaKeySession.expiration
---

{{APIRef("Encrypted Media Extensions")}}{{SecureContext_Header}}

The **`expiration`** read-only property of the {{domxref('MediaKeySession')}} interface returns the time after which the keys in the current session can no longer be used to decrypt media data, or NaN if no such time exists.

This value is determined by the CDM and measured in milliseconds since January 1, 1970, UTC.
This value may change during a session lifetime, such as when an action triggers the start of a window.

## Value

A number or NaN.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}
