# nexai-open-plc-gcc

Arduino board-manager index for the **NexAi S32K344** board, consumed by
OpenPLC Editor (via `arduino-cli`).

```
https://nexaibody.github.io/nexai-open-plc-gcc/package_nexai_index.json
```

This URL is embedded in signed `.vpp` packages — it must never change.

## What is here

| Item | Where | Contents |
|---|---|---|
| `package_nexai_index.json` | repository root (GitHub Pages) | platform + toolchain entries |
| `nexai-s32k-<version>.tar.bz2` | Release `nexai-s32k-<version>` | Platform shell only: `platform.txt`, `boards.txt`, an `Arduino.h` shim, `pins_arduino.h`. **No source code, no BSW.** |
| Windows toolchain | Release `gcc-<arm-version>` | Arm GNU Toolchain, unmodified, re-packed into a single root folder (arduino-cli rejects Arm's root-less zip) |
| Toolchain source | Release `gcc-<arm-version>` | `arm-gnu-toolchain-src-snapshot-<arm-version>.tar.xz` |

Linux toolchains are downloaded directly from `developer.arm.com`.

The platform does not build on its own: the S32K344 core and BSW are delivered
only inside the licensed `.vpp` package.

## Toolchain license

The toolchain is the **Arm GNU Toolchain**, redistributed unmodified. GCC,
binutils and GDB are licensed under the GNU GPL; newlib under its own BSD-style
licenses. The complete corresponding source code is published next to the
binaries in each `gcc-<arm-version>` Release, and is also available from Arm:
<https://developer.arm.com/downloads/-/arm-gnu-toolchain-downloads>.

## Maintenance

Do not edit `package_nexai_index.json` by hand. It is generated in the
private editor repository by `arduino-platform/tools/make-platform-archive.sh`
(see `docs/gcc_compiler_method.md` there). Old entries are never removed.
Upload the Release assets **before** publishing a new index.
