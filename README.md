# @tummycrypt/tinyland-prometheus (retired)

> **Retired 2026-10-10.** This package was merged into
> [xoxd-ai/tinyland-otel](https://github.com/xoxd-ai/tinyland-otel) as the
> `./prometheus` subpath export, shipped in `tummycrypt_tinyland_otel` 1.4.0 and
> later. This repository is archived and gets no further changes.

## Migration

- Bazel: remove `bazel_dep(name = "tummycrypt_tinyland_prometheus", ...)` and
  depend on `bazel_dep(name = "tummycrypt_tinyland_otel", version = "1.4.0")`
  (or later) from [xoxd-ai/bazel-registry](https://github.com/xoxd-ai/bazel-registry).
- Imports: change `@tummycrypt/tinyland-prometheus` to
  `@tummycrypt/tinyland-otel/prometheus`. The API is the same
  (`MetricsRegistry`, `metricsRegistry`, `incrementCounter`, `setGauge`,
  `observeHistogram`, `exportMetrics`, and the types `Metric`,
  `HistogramBucket` and `HistogramMetric`).
- The otel package root also re-exports the same names unchanged, and the root
  and the subpath share one `metricsRegistry` singleton.
- There is no behavior change: the sources were moved byte for byte.

## Distribution

Bazel is the only distribution path for in-house packages. Nothing is published
to npm from this repository any more, and the publish workflow has been removed.
The Bazel module `tummycrypt_tinyland_prometheus` (0.2.2, 0.2.3) is marked
deprecated in the registry but stays resolvable; nothing is yanked. Earlier npm
releases of `@tummycrypt/tinyland-prometheus` remain on the npm registry.

## What it was

An in-process, Prometheus-compatible metrics registry with counters, gauges and
histograms (label sets, configurable histogram buckets), and an exporter that
renders the Prometheus text exposition format for a `/metrics` endpoint.
