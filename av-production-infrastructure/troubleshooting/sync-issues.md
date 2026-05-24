# Troubleshooting – Sync Issues

## Symptoms

- Audio and video out of sync on stream
- IMAG appears delayed compared to live sound
- Lip-sync issues on broadcast output

## Current Baseline (Main Sanctuary Broadcast)

| Parameter | Value |
|-----------|-------|
| Audio chain latency | ≈200 ms |
| Video pipeline latency | ≈150–160 ms |
| SE-3200 audio delay | 46 ms |
| Dominant latency source | Ableton plugin chain (181 ms) |

If sync is off, something changed from these baseline values.

## Common Causes

1. **Plugin chain latency changed** – Adding/removing plugins on the broadcast bus changes total audio delay. This is the #1 cause.
2. **SE-3200 delay was reset** – Check that audio delay is still set to 46 ms
3. **Encoder buffering** – Streaming encoder adds variable delay
4. **Clock drift** – Mismatched Dante clock sources cause gradual drift
5. **Buffer size changed** – Ableton buffer change shifts overall latency

## Quick Diagnosis

| Observation | Likely Cause | Fix |
|-------------|-------------|-----|
| Audio late on stream | Plugin added or delay reduced | Re-measure, adjust SE-3200 delay down |
| Audio early on stream | Plugin removed or delay increased | Re-measure, adjust SE-3200 delay up |
| Gradual drift over time | Clock sync issue | Check Dante clock master |
| Sync was fine, now broken | Something changed | Check changelog, verify plugin chain |

## Diagnostic Steps

1. Verify SE-3200 audio delay is still set to 46 ms
2. Check Ableton plugin chain — does it still report 181 ms?
3. Run VLC sync test: play test file, measure audio offset
4. Calculate: correct delay = current SE-3200 delay − measured audio offset
5. Apply new value and re-verify

## Fine-Tuning Reference

| Adjustment | Effect |
|------------|--------|
| ±5 ms | Sub-frame, likely imperceptible |
| ±10–15 ms | Noticeable lip-sync change |
| 1 frame (60p) | 16.7 ms |
| 1 frame (30p) | 33 ms |

## Solutions

- Re-measure and update offset values
- Check Dante clock source alignment
- Verify Ableton plugin chain matches documentation (181 ms expected)
- Apply corrective delay: if audio late → decrease delay; if audio early → increase delay
- Document new values in [Broadcast Sync](../systems/main-sanctuary/broadcast/sync.md)
- Log the change in [Changelog](../systems/main-sanctuary/changelog.md)

## Related Documents

- [Broadcast Sync](../systems/main-sanctuary/broadcast/sync.md) – Full sync analysis
- [Audio Latency](../systems/main-sanctuary/audio/latency.md) – Component breakdown
- [Switcher Settings](../systems/main-sanctuary/video/switcher-settings.md) – SE-3200 delay config
- [Latency Measurement Standards](../standards/latency-measurement.md) – How to measure
