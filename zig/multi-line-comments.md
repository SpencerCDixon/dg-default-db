{
  "title": "Multi line comments",
  "categories": ["lang", "debug"],
  "keywords": ["comment", "comments", "multi", "multi-line", "impossible"]
}
---

# Multi-line comments

They're not possible in zig. Either use `//` for regular comments or `///` for
doc comments.

```zig
/// myFunc can be documented with three forward slashes
pub fn myFunc() void {
  // ...
}

test "comments" {
  // this is a regular comment
}
```
