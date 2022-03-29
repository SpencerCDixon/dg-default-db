{
  "title": "Hash map check exists",
  "categories": ["hash"],
  "keywords": ["insert", "entry"]
}
---
# Check if item exists in hash map

First we insert a couple strings then check if one exists.

```zig
test "check for hash value" {
    var map = std.StringHashMap(i32).init(std.testing.allocator);
    // make sure to dealloc used memory
    defer map.deinit();

    try map.put("one", 1);
    try map.put("two", 1);

    try std.testing.expect(map.get("one").? == 1);
}
```
