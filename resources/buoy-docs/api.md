---
title: "Bundle information API"
summary: "Public bundleinfo types and operations with behavior and lifetime notes."
category: "Reference"
order: 20
keywords: ["bundleinfo", "API", "reference"]
symbols: ["BundleInfoSupported", "BundleSnapshot", "BundleSnapshot.Resource", "BundleSnapshot.Identifier", "BundleSnapshot.Name", "BundleSnapshot.Version", "BundleSnapshot.Build"]
related: ["index.md", "getting-started.md", "typed-api.md"]
---

# API reference

`Import bundleinfo` exposes the following public API. Properties described as read-only have no public setter.

| Symbol | Behavior |
| --- | --- |
| `BundleInfoSupported() As Boolean` | Reports whether the macOS backend is available. |
| `BundleSnapshot(filePath As String = "")` | Read the main bundle when the path is empty; otherwise read the supplied bundle. |
| `BundleSnapshot.Path As String` | Read-only native bundle path. |
| `BundleSnapshot.Identifier As String` | Read-only CFBundleIdentifier. |
| `BundleSnapshot.Name As String` | Read-only display name with bundle-name fallback. |
| `BundleSnapshot.Version As String` | Read-only short version string. |
| `BundleSnapshot.Build As String` | Read-only build version string. |
| `BundleSnapshot.Resource(name, fileExtension = "") As Optional Of FileSystemItem` | Resolve a simple resource name; None means it was not found. |

## Errors and availability

macOS is required. `BundleInfoSupported()` is false on Windows and Linux; constructors and resource lookups throw `UnsupportedOperationException` there. A valid bundle may have empty identifier, version, or build metadata. Display name falls back from `CFBundleDisplayName` to `CFBundleName`. Resource names and extensions cannot contain path separators or equal `..`; resource names must be nonempty valid text. An invalid bundle path raises `InvalidArgumentException`. The snapshot needs no explicit close.
## Continue reading

- [Overview](index.md)
- [Getting started](getting-started.md)
- [API reference](api.md)

[Full typed API: properties, parameters, defaults, and returns](typed-api.md)
