# SXPM Repository

This is the central package repository for **SXOS** and its `sxpm` package manager. 

## Repository Structure

SXPM packages are organized into branches representing different release channels. You should use `git checkout <branch>` to navigate these channels:

- `stable`: Production-ready, fully tested packages.
- `testing`: Release candidates and beta packages.
- `nightly`: Bleeding edge builds.

### Index Layout (`index.json`)
At the root of each branch, there is an `index.json` file. This tells SXPM what packages exist and where their `.sxpkg` binary file is hosted.

```json
{
  "music": {
    "latest": "1.2.0",
    "versions": {
      "1.2.0": {
        "url": "https://raw.githubusercontent.com/SwirX/sxpm-repo/stable/packages/music/1.2.0.sxpkg",
        "sha256": "abc12345...",
        "dependencies": {
          "sxui": ">=1.0.0"
        }
      }
    }
  }
}
```

### The `.sxpkg` Package Format
The SXPM package manager creates serialized `.sxpkg` archives. 

#### How to build an app locally:
1. Initialize your project folder with a `manifest.lua`.
2. Keep your code in a `src/` folder.
3. On SXOS, run `sxpm build .` inside your project directory.
4. SXPM will safely map the directories and spit out a `.sxpkg` archive string.

#### Submitting a Package:
1. Fork this repository.
2. Build your `.sxpkg` and place it in `/packages/<name>/<version>.sxpkg`.
3. Update the `index.json` to expose your package.
4. Submit a Pull Request targeting the `testing` or `nightly` branch!
