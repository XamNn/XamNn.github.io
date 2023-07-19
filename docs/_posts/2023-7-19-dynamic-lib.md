---
title: "Dynamic Rust Library"
author: "Samuel Kriikkula"
---

Hello there! Today I will show you how to make dynamic rust libraries and call functions dynamically!

## Create the dynamic library
Initialize a rust library:
```
$ cargo new dynamic_lib --lib
```

Edit *Cargo.toml*:
```toml
[package]
name = "dynamic_lib"
version = "0.1.0"
edition = "2021"

[lib]
crate-type=["dylib"]

# See more keys and their definitions at https://doc.rust-lang.org/cargo/reference/manifest.html

[dependencies]
```

## Write a function
Delete the contents of *src/lib.rs*.  
Edit *src/lib.rs*:
```rust
#[no_mangle]
pub fn add(x: usize, y: usize) -> usize {
    x + y
}
```

## Build
```
cargo build --release
```
The library is found in *target/release* and will be named *libdynamic_lib.so*, *dynamic_lib.dll*, or *libdynamic_lib.dylib* depending on the platform.

## Call from rust
We use the **libloading** crate.  
Edit the caller crates *Cargo.toml*:
```toml
[dependencies]
...
libloading = "0.8"
```

Add this code to call a dynamic function:
```rust
unsafe {
    let lib = libloading::Library::new("/home/samuel/Code/Own/Tests/dynamic_lib/target/release/libdynamic_lib.so").unwrap();
    let func: libloading::Symbol<fn(usize, usize) -> usize> = lib.get(b"add").unwrap();
    println!("{}", func(1, 2));
    // output: 3
}
```
