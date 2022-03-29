{
  "title": "Detect if building for tests",
  "categories": ["test", "debug"],
  "keywords": ["build", "comptime"]
}
---

# Detect if in 'test' build mode

Use the `builtin` primitives:

```zig
const inTest = @import("builtin").is_test;

pub fn myFunc() void {
  if (inTest) {
    std.debug.print("in test mode\n", .{});
  } 
}
```
