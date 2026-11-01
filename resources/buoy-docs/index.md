---
title: "Bundle information"
summary: "Read application bundle identity, versions, and resource locations without loading code."
category: "Overview"
order: 0
keywords: ["bundleinfo", "macOS", "native"]
related: ["getting-started.md", "api.md", "typed-api.md"]
---

# Bundle information

Use `bundleinfo` for About panels, bundle diagnostics, and locating a named resource in the main application or another macOS bundle. `BundleSnapshot` copies metadata strings and exposes no native object to the caller.

## Platform availability

macOS is required. `BundleInfoSupported()` is false on Windows and Linux; constructors and resource lookups throw `UnsupportedOperationException` there.

## Package use

Install `bundleinfo-0.1.0.buipkg` in the consumer project's `packages/` directory, then use `Import bundleinfo`. This package is independently sealed; it does not require importing the other desktop integration packages.

## Behavior and lifetime

A valid bundle may have empty identifier, version, or build metadata. Display name falls back from `CFBundleDisplayName` to `CFBundleName`. Resource names and extensions cannot contain path separators or equal `..`; resource names must be nonempty valid text. An invalid bundle path raises `InvalidArgumentException`. The snapshot needs no explicit close.
## Continue reading

- [Overview](index.md)
- [Getting started](getting-started.md)
- [API reference](api.md)
