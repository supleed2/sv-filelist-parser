# SystemVerilog Filelist Parser

A Rust library to parse a SystemVerilog Filelist and return lists of files,
include directories, and preprocessor macro definitions.

Environment variables, optionally enclosed in parenthesis or curly braces
(e.g. `$FOO`, `$(FOO)` or `${FOO}`), will be substituted.

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
