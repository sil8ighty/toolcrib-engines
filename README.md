# ToolCrib engines

Release-only, binaries only. This repository holds the compiled engine components that the ToolCrib CAD/CAM application downloads on first run. It contains no ToolCrib source code. The product repository is private.

Everything is published as GitHub release assets. Open the Releases page and pick a tag.

## What is published

| Release tag | Asset | What it is | Licence of the binary |
|---|---|---|---|
| `cam-post-js-1.2.2` | `toolcrib_post_js-1.2.2-cp311-cp311-macosx_10_14_x86_64.whl` | Sandboxed JavaScript engine for post-processor code sections; its memory cap is counted the same on every computer (macOS Intel) | ToolCrib proprietary binding; includes QuickJS-NG 0.18.0 (MIT) |
| `cam-sim-1.8.1` | `toolcrib_cam_sim-1.8.1-cp311-cp311-macosx_10_14_x86_64.whl` | Fast CAM simulation engine (engine ABI 9) with its own portable maths: the same stock to the last bit on every computer (macOS Intel) | ToolCrib proprietary; includes pybind11 (BSD-3-Clause) and fdlibm maths (Sun, permissive notice) |
| `cam-post-js-1.2.2` | `toolcrib_post_js-1.2.2-cp311-cp311-macosx_11_0_arm64.whl` | Sandboxed JavaScript engine for post-processor code sections; its memory cap is counted the same on every computer (macOS Apple silicon) | ToolCrib proprietary binding; includes QuickJS-NG 0.18.0 (MIT) |
| `cam-sim-1.8.1` | `toolcrib_cam_sim-1.8.1-cp311-cp311-macosx_11_0_arm64.whl` | Fast CAM simulation engine (engine ABI 9) with its own portable maths: the same stock to the last bit on every computer (macOS Apple silicon) | ToolCrib proprietary; includes pybind11 (BSD-3-Clause) and fdlibm maths (Sun, permissive notice) |
| `cam-post-js-1.2.2` | `toolcrib_post_js-1.2.2-cp311-cp311-manylinux_2_28_aarch64.whl` | Sandboxed JavaScript engine for post-processor code sections; its memory cap is counted the same on every computer (Linux ARM64) | ToolCrib proprietary binding; includes QuickJS-NG 0.18.0 (MIT) |
| `cam-sim-1.8.1` | `toolcrib_cam_sim-1.8.1-cp311-cp311-manylinux_2_28_aarch64.whl` | Fast CAM simulation engine (engine ABI 9) with its own portable maths: the same stock to the last bit on every computer (Linux ARM64) | ToolCrib proprietary; includes pybind11 (BSD-3-Clause) and fdlibm maths (Sun, permissive notice) |
| `cam-post-js-1.2.2` | `toolcrib_post_js-1.2.2-cp311-cp311-manylinux_2_28_x86_64.whl` | Sandboxed JavaScript engine for post-processor code sections; its memory cap is counted the same on every computer (Linux x86_64) | ToolCrib proprietary binding; includes QuickJS-NG 0.18.0 (MIT) |
| `cam-sim-1.8.1` | `toolcrib_cam_sim-1.8.1-cp311-cp311-manylinux_2_28_x86_64.whl` | Fast CAM simulation engine (engine ABI 9) with its own portable maths: the same stock to the last bit on every computer (Linux x86_64) | ToolCrib proprietary; includes pybind11 (BSD-3-Clause) and fdlibm maths (Sun, permissive notice) |
| `cam-post-js-1.2.2` | `toolcrib_post_js-1.2.2-cp311-cp311-win_amd64.whl` | Sandboxed JavaScript engine for post-processor code sections; its memory cap is counted the same on every computer (Windows x64) | ToolCrib proprietary binding; includes QuickJS-NG 0.18.0 (MIT) |
| `cam-sim-1.8.1` | `toolcrib_cam_sim-1.8.1-cp311-cp311-win_amd64.whl` | Fast CAM simulation engine (engine ABI 9) with its own portable maths: the same stock to the last bit on every computer (Windows x64) | ToolCrib proprietary; includes pybind11 (BSD-3-Clause) and fdlibm maths (Sun, permissive notice) |
| `cam-sim-1.8.0` | `toolcrib_cam_sim-1.8.0-cp311-cp311-win_amd64.whl` | Fast CAM simulation engine (engine ABI 9) | ToolCrib proprietary; includes pybind11 (BSD-3-Clause) |
| `cam-sim-1.4.0` | `toolcrib_cam_sim-1.4.0-cp311-cp311-win_amd64.whl` | Earlier simulation engine (ABI 5), kept for older ToolCrib builds that still pin it | ToolCrib proprietary; includes pybind11 (BSD-3-Clause) |
| `cam-post-js-1.2.1` | `toolcrib_post_js-1.2.1-cp311-cp311-win_amd64.whl` | Sandboxed JavaScript engine for post-processor code sections | ToolCrib proprietary binding; includes QuickJS-NG 0.18.0 (MIT) |

Python 3.11 wheels. From the cam-sim-1.8.1 and cam-post-js-1.2.2 tags: Windows x64, macOS (Apple silicon, macOS 11 or later; Intel, macOS 10.14 or later) and Linux (x86_64 and ARM64, manylinux_2_28). Each platform build gives the same stock and the same posted files as Windows, bit for bit (checked by ToolCrib before every release). Earlier tags are Windows x64 only.

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
| `toolcrib_post_js-1.2.2-cp311-cp311-macosx_10_14_x86_64.whl` | 428620 | `3df242f6867b6868fa01e5c7c43fd971a2e5a8869b4b8666bbb555bdbaea3b82` |
| `toolcrib_cam_sim-1.8.1-cp311-cp311-macosx_10_14_x86_64.whl` | 213223 | `fcda674e4593cd5d016bf5c91ec026ede6466ba9afd541fe9e6a5e3b4c8c48f3` |
| `toolcrib_post_js-1.2.2-cp311-cp311-macosx_11_0_arm64.whl` | 389952 | `09193c9560468db87c391354a3e7056302d59b7ea2c038b7c70c1116d86300a2` |
| `toolcrib_cam_sim-1.8.1-cp311-cp311-macosx_11_0_arm64.whl` | 191586 | `3e94ad115868ac2b35f216b689a0fdc12aa78dab364adc84473d92ef4feaaee8` |
| `toolcrib_post_js-1.2.2-cp311-cp311-manylinux_2_28_aarch64.whl` | 510996 | `f38ead5ce684de4a4cdb3908d3f67584e6b3107aaf8a2f6f38e9973a0c0323f9` |
| `toolcrib_cam_sim-1.8.1-cp311-cp311-manylinux_2_28_aarch64.whl` | 217612 | `44bb508e2d5e4b5cf459a5282994198bf70d9c25686918be4bd8595130cad2fb` |
| `toolcrib_post_js-1.2.2-cp311-cp311-manylinux_2_28_x86_64.whl` | 540436 | `8a8098f98d389bd128ba4d35809751e08fe265df91d8baf7fc18cd0a9c7af865` |
| `toolcrib_cam_sim-1.8.1-cp311-cp311-manylinux_2_28_x86_64.whl` | 234035 | `c269404d7d3d33836ee921c4797a4a8d7d747883270dec8a39f81b42f380fae9` |
| `toolcrib_post_js-1.2.2-cp311-cp311-win_amd64.whl` | 486632 | `5dd3456f6dea3817043df5c75dce05db5f1e87c8acf7cf2e069a76bd0701c96f` |
| `toolcrib_cam_sim-1.8.1-cp311-cp311-win_amd64.whl` | 204792 | `0560fb9ace528e56e7a8a0788b1ff6efd459c953abcd6b137a4dacce451707cc` |
| `toolcrib_cam_sim-1.8.0-cp311-cp311-win_amd64.whl` | 199220 | `20cda636202714eaf5ad01a757698adbf16b27950346a83292a3785bc0b23faf` |
| `toolcrib_cam_sim-1.4.0-cp311-cp311-win_amd64.whl` | 161457 | `195663c7398e6b5d1034fb773c81de427f484c1679b459db8061f70bdca90381` |
| `toolcrib_post_js-1.2.1-cp311-cp311-win_amd64.whl` | 486533 | `ab867e1b6b83f3ba5087a6fc704dffc109c0766090eea13fa56b5f794aa7c1f7` |

## FreeCAD engine runtime (Windows)

| Release tag | Asset | What it is | Licence |
|---|---|---|---|
| `engine-1.1.4-tc8` | `FreeCAD_1.1.4-tc8-Windows-x86_64-py311.7z` | The FreeCAD 1.1.4 runtime ToolCrib CAD runs on (Windows x64, Python 3.11): the official FreeCAD 1.1.4 release with ToolCrib's engine patches 0001-0027 rebuilt into it and Coin3D 4.0.10 | FreeCAD: LGPL-2.1-or-later. Each third-party package keeps its own licence (below). |

This archive is free software, not ToolCrib proprietary code. Its complete corresponding source is public:

- **FreeCAD with ToolCrib's patches:** release [`engine-1.1.4-tc8`](https://github.com/sil8ighty/toolcrib-engine-source/releases/tag/engine-1.1.4-tc8) of `toolcrib-engine-source` (`FreeCAD_1.1.4-tc8-source.tar.gz`: FreeCAD 1.1.4 with patches 0001-0027 applied, the patches, and the build scripts with `BUILDING.md`). The patches and a manifest of every rebuilt file are also inside the runtime, in `doc/ToolCribEngine/`.
- **The LGPL and GPL third-party packages inside it** (Qt 6.8.3, PySide6 6.8.3, Open CASCADE 7.8.1, SMESH, OpenCAMLib, GEOS, GLib, cairo, MPFR, GMP, CalculiX 2.22, Gmsh 4.15.0, the GCC runtime and the rest): the upstream source archive of each exact version plus the conda-forge recipe that built it, in releases [`thirdparty-win-beta-2026-11`](https://github.com/sil8ighty/toolcrib-engine-source/releases/tag/thirdparty-win-beta-2026-11) and [`thirdparty-win-tc8-delta`](https://github.com/sil8ighty/toolcrib-engine-source/releases/tag/thirdparty-win-tc8-delta) (Graphviz, getopt-win32, Eigen, FreeImage, backports.zstd). Each release lists its files in `SHA256SUMS.txt`.
- **Notices:** [`notices/engine-tc8/`](notices/engine-tc8/): the licence files of every package in the runtime (`NOTICES-INDEX.md`), with the GPL-2.0, GPL-3.0, LGPL-2.1 and LGPL-3.0 texts.

CalculiX (`bin/ccx.exe`) and Gmsh (`bin/gmsh.exe`, `bin/gmsh.dll`) are separate GPL-2.0-or-later programs inside the runtime; ToolCrib runs them as their own processes. Their complete corresponding source code (and that of every other LGPL and GPL part) is published at no charge next to this runtime, in the source releases linked above.

Left out of this runtime (they are in the official FreeCAD release): FFmpeg with x264 and x265, and IfcOpenShell with its CGAL parts. FreeCAD's BIM IFC import and export therefore do not work in it.

You may modify the engine, rebuild it and replace the runtime, or any library in it, with your own build (`BUILDING.md` in the source archive).

| Asset | Size (bytes) | SHA-256 |
|---|---|---|
| `FreeCAD_1.1.4-tc8-Windows-x86_64-py311.7z` | 401024253 | `eaa505b07cf1bb08236a95e0e5373f4df193adcfd01e2ecfafb913f0b9e47445` |
