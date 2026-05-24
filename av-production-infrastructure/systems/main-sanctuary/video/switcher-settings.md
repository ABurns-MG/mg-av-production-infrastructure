# Main Sanctuary – Switcher Settings

## Switcher

Datavideo SE-3200

## Input Configuration

| Input # | Source | Format | Notes |
|---------|--------|--------|-------|
| (To be documented) | | | |

## Output Configuration

| Output # | Destination | Format | Notes |
|----------|-------------|--------|-------|
| PGM | Livestream encoder | SDI | Primary program output |
| (Others TBD) | | | |

## Key Settings

- Resolution: 1080p
- Frame Rate: 60p
- Genlock Source: (To be documented)

## Audio Delay Setting

| Parameter | Value | Rationale |
|-----------|-------|-----------|
| Audio Delay | **46 ms** | Compensates for audio-slower-than-video condition |
| Acceptable range | 42–50 ms | Fine-tune based on transient test |

This delay exists because the broadcast audio chain (~200 ms total) is slower than the video pipeline (~150–160 ms). The SE-3200 holds audio by 46 ms so it aligns with video at the PGM output.

**⚠️ If plugin chain changes in Ableton, this value must be re-measured.** See [Broadcast Sync](../broadcast/sync.md).

## Video Processing Latency

| Measurement | Value | Method | Date |
|-------------|-------|--------|------|
| Camera → PGM output | 150–160 ms (estimated) | Calculated | 2025-01-15 |

## Related Documents

- [Broadcast Sync](../broadcast/sync.md) – Full sync analysis
- [Audio Latency](../audio/latency.md) – Audio chain breakdown
