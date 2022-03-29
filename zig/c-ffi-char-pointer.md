{
  "title": "Zig to C char pointer",
  "categories": ["ffi", "C"],
  "keywords": ["pointer", "mutable"]
}
---
# Convert Zig string to mutable C pointer

Imagine this C interface:

```c
int putenv(char *string);
```

If we want to call it from Zig we would do:

```zig
const c = @cImport({
    @cInclude("stdlib.h");
});

test "call putenv from Zig" {
    var env_var = "MY_ENV_VAR=value".*;
    _ = c.putenv(&env_var);
}
```

The `MY_ENV_VAR=value` Zig string will be static in the data section of the
binary. By calling `.*` to derefernce it we create a mutable copy into
`env_var`. It's importaht that `env_var` is a `var` and not `const` because
`putenv` requires a `char *` and NOT a `const char*`.

Finally, after making a mutable copy of our string on the stack, we get a
pointer to it with `&` to pass into the C function.
