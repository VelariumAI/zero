# Agent Repair Demo

This demo shows the intended agent loop on a real diagnostic.

Repair flow:

1. Check broken fixture.
2. Inspect diagnostic.
3. Explain diagnostic.
4. Request repair plan.
5. Apply documented edit manually.
6. Re-check fixed fixture.

Notes:

- `broken.0` is intentionally invalid.
- `fixed.0` is expected repaired fixture.
- Broken fixture is used to demonstrate diagnostics and repair planning.

Validation notes:

- `bin/zero check --json examples/agent-repair-demo/broken.0` should return structured diagnostics and a non-zero result.
- `bin/zero check examples/agent-repair-demo/fixed.0` should pass when local toolchain is built and functioning.
- Missing native compiler or similar environment limits should be reported as environment limitations, not documentation failures.

Broken fixture:

```sh
bin/zero check --json examples/agent-repair-demo/broken.0
```

Explain the diagnostic:

```sh
bin/zero explain --json TYP009
```

Inspect the repair plan:

```sh
bin/zero fix --plan --json examples/agent-repair-demo/broken.0
```

Apply documented edit manually:

```diff
-    let dst: [4]u8 = [0, 0, 0, 0]
+    let mut dst: [4]u8 = [0, 0, 0, 0]
```

Re-run check:

```sh
bin/zero check examples/agent-repair-demo/fixed.0
```

Run the scripted demo:

```sh
pnpm run agent:demo
```
