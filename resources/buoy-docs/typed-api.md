---
title: "bundleinfo typed API"
summary: "Source-derived public signatures, properties, parameters, defaults, and return values."
category: "Reference"
order: 21
types: ["BundleSnapshot"]
dependencies: []
symbols: ["BundleSnapshot"]
related: ["api.md", "getting-started.md", "index.md"]
---

# bundleinfo typed API

Generated from the package source declarations. Platform guards are shown where present; inherited members are documented on the base type. See the [API contracts](api.md) for behavior and limitations.

## BundleInfo functions

### BundleInfoSupported

`Public Function BundleInfoSupported() As Boolean`

No parameters.

#### Returns

| Type |
| --- |
| `Boolean` |

## BundleSnapshot

`Public Class BundleSnapshot`

### Properties

| Name | Type | Read-Only | Shared | Default | Description |
| --- | --- | --- | --- | --- | --- |
| `Path` | `String` | Yes | No | — | — |
| `Identifier` | `String` | Yes | No | — | — |
| `Name` | `String` | Yes | No | — | — |
| `Version` | `String` | Yes | No | — | — |
| `Build` | `String` | Yes | No | — | — |

### Constructor

`Public Sub Constructor(filePath As String = "")`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `filePath` | `String` | `ByVal` | `""` |

Returns: no value.

### Resource

`Public Function Resource(name As String, fileExtension As String = "") As Optional Of FileSystemItem`

#### Parameters

| Name | Type | Passing | Default |
| --- | --- | --- | --- |
| `name` | `String` | `ByVal` | Required |
| `fileExtension` | `String` | `ByVal` | `""` |

#### Returns

| Type |
| --- |
| `Optional Of FileSystemItem` |
