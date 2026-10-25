# Repository migration

On 2026-10-26 the maintained Bootstrap directory was extracted from
`LKCY23/claudespace:claude-desktop-bootstrap` with `git subtree split`.
Its four source commits retain their authors, dates and messages. Commits have
new IDs because Bootstrap now lives at the repository root. Original releases
and full parent-repository history remain in claudespace.

| Original claudespace commit | Extracted Bootstrap commit |
| --- | --- |
| `c64da73f2a9c917b27bfaaa768d372a33c09a214` | `aaaa3b0deaeeeff5f31ce988e55eb2577ad9cc3f` |
| `28be0328983e8629d0c49533262045220d242040` | `472c5dd356b44cc244087dff5d2495cbb4e7b046` |
| `9fc80669cb16a620d53fe869e797435316fda273` | `b0b60b100b6e0f5c8c25d8c1f26041fe6ecc8b06` |
| `f52e54e5e662287322e4bdd6a7d85f98b850619b` | `3eafb8b797c46c9174705104e29fde7d018f7f47` |

The release workflow and `scripts/release_assets.py`, together with its tests,
were copied from claudespace at `46be132141ab9056dfee3bd6a4210cb68ba651b2`.
Workflow paths now target this repository root. The publisher's behavior is
unchanged; claudespace keeps its own copy for resource-baseline releases.

The independent development checkout is `~/claude-desktop-bootstrap`.
Claudespace adopts it through `apps/claude-desktop-bootstrap` as a submodule,
using the GitHub repository URL and an exact commit, not a local symlink.
The former root-level directory is removed. Runtime behavior remains 2.0.1.

MacBook is the development host. Tests, builds and third-party launcher use
belong on Mac mini. Old local App bundles and backups are not development
inputs. Local historical work and verification records, if retained, belong in
an ignored `.local-archive/`, never in the public source or release archive.
