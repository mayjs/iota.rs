# IOTA Shared(Dynamic) Library

This crates provides bindings to create a shared library which is compatible to the system ABI. This means the library can be included into a C codebase, and even more if other languages can use what ABI system provides. Usually cargo can generate the library simply through `cargo build` and the build will be right under `target/debug/libiota.so`. If you need a release build, pass `cargo build --release` and it will be `target/release/libiota.so`. After that users can import it directly and write extern functions. We will provide well-documented header files generated by `cbindgen` in the future. For now the example of usage is in `src/main.c`. We want the API to be similar to current `iota.c` and be more ergonimic. So the interface might also change later, but you should know how it works.

## Quick Start

Since the build targets are all produced in the `target` directory. We put the `Makefile` at the root of the workspace which is upper layer of this README. Make sure you are in the same path of `Makefile` and then simply enter:

```
make
```

What it does is building the shared library and C main file as example and run it. The C source file has been documented, each extern functions from the shared library all have their own documentations. If you are curious about performance, here's [benchmark](documentation/benchmark.md) result we tested on both C and Rust.