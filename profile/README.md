# ADS-7 (Advanced Disk System-7)

A file system built around three ideas: adaptive data splitting, strong
encryption by default, and the ability to detect and repair corrupted
data on its own.

## What it does today

- **Adaptive striping** — files are split into 7–56 chunks and
  scattered across disk, with files under 1MB kept as a single block.
- **AES-256-GCM encryption** — authenticated encryption on every chunk,
  so tampering is detected immediately, not just corruption.
- **Self-healing via Erasure Coding** — a single corrupted chunk can be
  reconstructed from parity data without user intervention.
- **Seal system** — a protected zone that rejects writes without a
  valid cryptographic seal, even from root.

## Status

Phase 1 (a tested userspace prototype) is complete: packing, unpacking,
deduplication, parity-based repair, and the seal system all work and
are covered by real tests. It is **not yet a mountable file system** —
kernel integration is the next major phase.

## Repositories

| Repo | Purpose |
|---|---|
| `ads-7-core` | The core C library |
| `ads-7-docs` | Design documentation and architecture |
