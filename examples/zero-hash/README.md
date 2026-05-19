# zero-hash

`zero-hash` demonstrates a small CLI package that seeds a file, reads it back through a fixed-buffer allocator, computes CRC-32 over the bytes, and prints `zero-hash ok` when the checksum matches.

Primary entry points:

- `zero.json`
- `src/main.0`
- `src/input.0`

Validation commands:

```sh
bin/zero check examples/zero-hash
bin/zero build --emit exe --target linux-musl-x64 examples/zero-hash --out .zero/out/zero-hash
```

Environment and target notes:

- Example uses hosted filesystem APIs through `std.fs.host()`.
- It seeds `.zero/zero-hash-input.txt` before reading the file.
- Use a hosted target for the executable path.
