{
  "title": "Create array of dynamic strings",
  "categories": ["lang"],
  "keywords": ["slice", "array", "string", "dynamic"]
}
---

# Creating an array of dynamic strings

Recall that a string in Zig can be represented by a slice of bytes:

* `[]u8` - mutable string 
* `[]const u8` - constant string

> NOTE: Additional metadata is associated with strings like if they are Nul
>       terminated and their length. This can be ignored for now.

To create a container with a dynamic number of strings we use an `ArrayList`:

```zig
test "dynamic array" {
    var dynamic = std.ArrayList([]const u8).init(std.testing.allocator);
    defer dynamic.deinit();

    try dynamic.append("one");
    try dynamic.append("two");

    try std.testing.expect(dynamic.items.len == 2);
}
```
