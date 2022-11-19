# Portable SIMD

Rust provides a "portable" SIMD implementation, available in the [`std::simd` module](https://doc.rust-lang.org/std/simd/index.html).

## What is "portable"?

Compilers, including the Rust compiler, often implement SIMD in a few different ways.
To understand what "portable" means, let's explore the different implementations.

### Automatic Vectorization

One way that Rust makes use of SIMD is by an optimization called automatic vectorization.
Instead of using any special SIMD support in the Rust language, the compiler tries to identify regular Rust code that it can turn into SIMD operations.

This is a convenient optimization because the programmer doesn't need to do anything special to their code.
The downside is that the optimization only works in specific circumstances, since the compiler must be able to determine that it can split up a particular bit of code to run in parallel.

### Vendor Intrinsics

Hardware vendors provide special functions called _intrinsics_ which correspond to particular instructions or behavior.
In Rust, these are provded by the [`std::arch` module](https://doc.rust-lang.org/std/arch/index.html).

Using vendor intrinsics is a form of _explicit SIMD_, in which the programmer specifies exactly how the program is parallelized.
Vendor intrinsics also provide complete access to features available to a particular target architecture, offering the best potential for performance.
This capability comes at the cost of portability: code that uses vendor intrinsics will only work with that particular target.

More information about using vendor intrinsics is found in the next section.

### Portable SIMD

Rust's portable SIMD implementation offers a middle ground between automatic vectorization and vendor intrinsics.

Portable SIMD is another form of _explicit SIMD_ and allows the programmer to specify how the program is parallelized.
Unlike vendor intrinsics, portable SIMD works on all targets.
Rust's portable SIMD vector types provide the most common SIMD operations that perform well on most SIMD instruction sets.

In many cases, using portable SIMD can result in similar or identical compiled programs as the equivalent code using vendor intrinsics.
With portable SIMD, programmers have the ability to write intricate vectorized programs and be confident that their code will not just perform well, but will also act as expected on any target architecture.
Reaching for vendor intrinsics is often only necessary when taking advantage of an unusual feature provided by a specific target.
