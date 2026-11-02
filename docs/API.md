# Bundle metadata and resources · 0.1.0

See the [installation and complete usage example](../resources/buoy-docs/getting-started.md) for an availability guard and optional resource lookup, or the [API reference](../resources/buoy-docs/api.md) for metadata and error behavior.

`Import bundleinfo`. `New BundleSnapshot(bundlePath = "")` reads the main bundle or another bundle without loading executable code. Read-only `Path`, `Identifier`, `Name`, `Version`, and `Build`. `Resource(name, fileExtension = "")` returns `Optional Of FileSystemItem`; missing resources are None. Resource names cannot contain path separators. Snapshot strings are copied; no native object escapes the operation.

These native operations require macOS. `BundleInfoSupported()` returns False on Windows/Linux, and unsupported operations throw.

Inspired by [macoslib’s Cocoa examples](https://github.com/macoslib/macoslib); implemented independently against [Apple’s API](https://developer.apple.com/documentation/foundation/bundle).
