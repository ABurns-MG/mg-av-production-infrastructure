# Main Sanctuary – Broadcast Audio

## Purpose

Document the audio feed path from the DM7 console through Ableton processing to the SE-3200 switcher for livestream output.

## Broadcast Mix Source

- **Console:** Yamaha DM7
- **Output Bus:** Broadcast Bus (dedicated mix for stream/recording)
- **Feed Type:** Post-fader stereo mix

## Signal Path

```
DM7 Broadcast Bus
    │
    ├─ Dante Send ──────────────────── [4 ms]
    │       │
    │       ▼
    │   Broadcast PC (Ableton Live)
    │       │
    │       ├─ I/O + Buffers ────────── [10.7 ms]
    │       ├─ Plugin Chain ─────────── [181 ms]
    │       │   (Lookahead limiters, linear-phase EQ)
    │       │
    │       ▼
    ├─ Dante Return ─────────────────── [4 ms]
    │       │
    │       ▼
    │   DM7 Return Channel ──────────── [~1 ms]
    │       │
    │       ▼
    └─ SE-3200 Audio Input
            │
            ├─ Audio Delay ──────────── [46 ms applied]
            │
            ▼
        PGM Output (synced with video)
```

## Routing Table

| Segment | Source | Destination | Connection | Latency |
|---------|--------|-------------|------------|---------|
| 1 | DM7 Broadcast Bus | Broadcast PC | Dante | 4 ms |
| 2 | Broadcast PC input | Plugin chain | Ableton internal | 10.7 ms |
| 3 | Plugin chain | Broadcast PC output | Ableton internal | 181 ms |
| 4 | Broadcast PC | DM7 Return | Dante | 4 ms |
| 5 | DM7 Return | SE-3200 | (TBD connection type) | ~1 ms |
| **Total** | | | | **≈200 ms** |

## Processing (Ableton Plugin Chain)

The broadcast audio is processed through Ableton Live with the following chain:

| Plugin | Purpose | Added Latency | Notes |
|--------|---------|---------------|-------|
| (To be itemized) | Lookahead limiting | (Part of 181 ms) | |
| (To be itemized) | Linear-phase EQ | (Part of 181 ms) | |
| **Total chain** | | **181 ms** | Reported by Ableton |

**⚠️ Critical:** Any change to this plugin chain directly affects broadcast sync. See [Broadcast Sync](sync.md) for re-measurement procedure.

## Levels

- Target output level: (To be documented)
- Limiter threshold: (To be documented)
- Loudness target: (To be documented, e.g., -14 LUFS for YouTube)

## Key Characteristics

- **Total path latency:** ≈200 ms
- **Dominant contributor:** Ableton plugin chain (181 ms = 90% of total)
- **Sync regime:** Audio slower than video
- **Compensation:** SE-3200 audio delay set to 46 ms

## Related Documents

- [Broadcast Sync](sync.md) – A/V sync analysis and delay compensation
- [Audio Latency](../audio/latency.md) – Full latency breakdown
- [Audio Routing](../audio/routing.md) – All audio signal paths
- [Switcher Settings](../video/switcher-settings.md) – SE-3200 delay configuration
