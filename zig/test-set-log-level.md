{
  "title": "Set log level in tests",
  "categories": ["test", "log"],
  "keywords": ["setting"]
}
---
# Set Test Runner Log Level

Sometimes it's useful to leave debug logs in complicated tests but you only want
to print to stderr when you need to diagnose issues. Here we can add debug
logging and then turn it on for individual tests as needed:

```zig
const std = @import("std");

// The default test runners log level is .warn but this can be used to update it
// if we want to instrument tests with debug logs and get extra verbosity.
pub fn setLogLevel(level: std.log.Level) void {
    std.testing.log_level = level;
}

test "really complicated test" {
  setLogLevel(.debug);

  // ...
  std.log.debug("this will now be seen to debug things", .{});
}
```
