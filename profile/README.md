<div align="center">

# z-libs: Building the Future of C

[![Sponsor](https://img.shields.io/static/v1?label=Sponsor&message=%E2%9D%A4&logo=GitHub&color=%23fe8e86)](https://github.com/sponsors/Zuhaitz-dev) [![Discord](https://img.shields.io/discord/1460350343966887970?label=Discord&logo=discord&color=5865F2)](https://discord.com/invite/q6wEsCmkJP)

> Home of the **Zen C** programming language.

**z-libs** is an organization dedicated to modernizing systems programming. We believe C is the perfect foundation, but it needs modern ergonomics. Whether through our compiled language **Zen C** or our classic header-only libraries, our mission is the same:
<br>
**Zero Overhead. Maximum Productivity.**

</div>

---

## Zen C

**[Zen C](https://github.com/z-libs/Zen-C)** is a compiled systems language that seamlessly extends C11. It isn't just a wrapper; it's a full language toolchain designed to make C development joyful again.

### Why Zen C?

*   **Modern Syntax**: Type inference (`let`), Pattern Matching (`match`), and Traits (`impl`).
*   **Zero cost**: Compiles to standard, human-readable C11. No heavy runtime.
*   **Memory Safety Options**: Manual memory management with `defer`, `autofree`, and strict **Move Semantics** by default.
*   **Universal Binaries**: Compiles to **APE** (Actually Portable Executable) format—build once, run anywhere.
*   **Seamless Interop**:
    *   **C++ Mode**: Compiles to C++ to use libraries like `<vector>` or OpenCV.
    *   **CUDA Support**: Write GPU kernels directly in Zen C syntax.
    *   **Objective-C linkage**: Build native macOS apps with Cocoa.

```zc
import "std/vec.zc"
import "std/net.zc"

struct User { id: int; name: string; }

async fn fetch_user(id: int) -> User {
    // Async/Await syntax built on native pthreads/coroutines
    return User{id: id, name: "Alice"};
}

fn main() {
    let users = Vec<User>::new();
    
    match fetch_user(101) |> await {
        User(id, name) => println "Got user: {name}", // Pattern destructuring
        _              => println "Failed"
    }
}
```

<div align="center">

[**Explore the Language**](https://github.com/z-libs/Zen-C)

</div>

---

## Classic C Libraries (z-libs)

Before Zen C, we built the **z-libs** suite: a collection of single-header C11 libraries that bring C++ container convenience to pure C. These are stable, battle-tested, and fully interoperable.

| Library | Description | Features | Status |
| :--- | :--- | :--- | :--- |
| **[zvec](https://github.com/z-libs/zvec.h)** | Type-safe dynamic arrays | Full C++ Wrapper | Stable |
| **[zstr](https://github.com/z-libs/zstr.h)** | SSO-optimized strings & views | C++ Wrapper, Lua Bindings | Stable |
| **[zmap](https://github.com/z-libs/zmap.h)** | Open-addressing hash maps | Full C++ Wrapper | Stable |
| **[zlist](https://github.com/z-libs/zlist.h)** | Doubly-linked lists | Full C++ Wrapper | Stable |
| **[zalloc](https://github.com/z-libs/zalloc.h)** | Arenas, Pools, and Leak Detection | Zero-overhead, Cache-friendly | Stable |

<br>

### The "Bridge" Philosophy

Most libraries force you to choose a side. **z-libs** lets you cross the border freely.

#### 1. Works perfectly in C11
Full control, no hidden allocations, type-safe macros.

```c
// zvec: Dynamic Arrays
vec(int) scores = vec_init(int);
vec_push(&scores, 10);
```

#### 2. And the SAME headers work natively in C++
RAII, methods, iterators, and `std::` compatibility.

```cpp
// z_vec: Wrapper around vec_int
z_vec::vector<int> scores = {10, 42};
```

#### 3. Scripting Ready (Lua)
High-performance mutable buffers for scripts to avoid garbage collection churn.

```lua
local zstr = require("zstr")
local buf = zstr.new("Start: ")
```

<details>
<summary><b>Click to see more reasons "Why z-libs?"</b></summary>

Most C container libraries suffer from **Macro Hell** (cryptic errors), **void\* soup** (no type safety), or **Build System Fatigue** (requiring CMake/Make just to use a vector).

**z-libs** solves this by using modern C11 features (`_Generic`) for the implementation while providing a "feels-like-native" C++ layer on top.

* **Zero external dependencies**: Standard C library only.
* **Truly single-header**: Just drop the file in your project.
* **Allocator-aware**: Use **zalloc.h** (arenas, pools) or your custom heaps.
* **Universal**: Compiles on GCC, Clang, MSVC, and tiny microcontrollers.

</details>

---

## The Zen Ecosystem

It's not just a language; it's a complete toolkit.

*   **LSP (Language Server)**: Go-to-definition, hover docs, and autocompletion for VS Code / Neovim.
*   **REPL**: Interactive shell for rapid prototyping and testing.
*   **Build System**: Zero-config compilation. Just `zc run main.zc`.

---

<div align="center">

## Meet Zibi

<img src="https://raw.githubusercontent.com/z-libs/.github/main/profile/zibi.svg" width="200" alt="Zibi the Ogre">

<br>

**Zibi is the tiny green ogre that guards your memory.**
<br>
He started life as a random GitHub identicon, reminded us of an ogre, and became the official mascot.

| **Zibi Likes** | **Zibi Hates** |
| :--- | :--- |
| **Zen C** (obviously) | `void*` casting |
| Single-header libraries | Segfaults |
| Stack allocation (SSO) | Garbage Collection pauses |
| Onions (layers!) | Complex build scripts |

<br>
<i>If your code compiles and runs on the first try, Zibi is happy.</i>

</div>

---

## License

All projects under z-libs use the **MIT License**. Free to use, modify, and distribute for personal and commercial projects.

