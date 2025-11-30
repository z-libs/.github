# z-libs: Modern single-header libraries for C

Zero-dependency • Header-only • C11 • Type-safe • Allocator-aware • **C++ Compatible***

**z-libs** is a collection of single-header container libraries. They are written in pure C for maximum portability but include zero-cost C++ wrappers for modern developer ergonomics.

These libraries allow you to write standard C11 code with full control over memory, or drop them into a C++ project to utilize RAII, move semantics, and range-based loops without any performance overhead.

- Works perfectly in C:

```c
vec_int scores = vec_init(int);
vec_push(&scores, 10);
vec_push(&scores, 42);

zstr name = zstr_lit("Ada");
zstr_fmt(&name, " %s", "Lovelace");   // -> "Ada Lovelace"

map_ages ages = map_init();
map_put(&ages, zstr_lit("Ada"), 36);
map_put(&ages, zstr_lit("Grace"), 85);

int *val = map_get(&ages, zstr_lit("Grace"));
if (val) printf("Age: %d\n", *val);   // -> Age: 85
```

- And the same headers can be used in C++:

```cpp
z_str::string name = "Ada";
name += " Lovelace";  // RAII handles memory

// Range-based loops & Views
for (auto part : name.split(" ")) {
    std::cout << part << "\n";
}
```

> *C++ support is currently only available for `zstr.h`, but we are working on the other libraries.

## The libraries

| Library     | Description                                           | Key features                                                |
|-------------|-------------------------------------------------------|-------------------------------------------------------------|
| [zvec.h](https://github.com/z-libs/zvec.h) | Growable vectors (like std::vector) | O(1) swap-remove, built-in sort/search, custom allocators |
| [zstr.h](https://github.com/z-libs/zstr.h) | Modern strings | 23-byte SSO, **full C++ wrapper**, views, split, zero-copy slicing |
| [zlist.h](https://github.com/z-libs/zlist.h) | Doubly-linked lists | Non-intrusive, safe iteration, O(1) splice |
| [zmap.h](https://github.com/z-libs/zmap.h) | Open-addressing hash tables (like std::unordered_map) | Linear probing, FNV-1a, cache-friendly, custom allocators |

## Philosophy

All libraries share the same DNA:

* **Zero external dependencies**: Standard C standard library only.
* **Truly single-header**: Just drop the file in your project.
* **Dual API**: 
    * **C**: Full control, no allocations hidden from you.
    * **C++**: RAII, Move Semantics, Iterators, and `std::string_view` compatibility.
* **Type safety**: Generics via macros (C) or Templates (C++).
* **Allocator-aware**: Support for arenas, pools, and custom heaps.
* **Universal**: Compiles on gcc, clang, msvc, and tiny microcontrollers.

## Quick start

Clone each one of the repositories. Then simply use the header files you want. They are independent.

> A repository will soon be available as a suite that contains all header files.

## Why another C container collection?

Most C container libraries suffer from **Macro Hell** (cryptic errors), **void\* soup** (no type safety), or **Build System Fatigue** (requiring CMake/Make/etc just to use a vector).

**z-libs** solves this by using modern C11 features for the implementation while providing a "feels-like-native" C++ layer on top. You get the raw performance and portability of C with the safety and convenience of C++.

## Meet Zibi

Zibi is the tiny green ogre that guards your memory.

He started life as a random GitHub identicon, reminded us of an ogre, and became the official mascot.

**Zibi likes:**
* Single-header libraries.
* Stack allocation (SSO).
* Onions (because C macros have layers).

**Zibi hates:**
* `void*` casting.
* Segfaults.
* Complex build scripts.

If your code compiles and runs on the first try, Zibi is happy.

![Zibi](zibi.svg)

## Coming soon

This is a growing project. New libraries will come often. Benchmarks will be made too.

## License

The whole project uses the **MIT License**.








