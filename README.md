# sxpm-repo

The official package repository for [SXOS](https://github.com/SwirX/sxos).

## Branches

| Branch | Description |
|--------|-------------|
| `stable` | Production releases |
| `testing` | Pre-release validation |
| `nightly` | Automated development builds |

## Index URL (stable)

```
https://raw.githubusercontent.com/SwirX/sxpm-repo/stable/index.json
```

`sxpm` syncs this index automatically on `sxpm sync` and `sxpm upgrade`.

## Adding a Package

1. Build your package:
   ```sh
   sxpm build manifest.lua
   ```
2. Place the generated `.sxpkg` file in `packages/<name>/<name>-<version>.sxpkg`.
3. Append your entry to `index.json`:
   ```json
   "my-package": {
     "latest": "1.0.0",
     "versions": {
       "1.0.0": {
         "url": "https://raw.githubusercontent.com/SwirX/sxpm-repo/stable/packages/my-package/my-package-1.0.0.sxpkg",
         "sha256": "<sha256>",
         "size": 12345
       }
     }
   }
   ```
4. Open a Pull Request against the appropriate branch.

## Published Packages

| Package | Latest | Description |
|---------|--------|-------------|
| `sxos-core` | 2.0.0 | SXOS operating system core |
