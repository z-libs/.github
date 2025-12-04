# z-libs: Modern single-header libraries for C/C++

> Zero-dependency • Header-only • C11 - C++11/C++17 • Type-safe • Lua Bindings

**z-libs** is a collection of single-header container libraries. They are written in pure C for maximum portability but include zero-cost C++ wrappers for modern developer ergonomics.

These libraries allow you to write standard C11 code with full control over memory, drop them into a C++ project to utilize RAII and range-based loops, or expose them to scripting languages like Lua without performance loss.

### The "Bridge" Philosophy

Most libraries force you to choose a side. **z-libs** lets you cross the border freely.

**1. Works perfectly in C11:**
Full control, no hidden allocations, type-safe macros.

```c
// zvec: Dynamic Arrays
vec_int scores = vec_init(int);
vec_push(&scores, 10);

// zstr: SSO Strings
zstr name = zstr_lit("Ada");
zstr_fmt(&name, " %s", "Lovelace");

// zmap: Hash Maps
map_ages ages = map_init(ages);
map_put(&ages, "Grace", 85);
```

**2. And the SAME headers work natively in C++:**
RAII, methods, iterators, and `std::` compatibility.

```cpp
// z_vec: Wrapper around vec_int
z_vec::vector<int> scores = {10, 42};

// z_map: Wrapper around map_ages
z_map::map<std::string, int> ages;
ages.put("Grace", 85);

// z_str: Wrapper around zstr
z_str::string name = "Ada";
for (auto part : name.split(" "))
{
    std::cout << part << "\n";
}
```

**3. Scripting Ready (Lua):**
High-performance mutable buffers for scripts to avoid garbage collection churn.

```lua
local zstr = require("zstr")
local buf = zstr.new("Start: ")

-- Efficient appending (no intermediate garbage).
buf:append("User=", "Alice", " ID=", tostring(101))
buf:upper()

print(tostring(buf)) -- "START: USER=ALICE ID=101"
```

## The Libraries

| Library | Description | Features | Status |
| :--- | :--- | :--- | :--- |
| **[zvec](https://github.com/z-libs/zvec.h)** | Type-safe dynamic arrays | Full C++ Wrapper | Stable |
| **[zstr](https://github.com/z-libs/zstr.h)** | SSO-optimized strings & views | C++ Wrapper, Lua Bindings | Stable |
| **[zmap](https://github.com/z-libs/zmap.h)** | Open-addressing hash maps | Full C++ Wrapper | Stable |
| **[zlist](https://github.com/z-libs/zlist.h)** | Doubly-linked lists | Full C++ Wrapper | Stable |
| **[zalloc](https://github.com/z-libs/zalloc.h)** | Arenas, Pools, and Leak Detection | Zero-overhead, Cache-friendly | Stable |

## Quick Start

The libraries are designed to be modular. You can grab just one, or use them all together.

### Option A: The Suite (Recommended)

Use **[z-core](https://github.com/z-libs/z-core)** tools to manage type generation automatically.

```bash
git submodule add https://github.com/z-libs/zvec.git
git submodule add https://github.com/z-libs/zstr.git
git submodule add https://github.com/z-libs/z-core.git
```

### Option B: Drag and Drop

Since they are header-only and zero-dependency, you can simply download `zvec.h` or `zstr.h` and drop them into your `include/` folder.

## Why z-libs?

Most C container libraries suffer from **Macro Hell** (cryptic errors), **void\* soup** (no type safety), or **Build System Fatigue** (requiring CMake/Make just to use a vector).

**z-libs** solves this by using modern C11 features (`_Generic`) for the implementation while providing a "feels-like-native" C++ layer on top.

* **Zero external dependencies**: Standard C library only.
* **Truly single-header**: Just drop the file in your project.
* **Allocator-aware**: Use **zalloc.h** (arenas, pools) or your custom heaps.
* **Universal**: Compiles on GCC, Clang, MSVC, and tiny microcontrollers.

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

![Zibi](https://raw.githubusercontent.com/z-libs/.github/main/profile/zibi.svg)

## License

The whole project uses the **MIT License**.








