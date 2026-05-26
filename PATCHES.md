# PATCHES

This fork carries Qualia-specific patches on top of [`RLinf/RLinf`](https://github.com/RLinf/RLinf). See [`.claude/skills/vendoring/SKILL.md`](https://github.com/qualia-studios/q-core/blob/develop/.claude/skills/vendoring/SKILL.md) in the qcore repo for the pattern.

Currently composed on top of upstream `9689e48f4f7faf3d081849927e847e9a65a67820` (`feat: use broadcast for weight sync (#1157)`).

## q/fix/torch-version-range
Status: not yet PR'd upstream
Relaxes `torch>=2.5.0,<=2.9.0` → `torch>=2.5.0,<3`. Upstream's upper
bound blocks aarch64 Blackwell edges (DGX Spark, Jetson Thor) whose
only available torch wheels are 2.11+ from PyTorch's cu128 index
(earlier wheel lines don't ship sm_121 / sm_110 kernels).
