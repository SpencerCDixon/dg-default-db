{
  "title": "Test string equality",
  "categories": ["test", "string"],
  "keywords": ["assertion", "expectation"]
}
---
# Testing string equality

There is a function in the `std.testing` namespace for just this purpose. It
will give you a pretty diff on failures:

```zig
test "pretty print string diffs" {
    const foo = "foo";
    try std.testing.expectEqualStrings(foo, "foo");
}
```
