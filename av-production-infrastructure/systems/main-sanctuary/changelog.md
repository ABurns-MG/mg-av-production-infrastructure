# Main Sanctuary – Change Log

## Purpose

Track all changes to routing, latency, configuration, and hardware that affect system behavior. This is critical because changes (especially to plugin chains) directly affect broadcast sync.

## Log

| Date | Category | Change | Impact | Verified By |
|------|----------|--------|--------|-------------|
| 2025-01-15 | Sync | Measured and documented broadcast audio chain latency (≈200 ms) | Established baseline | Initial measurement |
| 2025-01-15 | Sync | Set SE-3200 audio delay to 46 ms | Broadcast A/V sync aligned | VLC sync test |
| 2025-01-15 | Documentation | Created full broadcast audio flow documentation | Reference baseline established | — |

## Change Categories

- **Sync** – Latency, delay compensation, clock changes
- **Routing** – Signal path additions/removals/modifications
- **Hardware** – Device swaps, firmware updates
- **Plugin** – Ableton plugin chain changes (HIGH IMPACT on sync)
- **Config** – Console scenes, switcher presets, Dante routing

## High-Impact Changes (Require Re-measurement)

These changes **always** require re-measuring broadcast sync:

1. Any Ableton plugin added/removed/reordered
2. Ableton buffer size change
3. Sample rate change
4. Dante latency setting change
5. SE-3200 firmware update
6. Hardware swap in audio or video chain
