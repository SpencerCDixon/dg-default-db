{
  "title": "Spawn child process and read stdout",
  "categories": ["process"],
  "keywords": ["child", "stdout", "process", "spawn", "read"]
}
---

# Spawning a child process and reading output

Inside `std` there is a struct `ChildProcess` which we can use to either
`init` or `exec`. Using `init` gives you maximum flexibility but if you're
trying to quickly execute something and get it's `stdout` or `stderr` then using
`exec` is a bit nicer:

```zig
test "exec a process and get stdout" {
    const argv = &.{ "git", "version" };
    var result = try std.ChildProcess.exec(.{
        .argv = argv,
        .allocator = std.testing.allocator,
    });

    // We now own the memory for stdout/err and need to remember to deallocate.
    defer {
        std.testing.allocator.free(result.stdout);
        std.testing.allocator.free(result.stderr);
    }

    switch (result.term) {
        .Exited => |v| {
            try std.testing.expect(v == 0);
            try std.testing.expect(std.mem.startsWith(u8, result.stdout, "git version"));
        },
        else => return std.testing.expect(false),
    }
}
```
