# ToolCrib engines

Release-only, binaries only. This repository holds the compiled engine components that the ToolCrib CAD/CAM application downloads on first run. It contains no ToolCrib source code. The product repository is private.

Everything is published as GitHub release assets. Open the Releases page and pick a tag.

## What is published

| Release tag | Asset | What it is | Licence of the binary |
|---|---|---|---|
| `cam-post-js-1.2.2` | `toolcrib_post_js-1.2.2-cp311-cp311-win_amd64.whl` | Sandboxed JavaScript engine for post-processor code sections; its memory cap is counted the same on every computer (Windows x64) | ToolCrib proprietary binding; includes QuickJS-NG 0.18.0 (MIT) |
| `cam-sim-1.8.1` | `toolcrib_cam_sim-1.8.1-cp311-cp311-win_amd64.whl` | Fast CAM simulation engine (engine ABI 9) with its own portable maths: the same stock to the last bit on every computer (Windows x64) | ToolCrib proprietary; includes pybind11 (BSD-3-Clause) and fdlibm maths (Sun, permissive notice) |
| `cam-sim-1.8.0` | `toolcrib_cam_sim-1.8.0-cp311-cp311-win_amd64.whl` | Fast CAM simulation engine (engine ABI 9) | ToolCrib proprietary; includes pybind11 (BSD-3-Clause) |
| `cam-sim-1.4.0` | `toolcrib_cam_sim-1.4.0-cp311-cp311-win_amd64.whl` | Earlier simulation engine (ABI 5), kept for older ToolCrib builds that still pin it | ToolCrib proprietary; includes pybind11 (BSD-3-Clause) |
| `cam-post-js-1.2.1` | `toolcrib_post_js-1.2.1-cp311-cp311-win_amd64.whl` | Sandboxed JavaScript engine for post-processor code sections | ToolCrib proprietary binding; includes QuickJS-NG 0.18.0 (MIT) |

Python 3.11, Windows x64 wheels for now. macOS and Linux builds will be added here when they exist.

## Licences

- The compiled ToolCrib engine code is proprietary and copyright ToolCrib. All rights reserved. It is published here only so the ToolCrib application can download it. No source is published, and no licence is granted to use these binaries other than as part of ToolCrib.
- Bundled third-party code keeps its own licence. The notices are in [`notices/`](notices/) and are also inside each wheel under `*.dist-info/licenses/`:
  - QuickJS-NG (MIT): [`notices/QuickJS-NG-MIT-LICENSE.txt`](notices/QuickJS-NG-MIT-LICENSE.txt). ToolCrib builds the official QuickJS-NG 0.18.0 source with one change, an explicit call-depth limit.
  - pybind11 (BSD-3-Clause): [`notices/pybind11-BSD-3-Clause-LICENSE.txt`](notices/pybind11-BSD-3-Clause-LICENSE.txt).
  - fdlibm 5.3 (Sun Microsystems, permissive notice), whose algorithms the simulation engine uses for sin, cos, acos and atan2 from 1.8.1: [`notices/fdlibm-NOTICE.txt`](notices/fdlibm-NOTICE.txt).

## How downloads are verified

ToolCrib does not trust a download because of where it came from. Each lock file in the product (`sim-engine.lock.json`, `postjs-engine.lock.json`) records the expected file name, size and SHA-256 of every wheel. ToolCrib downloads the asset, checks the size and SHA-256 against its lock, and refuses to install on any mismatch. It then also checks the SHA-256 of every installed file.

To check a file yourself, compare it with [`SHA256SUMS.txt`](SHA256SUMS.txt) (the same values as in the table below):

```
sha256sum -c SHA256SUMS.txt
```

| Asset | Size (bytes) | SHA-256 |
|---|---|---|
| `toolcrib_post_js-1.2.2-cp311-cp311-win_amd64.whl` | 486632 | `5dd3456f6dea3817043df5c75dce05db5f1e87c8acf7cf2e069a76bd0701c96f` |
| `toolcrib_cam_sim-1.8.1-cp311-cp311-win_amd64.whl` | 204792 | `0560fb9ace528e56e7a8a0788b1ff6efd459c953abcd6b137a4dacce451707cc` |
| `toolcrib_cam_sim-1.8.0-cp311-cp311-win_amd64.whl` | 199220 | `20cda636202714eaf5ad01a757698adbf16b27950346a83292a3785bc0b23faf` |
| `toolcrib_cam_sim-1.4.0-cp311-cp311-win_amd64.whl` | 161457 | `195663c7398e6b5d1034fb773c81de427f484c1679b459db8061f70bdca90381` |
| `toolcrib_post_js-1.2.1-cp311-cp311-win_amd64.whl` | 486533 | `ab867e1b6b83f3ba5087a6fc704dffc109c0766090eea13fa56b5f794aa7c1f7` |
