---
title: "Bundle information getting started"
summary: "Install and use bundleinfo with an availability check and a complete example."
category: "Guides"
order: 10
keywords: ["bundleinfo", "install", "example"]
related: ["index.md", "api.md", "typed-api.md"]
---

# Getting started

## Install and import

Copy the sealed `bundleinfo-0.1.0.buipkg` archive into your application's `packages/` folder.

## First use

Create a snapshot with no argument for the main bundle, or pass a bundle directory path. The operation does not load that bundle's executable. Read the copied properties, then call `Resource` for a simple resource name and optional extension. An absent resource returns `None`.

```basic
Import bundleinfo

Sub Main()
    If Not BundleInfoSupported() Then
        Print "Bundle information requires macOS."
        Return
    End If
    Dim bundle As New BundleSnapshot()
    Print bundle.Name
    Print bundle.Identifier
    Print bundle.Version
    Dim resource As Optional Of FileSystemItem = bundle.Resource("help", "txt")
    If resource.HasValue Then Print resource.Value.FullPath()
End Sub
```

The example checks backend availability before invoking macOS-only operations. It does not catch input or access failures; catch exceptions at your application boundary and present a useful message to the user.

## Platform and error handling

macOS is required. `BundleInfoSupported()` is false on Windows and Linux; constructors and resource lookups throw `UnsupportedOperationException` there. A valid bundle may have empty identifier, version, or build metadata. Display name falls back from `CFBundleDisplayName` to `CFBundleName`. Resource names and extensions cannot contain path separators or equal `..`; resource names must be nonempty valid text. An invalid bundle path raises `InvalidArgumentException`. The snapshot needs no explicit close.
## Continue reading

- [Overview](index.md)
- [Getting started](getting-started.md)
- [API reference](api.md)
