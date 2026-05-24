# Main Sanctuary – IMAG Delay Alignment

> **Last Updated:** 2026-05-24

---

## Purpose

Ensure IMAG displays are time-aligned with live audio for the in-room audience. Unlike broadcast (which uses the SE-3200's 46 ms audio delay), IMAG sync depends on the video pipeline latency relative to the speed of sound from the PA.

## Video Pipeline Latency (Estimated)

| Segment | Latency | Notes |
|---------|---------|-------|
| Camera processing | ~30–50 ms | Panasonic PTZ internal |
| SE-3200 switcher | ~1–2 frames (~17–33 ms) | Depends on format |
| NovaStar scaler | ~1–2 frames (~17–33 ms) | LED wall processing |
| LED panel response | ~3–5 ms | Panel scan time |
| **Total estimated** | **~70–120 ms** | Needs on-site measurement |

## Speed of Sound Reference

- Speed of sound: ~343 m/s (at 20°C)
- Delay per meter: ~2.9 ms/m
- If LED wall is 15 m from PA source → ~44 ms acoustic delay

## Alignment Strategy

For in-room IMAG, the audience perceives:
- **Audio** arrives at speed of sound (~2.9 ms/m from PA)
- **Video** arrives after the video pipeline (~70–120 ms)

If the video pipeline is shorter than the acoustic propagation delay to the back of the room, no correction is needed. If video is noticeably late for front rows, consider:
- Reducing NovaStar processing (low-latency mode)
- Using a faster display pipeline

## Measured Values

> **TODO:** Measure during next site visit with lip-sync test generator.

| Display | Measured Video Latency | Acoustic Delay (at seating) | Net Offset | Action |
|---------|----------------------|---------------------------|------------|--------|
| LED Wall | (TBD) | (TBD) | (TBD) | (TBD) |

## Related Documents

- [Broadcast Sync](../broadcast/sync.md) — SE-3200 audio delay for stream
- [IMAG Routing](routing.md) — video signal path to displays
