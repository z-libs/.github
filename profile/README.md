# z-libs — Modern single-header libraries for C

Zero-dependency • Header-only • C11 • Type-safe • Allocator-aware • No macro hell for the developer

```c
zvec(int) scores = {0};
vec_push(&scores, 10);
vec_push(&scores, 42);

zstr name = zstr_lit("Ada");
zstr_fmt(&name, " %s", "Lovelace");        // -> "Ada Lovelace"

zmap(zstr, int) ages = {0};
map};
map_put(&ages, zstr_lit("Ada"), 36);
map_put(&ages, zstr_lit("Grace"), 85);

printf("%d\n", *map_get(&ages, zstr_lit("Grace")));  // -> 85
```

## The libraries

| Library     | Description                                           | Key features                                                |
|-------------|-------------------------------------------------------|-------------------------------------------------------------|
| [zvec.h]    | Growable vectors (like std::vector)                   | O(1) swap-remove, built-in sort/search, custom allocators   |
| [zstr.h]    | Modern UTF-8 strings (like std::string)               | 22-byte SSO, views, formatting, split, zero-copy slicing    |
| [zlist.h]   | Doubly-linked lists                                   | Non-intrusive, safe iteration, O(1) splice                  |
| [zmap.h]    | Open-addressing hash tables (like std::unordered_map) | Linear probing, FNV-1a, cache-friendly, custom allocators   |

All libraries share the same philosophy:

- Zero external dependencies  
- Truly single-header (just drop the file in your project)  
- Full type safety through _Generic + X-macros  
- Per-container custom allocator support (arenas, pools, etc.)  
- No hidden global or thread-local state  
- Works everywhere: gcc, clang, msvc, tcc, any C11+ compiler  

## Quick start

```bash
git clone https://github.com/z-libs/z-libs.git
cd z-libs```
```

Then simply use the header files you want. They are independent.

## Why another C container collection?

Most existing solutions suffer from at least one of these problems:

- Heavy use of void* → endless casts, no type safety  
- Macro hell → cryptic errors and unhappy IDEs  
- Require a build system or external dependencies  
- Haven’t evolved since the early 2000s  

z-libs gives you modern ergonomics while staying pure C: you keep full control over memory, compilation remains instant, and everything still runs on the smallest microcontrollers.

## Coming soon

This is a growing project. New libraries will come often. Benchmarks will be made too.

## License

The whole project uses the MIT license.
