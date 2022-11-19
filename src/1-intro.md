# A quick introduction

SIMD is short for *single instruction, multiple data*.
As the name suggests, a single SIMD instruction can operate on multiple data values simultaneously.
This type of parallelism can speed up programs, and comes with much lower overhead and complexity than other types of parallelism, such as concurrency.

Consider the following function:

```rust
fn add_array(a: [f32; 4], b: [f32; 4]) -> [f32; 4] {
    [
        a[0] + b[0],
        a[1] + b[1],
        a[2] + b[2],
        a[3] + b[3],
    ]
}
```

Without SIMD, each array element is computed separately.  On x86-64, this instruction is `addss`:

<center>

```svgbob
      .------.   .------.   .------.
addss | a[0] | + | b[0] | = | c[0] |
      '------'   '------'   '------'
      .------.   .------.   .------.
addss | a[1] | + | b[1] | = | c[1] |
      '------'   '------'   '------'
      .------.   .------.   .------.
addss | a[2] | + | b[2] | = | c[2] |
      '------'   '------'   '------'
      .------.   .------.   .------.
addss | a[3] | + | b[3] | = | c[3] |
      '------'   '------'   '------'
```
</center>

With SIMD, however, all 4 array elements can be computed with a single instruction!  On x86-64, this instruction is `addps`:

<center>

```svgbob
      .------.   .------.   .------.
      | a[0] |   | b[0] |   | c[0] |
      +------+   +------+   +------+
      | a[1] |   | b[1] |   | c[1] |
addps +------+ + +------+ = +------+
      | a[2] |   | b[2] |   | c[2] |
      +------+   +------+   +------+
      | a[3] |   | b[3] |   | c[3] |
      '------'   '------'   '------'
```
</center>

SIMD operations make use of special _vector_ registers to perform operations on multiple values at once.
The elements of these vectors are also known as _lanes_.
