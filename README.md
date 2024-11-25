# SimpleLinearRegression Library for Zig programming language

## How to use?

- Run the fetch command:

```zig
zig fetch --save https://github.com/RohanVashisht1234/SimpleLinearRegression.zig/archive/refs/tags/v0.0.0.tar.gz
```

- Add the following to your build.zig file just above `b.installArtifact(exe);`:

```zig
const SimpleLinearRegression = b.dependency("SimpleLinearRegression", .{
    .target = target,
    .optimize = optimize,
});

exe.root_module.addImport("SimpleLinearRegression", SimpleLinearRegression.module("SimpleLinearRegression"));
```

- Now, you can add the following code to `src/main.zig`:
```zig
const std = @import("std");
const SimpleLinearRegression = @import("SimpleLinearRegression.zig");

pub fn main() void {
    const data = &.{
        // x , y
        .{ 1.2, 39344.0 },
        .{ 1.4, 46206.0 },
        // ...
    };
    var SLR = SimpleLinearRegression.init(data);
    const y = SLR.predict(11.0);
    std.debug.print("Y: {d}\n", .{y});
    std.debug.print("M: {d}\n", .{SLR.m});
    std.debug.print("C: {d}\n", .{SLR.c});
}
```
- You can check the examples folder for better examples.
