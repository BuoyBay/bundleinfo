# Bundle identity and resources

See the [installation and complete usage example](resources/buoy-docs/getting-started.md) for an availability guard and optional resource lookup, or the [API reference](resources/buoy-docs/api.md) for metadata and error behavior.

`Import bundleinfo`. `New BundleSnapshot(bundlePath = "")` reads the main bundle or another bundle without loading executable code. Read-only `Path`, `Identifier`, `Name`, `Version`, and `Build`. `Resource(name, fileExtension = "")` returns `Optional Of FileSystemItem`; missing resources are None. Resource names cannot contain path separators. Snapshot strings are copied; no native object escapes the operation.

## Install

From a Buoy consumer project with BPM installed:

```sh
bpm add bundleinfo --git https://github.com/BuoyBay/bundleinfo.git --rev refs/heads/main
```

BPM records the resolved commit in its lockfile. Keep that lockfile with the
consumer project for reproducible installs.

## Example

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

## Build from source

With the native `build-packages` driver from [devtools](https://github.com/BuoyBay/devtools)
on your `PATH`, run from this checkout:

```sh
build-packages --root "$PWD" --compile-consumer bundleinfo
```

The driver checks source targets and compiles an import consumer. See the
[API guide](docs/API.md) for behavior, limits and any host prerequisites.

## Contributing

[Contributing](CONTRIBUTING.md) · [License](LICENSE)
