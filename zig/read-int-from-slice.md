{
  "title": "Read int from a slice of bytes",
  "categories": ["bytes"],
  "keywords": ["read", "int", "byte"]
}
---
# Read int from a slice of bytes

There are utilities in `std.mem` for reading and writing bytes in either little,
big, or the host native endianness:

```zig
test "read int in Big Endian" {
    const bytes = [_]u8{
        0x12,
        0x23,
        0x34,
        0x45,
    };
    const result = std.mem.readInt(u32, &bytes, .Big);
    std.debug.assert(result == 0x12233445);

    const slice = bytes[1..3];
    const big_result = std.mem.readIntSliceBig(u16, slice);
    const little_result = std.mem.readIntSliceLittle(u16, slice);
    std.debug.assert(big_result == 0x2334);
    std.debug.assert(little_result == 0x3423);
}
```
