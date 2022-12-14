# Target Features

For many architectures, SIMD support is an optional CPU feature.
Rust supports enabling a variety of these "target features".

To view a list of features supported by a target, run:

```bash
rustc --print target-features
```

To view a list of CPUs supported by a target, run:

```bash
rustc --print target-cpus
```

This list of target features is also available in the documentation for the [`target-features` crate](https://docs.rs/target-features/latest/target_features/docs/index.html).

The following sections will address different approaches to enabling these target features.
