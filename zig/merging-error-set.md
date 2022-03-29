{
  "title": "Merging error sets",
  "categories": ["lang"],
  "keywords": ["error", "combining", "set", "error", "types"]
}
---

# Merging error sets

Use the `||` operator to merge error sets. 

```zig
const CustomError = error{TooShiny};
const OtherError = error{TooSmall};

// Merge our two custom error types into a superset
const AllError = CustomError || OtherError;

fn alwaysErrors() AllError!void { return CustomError.TooShiny; }

test "merging error sets" {
    try std.testing.expectError(AllError.TooShiny, alwaysErrors());
}
```

This can also be used to merge with error sets from the `std`:

```zig
const CustomError = error{TooShiny} || std.process.ArgIterator.NextError;
```
