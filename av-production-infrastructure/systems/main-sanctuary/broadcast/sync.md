# Main Sanctuary – Broadcast Sync

## Purpose

Document audio/video synchronization for the broadcast (livestream) output from the SE-3200 switcher.

## System Regime

**Audio is slower than video.** The Ableton plugin chain (~181 ms) dominates the audio path, making audio arrive later than video at the SE-3200 output. This means:

- We cannot "advance" audio — only reduce added video delay
- The SE-3200 audio delay compensates by holding video to let audio catch up
- The delay value must be the **minimum** needed to align, not a zero-latency target

## Measured Latency

| Component | Latency (ms) | Method | Notes |
|-----------|-------------|--------|-------|
| Dante send (DM7 → Broadcast PC) | 4 | Dante specs | Network traversal |
| Ableton overall latency (I/O + buffers) | 10.7 | Ableton status bar | Includes I/O and safety buffers |
| Ableton plugin chain | 181 | Ableton track delay display | Lookahead limiters, linear-phase EQ |
| Dante return (Broadcast PC → DM7) | 4 | Dante specs | Network traversal |
| DM7 internal processing | ~1 | Yamaha specs | Console throughput |
| **Total audio pipeline** | **≈200 ms** | Calculated | Sum of above |
| Video pipeline (Camera → SE-3200 PGM) | 150–160 | Estimated | Includes camera + switcher processing |
| **Audio-video difference** | **≈40–50 ms** | Calculated | Audio arrives later |

## Empirical Validation (VLC Method)

| Parameter | Value |
|-----------|-------|
| Test method | VLC sync test file playback through full chain |
| Audio offset observed | +150 ms late (audio behind video) |
| SE-3200 delay at time of test | 196 ms |
| Correct delay calculation | 196 − 150 = **46 ms** |

### Cross-validation

- Calculated model: audio − video ≈ 200 − 155 = **45 ms**
- Empirical test: **46 ms**
- ✅ Both methods independently agree

## Active Compensation Setting

| Device | Parameter | Value | Status |
|--------|-----------|-------|--------|
| Datavideo SE-3200 | Audio Delay | **46 ms** | ✅ Active |

**Acceptable fine-tuning range:** 42–50 ms

## Sync Method

The SE-3200's built-in audio delay holds the audio output to align with the video processing pipeline. Since audio arrives ~200 ms after source and video arrives ~155 ms after source, the switcher delays audio by only 46 ms (not the full pipeline difference) to achieve sync at output.

## Fine-Tuning Procedure

1. Feed a sharp transient (hand clap, slate click, or LED flash + tone)
2. Record the SE-3200 PGM output
3. In VLC or a DAW, zoom into waveform + video frame
4. Check alignment: audio spike vs. visual contact
5. Adjust:
   - Audio still slightly late → **decrease** delay
   - Audio slightly early → **increase** delay

### Adjustment Scale

| Adjustment | Effect |
|------------|--------|
| ±5 ms | Sub-frame precision (imperceptible to most) |
| ±10–15 ms | Visible lip-sync change |
| 1 frame (60p) | 16.7 ms |
| 1 frame (30p) | 33 ms |

## Re-measurement Triggers

Any of these changes require re-measuring and potentially adjusting the 46 ms value:

| Change | Expected Effect |
|--------|----------------|
| Remove heavy plugin (e.g., lookahead limiter) | Audio becomes earlier → increase delay |
| Add lookahead plugin | Audio gets later → decrease delay |
| Change Ableton buffer size | Slight shift in either direction |
| Change sample rate | Recalculate all values |
| Swap/update hardware | Full re-measurement required |
| Firmware update on SE-3200 | Re-verify video pipeline latency |

## Signal Path (Broadcast Audio)

```
DM7 Broadcast Bus
    → Dante (4 ms)
        → Ableton Live (Broadcast PC)
            → I/O + Buffers (10.7 ms)
            → Plugin Chain (181 ms)
        → Dante Return (4 ms)
    → DM7 (~1 ms)
        → SE-3200 Audio Input
            → Audio Delay (46 ms applied)
            → PGM Output (synced with video)
```

## Last Verified

2025-01-15
