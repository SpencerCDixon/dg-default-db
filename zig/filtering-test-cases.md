{
  "title": "Filtering test cases",
  "categories": ["test", "debug"],
  "keywords": ["filter", "cli"]
}
---
# Filtering test cases with `zig test`

TLDR: Use the `--test-filter` flag with `zig test`

```zig
// src/main.zig
const std = @import("std");

test "add" {
  std.testing.expectEqual(1 + 1, 2);
}

test "multiply" {
  std.testing.expectEqual(2 * 2, 4);
}
```

To run just the `multiply` test we can use:

```bash
$ zig test src/main.zig --test-filter "multiply"
```

> NOTE: Make sure you're running `zig test` and not `zig build test` which 
>       gets auto generated when you run `zig init-exe`.
