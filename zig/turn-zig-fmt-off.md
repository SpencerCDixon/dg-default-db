{
  "title": "Turn zig fmt off or on",
  "categories": ["lang", "debug"],
  "keywords": ["format", "zig", "off", "on", "source", "sourcecode"]
}
---

# How to turn zig fmt on/off in source code

Toggling Zig's `fmt` tool can be done via inline comments in the source code:

```zig
// zig fmt: off
switch (self) {
    .search      => |c| return std.mem.eql(u8, c.query, other.search.query),
    .test_render => |c| return std.mem.eql(u8, c, other.test_render),
    .list_titles => |l| return l == other.list_titles,
}
// zig fmt: on
```

> NOTE: Remember to turn it back on with 'zig fmt: on'
