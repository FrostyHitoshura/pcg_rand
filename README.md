pcg_rand
========

[![Crates.io Version](https://img.shields.io/crates/v/pcg_rand.svg)](https://crates.io/crates/pcg_rand)
[![](https://docs.rs/pcg_rand/badge.svg)](https://docs.rs/pcg_rand/)
![License](https://img.shields.io/crates/l/rustc-serialize.svg)

To use this library add the following to your `Cargo.toml`

```
pcg_rand = "0.9.0"
```

PCG stands for Permuted Congruential generators. They are a simple family of
random number generators which use the much denounced Linear Congruential
Generator as a base. To overcome the well known limitations of the LCG Generator
the PCG family utilizes permutation functions to permute the output. More
information about PCG can be found [here](http://pcg-random.org).

Current Status
--------------
This library currently provides 32 and 64 bit generators. 
It provides the major "stream" types, including the unique stream which is determined
by their current location in memory. 

Future Work
-----------

* Implement seeking for the generators

Changes
-------
 * (6/8/2016): Added support for extended generators. This implementation
 is based on my understanding of how the extension is specified in the paper. 
 I would love a code review on the implementation. I don't think that this 
 particular implementation is the same as the implementation in the C++ version
 of PCG.
 * (6/7/2016): Added back some of the macros which got removed in 0.5.0
 This is in an effort to improve some performance. Hopefully associated constants
 can help us remove these again, but for now removing the PcgConsts trait gives
 some extra performance and reduces indirection. It also means that it is now
 easier to implement new streams and multipliers because you aren't bound
 to using the three things in PcgConsts.
 * (7/31/2018): Remembered to update the README (including changelog). Migrated
 to using the `rand: 0.5` crate which involves new methods. Most of the functions
 are now not based on macro's but instead are fully generic and utilize the 
 `num-traits` wrapping traits as needed. Additionally the crate now has support
 for using the native `u128` since that is stable in Rust now. This pushes the 
 minimum Rust version to 1.26. 
