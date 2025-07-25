---
title: "WebGLRenderingContext: attachShader() method"
short-title: attachShader()
slug: Web/API/WebGLRenderingContext/attachShader
page-type: web-api-instance-method
browser-compat: api.WebGLRenderingContext.attachShader
---

{{APIRef("WebGL")}}{{AvailableInWorkers}}

The **WebGLRenderingContext.attachShader()** method of the [WebGL API](/en-US/docs/Web/API/WebGL_API) attaches either a fragment or
vertex {{domxref("WebGLShader")}} to a {{domxref("WebGLProgram")}}.

## Syntax

```js-nolint
attachShader(program, shader)
```

### Parameters

- `program`
  - : A {{domxref("WebGLProgram")}}.
- `shader`
  - : A fragment or vertex {{domxref("WebGLShader")}}.

### Return value

None ({{jsxref("undefined")}}).

## Examples

The following code attaches pre-existing shaders to a {{domxref("WebGLProgram")}}.

```js
const program = gl.createProgram();

// Attach pre-existing shaders
gl.attachShader(program, vertexShader);
gl.attachShader(program, fragmentShader);

gl.linkProgram(program);

if (!gl.getProgramParameter(program, gl.LINK_STATUS)) {
  const info = gl.getProgramInfoLog(program);
  throw new Error(`Could not compile WebGL program. \n\n${info}`);
}
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{domxref("WebGLProgram")}}
- {{domxref("WebGLShader")}}
- {{domxref("WebGLRenderingContext.compileShader()")}}
- {{domxref("WebGLRenderingContext.createProgram()")}}
- {{domxref("WebGLRenderingContext.createShader()")}}
- {{domxref("WebGLRenderingContext.deleteProgram()")}}
- {{domxref("WebGLRenderingContext.deleteShader()")}}
- {{domxref("WebGLRenderingContext.detachShader()")}}
- {{domxref("WebGLRenderingContext.getAttachedShaders()")}}
- {{domxref("WebGLRenderingContext.getProgramParameter()")}}
- {{domxref("WebGLRenderingContext.getProgramInfoLog()")}}
- {{domxref("WebGLRenderingContext.getShaderParameter()")}}
- {{domxref("WebGLRenderingContext.getShaderPrecisionFormat()")}}
- {{domxref("WebGLRenderingContext.getShaderInfoLog()")}}
- {{domxref("WebGLRenderingContext.getShaderSource()")}}
- {{domxref("WebGLRenderingContext.isProgram()")}}
- {{domxref("WebGLRenderingContext.isShader()")}}
- {{domxref("WebGLRenderingContext.linkProgram()")}}
- {{domxref("WebGLRenderingContext.shaderSource()")}}
- {{domxref("WebGLRenderingContext.useProgram()")}}
- {{domxref("WebGLRenderingContext.validateProgram()")}}
