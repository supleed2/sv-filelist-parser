# SystemVerilog Filelist Parser

A library in Rust to parse a SystemVerilog Filelist and return
a list of files, include directories and defines.

Environment variables optionally enclosed in paranthesis or
curly braces (i.e. `$`, `$()` or `${}`) will be automatically
substituted.

## Example

```rust
use sv_filelist_parser;
let filelist = sv_filelist_parser::parse_file("testcase/files.f")
    .expect("Cannot read filelist");
for file in filelist.files {
    println!("{:?}", file);
}
for incdir in filelist.incdirs {
    println!("{:?}", incdir);
}
for (d, t) in filelist.defines {
    match t {
        None => println!("{:?}", d),
        Some(te) => println!("{:?}={:?}", d, te),
    };
}
```
