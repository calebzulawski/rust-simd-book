# Summary

[Portable SIMD Programming in Rust](./0-title.md)

- [A quick introduction](./1-intro.md)
- [Portable SIMD](./2-portable-simd.md)
  - [Vectors](./2.1-vectors.md)
  - [Masks](./2.2-masks.md)
  - [Vendor Intrinsics](./2.3-vendor-intrinsics.md)
- [Target Features](./3-target-features.md)
  - [Program-wide with RUSTFLAGS](./3.1-rustflags.md)
  - [Runtime detection](./3.2-detection.md)
  - [The easy way, with `multiversion`](./3.3-multiversion.md)
- [Tips and tricks](./4-tricks.md)
  - [Inlining and target features](./4.1-inlining.md)
  - [Native vector width](./4.2-native-vector-width.md)
