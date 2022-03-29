{
  "title": "Print number in hexidecimal",
  "categories": ["fmt"],
  "keywords": ["hex", "print"]
}
---
# Print number in hexidecimal

You can use the `{x}` format specifier:

```zig
test "print hex" {
    const number = 42;
    std.debug.print("{x}\n", .{number});
}
```
