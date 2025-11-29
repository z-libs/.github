# z-libs: Modern single-header libraries for C

Zero-dependency • Header-only • C11 • Type-safe • Allocator-aware • No macro hell for the developer

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

## The libraries

| Library     | Description                                           | Key features                                                |
|-------------|-------------------------------------------------------|-------------------------------------------------------------|
| [zvec.h](https://github.com/z-libs/zvec.h)    | Growable vectors (like std::vector)                   | O(1) swap-remove, built-in sort/search, custom allocators   |
| [zstr.h](https://github.com/z-libs/zstr.h)    | Modern UTF-8 strings (like std::string)               | 22-byte SSO, views, formatting, split, zero-copy slicing    |
| [zlist.h](https://github.com/z-libs/zlist.h)   | Doubly-linked lists                                   | Non-intrusive, safe iteration, O(1) splice                  |
| [zmap.h](https://github.com/z-libs/zmap.h)    | Open-addressing hash tables (like std::unordered_map) | Linear probing, FNV-1a, cache-friendly, custom allocators   |

All libraries share the same philosophy:

- Zero external dependencies  
- Truly single-header (just drop the file in your project)  
- Full type safety through _Generic + X-macros  
- Per-container custom allocator support (arenas, pools, etc.)  
- No hidden global or thread-local state  
- Works everywhere: gcc, clang, msvc, tcc, any C11+ compiler  

## Quick start

Clone each one of the repositories. Then simply use the header files you want. They are independent.

> A repository will soon be available as a suite that contains all header files.

## Why another C container collection?

Most existing solutions suffer from at least one of these problems:

- Heavy use of void* → endless casts, no type safety  
- Macro hell → cryptic errors and unhappy IDEs  
- Require a build system or external dependencies  
- Haven’t evolved since the early 2000s  

z-libs gives you modern ergonomics while staying pure C: you keep full control over memory, compilation remains instant, and everything still runs on the smallest microcontrollers.

## Meet Zibi

Zibi is the tiny green ogre that guards your containers.

He started life as a random GitHub identicon, reminded us of an ogre, and became the official mascot.

Zibi likes:
- single-header libraries
- type safety
- onions (because C macros have layers)

Zibi hates:
- void*
- build systems
- segfaults

If your code compiles and runs on the first try, Zibi is happy.

## Coming soon

This is a growing project. New libraries will come often. Benchmarks will be made too.

## License

The whole project uses the MIT license.






