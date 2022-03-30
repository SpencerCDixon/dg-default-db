{
  "title": "String equality regardless of case",
  "categories": ["string", "lang"],
  "keywords": ["equal", "equality", "casing", "downcase", "lowercase", "uppercase"]
}
---

# String equality regardless of case

There is a function in the `ascii` namespace we can use:

```zig
const lang = "Zig";
std.ascii.eqlIgnoreCase(lang, "zig")
```

