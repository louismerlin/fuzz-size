## AFL.rs sanity check for inputs > 1MB

This repository was created to check if AFL.rs works with inputs bigger then 1 megabyte.

So far, I was unable to make it work.

To reproduce, run:

```
cargo afl build
mkdir in
# The fuzz-size binary is around 4MB on my machine, so we use it as initial input
cp target/debug/fuzz-size in/
# -G 10000000 is supposed to allow AFL to use and generate inputs <= 10MB in size
cargo afl fuzz -i in -o out -G 10000000 target/debug/fuzz-size 
```

The fuzzer will not find the crash defined in [main.rs](./src/main.rs).
