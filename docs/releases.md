# Release operations

This repository owns Bootstrap tests, source archives and releases. Claudespace
only pins the adopted commit at `apps/claude-desktop-bootstrap`; Bootstrap does
not enter its resource catalogs or baseline installation flow.

1. Change the launcher, update `VERSION` in `install-app.py` when releasing a new
   version, and keep the README and download instructions consistent.
2. Run tests on Mac mini, including the real claude-config integration, and
   review the source diff. GitHub also runs the macOS suite on pull requests
   and main, against the pinned framework revision in the workflow.
3. Once checks pass and changes are merged, create and push the matching
   `bootstrap-v<version>` tag. Never move an existing tag.
4. `Verify and release Bootstrap` reruns tests, checks the version, and archives
   the exact repository commit. `scripts/release_assets.py` verifies each
   uploaded asset before publishing; it does not replace published contents.
5. Build the Dock app on Mac mini with that machine's explicit Machine file.
   Update claudespace's submodule pointer separately when adopting the version.

The archive contains source, tests, documentation and release tooling. It never
contains local Machine files, credentials, migration archives or a pre-bound
application. Isolated test success does not establish actual provider or GUI
acceptance.

The 2.0.0 and 2.0.1 source releases remain under LKCY23/claudespace. Their tags
in this repository identify the extracted source trees, not the original
claudespace commits. The old release assets are retained without replacement.
