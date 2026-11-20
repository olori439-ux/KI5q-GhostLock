# TECNO KI5q (Spark 10) — stock boot.img for GhostLock profile request

Device: TECNO KI5q (Spark 10), MT6765 (Helio G37)
Build: KI5q-H6127AlAmAnAoApAq-T-GL-250117V2518 (global, V2518)
Kernel: 4.19.191-g1e6fa7bf2642-dirty, boot header v2, non-GKI

File: `KI5q-boot.img` (33,554,432 bytes)
SHA256: `6136dea47b4f40839f8bb8435f82b9649b6e1f8a96fa5c0e2d04007a3b0b07cc`

GhostLock v1.2 says "Not supported" (no built-in profile). The extractor only
accepts boot header v3/v4, and this image is v2. Repacking the same kernel as
v3 passes the header check, but then fails with:

`kallsyms recovery failed: no kallsyms table found (0 token tables, 0 name blocks)`

The kernel was shipped with the symbol table stripped (CONFIG_KALLSYMS=y in
the config, but no valid token table in the decompressed kernel), so no profile
can be derived from the image alone. This file is published so a GhostLock
maintainer can attempt a manual port for this exact kernel build.

Related: https://github.com/YuKongA/ghostlock-app
Proof 4.19.191 is portable: Samsung M53 port (N1et/samsung-m53-root-4x).
