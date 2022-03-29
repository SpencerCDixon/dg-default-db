{
  "title": "Check for error in 'if' expression",
  "categories": ["error", "lang"],
  "keywords": ["if", "unwrap"]
}
---

# Check for error in an 'if' expression

```zig
test {
  const b = error.BadValue;

  // To check only the error value, use an empty block expression.
  if (b) |_| {} else |err| {
      try expect(err == error.BadValue);
  }
}
```
