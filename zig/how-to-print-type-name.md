{
  "title": "How to print type name",
  "categories": ["lang"],
  "keywords": ["type", "name", "print"]
}
---

# How to print type name

TL;DR: `@typeName(@TypeOf(variable_to_test))`

Sometimes it can be useful to know the resolved type name of some data
structure. There are builtin compiler directives to accomplish this task:

```zig
const MyStruct = struct {
    name: []const u8 = "MyStruct",
};

test "print type name" {
    const structs = &[2]MyStruct{
        MyStruct{},
        MyStruct{},
    };
    // *const [2]MyStruct
    std.debug.print("\n'{s}'\n", .{@typeName(@TypeOf(structs))});
}
```

The type here is `*const [2]MyStruct` which is a constant pointer to an array of
length two housing the data structure `MyStruct`.
