# Main Sanctuary – Audio Routing

## Overview

All audio signal paths for the Main Sanctuary including Dante network audio, analog connections, and processing inserts.

## Dante Routing

### Broadcast Audio Path

| Channel | Source | Destination | Notes |
|---------|--------|-------------|-------|
| (TBD) | DM7 Broadcast Bus | Broadcast PC (Ableton) | Dante send, 4 ms |
| (TBD) | Broadcast PC (Ableton) | DM7 Return | Dante return, 4 ms |
| (TBD) | DM7 | SE-3200 Audio Input | Final broadcast feed |

### FOH Audio Path

| Channel | Source | Destination | Notes |
|---------|--------|-------------|-------|
| (To be documented) | | | |

### Monitor Audio Path

| Channel | Source | Destination | Notes |
|---------|--------|-------------|-------|
| (To be documented) | | | |

## Analog Routing

| Channel | Source | Destination | Notes |
|---------|--------|-------------|-------|
| (To be documented) | | | |

## Insert Points

### Broadcast Insert Chain

The broadcast bus is routed through Ableton Live for plugin processing before returning to the DM7 and feeding the SE-3200:

```
DM7 Broadcast Bus
    → Dante Out → Broadcast PC (Ableton Live)
        → Plugin processing (181 ms chain)
    → Dante In → DM7 Return Channel
        → SE-3200 Audio Input
```

**Total insert latency:** ≈200 ms (see [Audio Latency](latency.md))

## Clock Source

| Role | Device | Notes |
|------|--------|-------|
| Dante Clock Master | (To be documented) | |
| Word Clock | (To be documented) | |

## Related Documents

- [Audio Latency](latency.md) – Measured latency per segment
- [Broadcast Sync](../broadcast/sync.md) – A/V sync compensation
- [Console Settings](console-settings.md) – DM7 configuration
