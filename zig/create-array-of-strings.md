{
  "title": "Create array of constant strings",
  "categories": ["lang"],
  "keywords": ["slice", "array", "string", "const", "constant"]
}
---

# Creating an array of constant strings

Imagine we have this function we'd like to call:

```zig 
// This function takes a constant slice of constant bytes. 
// Think of it as an array of constant immutable strings.
fn takesSliceOfStrings(args: []const []const u8) void {
    for (args) |item| {
        std.debug.print("{s}\n", .{item});
    }
}
```

Arrays are denoted by `[N]T` where `N` is the number of elements. For array
literals you can replace `N` with `_` to have the number be inferred:

```zig
const a = [5]u8{ 'h', 'e', 'l', 'l', 'o' };
const b = [_]u8{ 'w', 'o', 'r', 'l', 'd' };
```

A string in Zig can be represented by a slice of bytes (`[]u8` or `[]const u8`).

Therefore, to create an array/slice of strings we would do:

```zig
test "array of constant strings" {
    // Use '_' to infer the size of the array
    const keywords = &[_][]const u8{
        "async",
        "await",
    };
    // *const [2][]const u8
    std.debug.print("\n'{s}'\n", .{@typeName(@TypeOf(keywords))});
    takesSliceOfStrings(keywords);
}
```

There is also a shorthand notation we can use via `&.{ ... }`:

```zig
test "shorthand notation" {
    takesSliceOfStrings(&.{ "one", "two", "thre" });
}
```
