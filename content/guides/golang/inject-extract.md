---
title: "Go: Inject and Extract (Under Construction)"
---

## Introduction

In order to trace across process boundaries and RPC calls in distributed systems, `spanContext` needs to propagated over the wire. The OpenTracing Go API provides two methods in the Tracer interface to do just that, `inject(SpanContext, format, carrier)` and `extract(format, carrier)`.

## Format Options and Carriers
The **format** parameter refers to one of the three standard encodings the OpenTracing API defines:

1. `TEXT_MAP` where `spanContext` is encoded as a collection of string key-value pairs,
2. `BINARY` where `spanContext` is encoded as an opaque byte array,
3. `HTTP_HEADERS`, which is similar to `TEXT_MAP` except that the keys must be safe to be used as HTTP headers.

The **carrier** is an abstraction over the underlying RPC framework. For example, a carrier for `TEXT_MAP` format is an interface that allows the tracer to write key-value pairs via `put(key, value)` method, while a carrier for `BINARY` format is simply a ByteBuffer.

## Injecting and Extracting HTTP
When your service calls a downstream service, it's useful to pass down the `SpanContext`, so that `Spans` generated by this service could join the Spans from our service in a single trace. To do that, our service needs to `Inject` the `SpanContext` into the payload. On the other side of the connection, the downstream service needs then to `Extract` the `SpanContext` before it creates any `Spans`.

#### Injecting the `spanContext` to HTTP
#### Extracting the Span’s Context from Incoming Request

## Injecting and Extracting TextMap

## Injecting and Extracting BINARY