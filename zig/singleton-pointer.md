{
  "title": "Singleton design pattern",
  "categories": ["pattern", "pointer"],
  "keywords": ["singleton", "memory"]
}
---
# Singleton pointer design pattern

First we can define some global state that is optional. A `setup` function needs
to be called before the singleton is accessed.

```zig
const TermState = struct {
    buffer: struct {
        in: ArrayList(u8) = undefined,
        out: ArrayList(u8) = undefined,
    } = .{},
};
var termState: ?TermState = null;
```

In debug modes, we can protect access to our global state with a helpful
warning. 

```zig
fn state() callconv(.Inline) *TermState {
    if (std.debug.runtime_safety) {
        if (termState) |*self| return self else @panic("terminal is not initialized");
    } else return &termState.?;
}

pub fn setup(alloc: *Allocator) !void {
    errdefer termState = null;
    termState = .{};
    const self = state();

    self.buffer.in = try ArrayList(u8).initCapacity(alloc, 4096);
    errdefer self.buffer.in.deinit();
    self.buffer.out = try ArrayList(u8).initCapacity(alloc, 4096);
    errdefer self.buffer.out.deinit();
}
```
