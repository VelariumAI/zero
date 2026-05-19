# memory-package

`memory-package` demonstrates a small multi-file package that copies a fixed message into caller-owned storage, checks the first byte, and validates a byte-span checksum without hosted filesystem access.

Primary entry points:

- `zero.json`
- `src/main.0`
- `src/buffer.0`
- `src/checksum.0`

Validation command:

```sh
bin/zero build --target linux-musl-x64 examples/memory-package --out .zero/out/memory-package
```

Environment and target notes:

- Package is target-neutral and does not depend on hosted filesystem APIs.
- Existing docs use it for direct cross-target builds.
- `src/main.0` writes only to caller-owned memory and stdout.
