{
  "title": "Detect if building for tests",
  "categories": ["pattern", "lang"],
  "keywords": ["dispatch", "dynamic", "dynamic dispatch", "union", "tagged"]
}
---

# Dynamic dispatch via tagged unions


```zig
const Cat = struct {
    fn meow(_: Cat) []const u8 {
        return "meow!";
    }
};

const Dog = struct {
    fn bark(_: Dog) []const u8 {
        return "woof!";
    }
};

const Animal = union(enum) {
    cat: Cat,
    dog: Dog,

    fn speak(animal: Animal) []const u8 {
        return switch (animal) {
            .cat => |c| c.meow(),
            .dog => |d| d.bark(),
        };
    }
};
```
