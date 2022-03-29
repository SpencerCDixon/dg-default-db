{
  "title": "How to set a breakpoint",
  "categories": ["debug"],
  "keywords": ["breakpoint", "set"]
}
---
# How to set a breakpoint

There is a compiler `builtin` which will set a platform specific breakpoint
useful for debugging. Note, they must be set inside function scope.

```zig
pub fn do_thing() void {
  @breakpoint();
  // more things
}

test "hit a breakpoint" {
  do_thing();
}
```
