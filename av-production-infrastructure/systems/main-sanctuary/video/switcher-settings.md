# Main Sanctuary – Switcher Settings

> **Model:** Datavideo SE-3200  
> **IP:** 192.168.0.101 (VLAN 110) | **MAC:** 00:07:36:0a:85:c8  
> **Last Updated:** 2026-05-24

## Input Configuration

| Input # | Source | Format | IP | Notes |
|---------|--------|--------|-----|-------|
| 1 | Remote Stream Camera 1 | SDI | 192.168.0.12 | PTZ via AW-RP150 |
| 2 | Remote Stream Camera 2 | SDI | 192.168.0.13 | PTZ via AW-RP150 |
| 3 | Remote Stream Camera 3 | SDI | 192.168.0.14 | PTZ via AW-RP150 |
| 4 | Camera 4 (Booth) | SDI | 192.168.0.15 | PTZ via AW-RP150 |
| Audio | BCast-Audio (AVIO-DAO2) | Analog | — | DM7 TX 63-64 (Broadcast L/R) |

## Output Configuration

| Output # | Destination | Format | Notes |
|----------|-------------|--------|-------|
| PGM | Livestream encoder | SDI | Primary program output |
| PGM | Blackmagic Videohub (In 12) | SDI | "Worship Center Feed" – distributed to classrooms, foyer, hallways |
| AUX | Confidence monitors | SDI | Stage / green room |

> **Note:** The SE-3200 does NOT feed the LED wall directly. The LED wall is driven by the ATEM 2 M/E (Resolume + ProPresenter via DSK1 → NovaStar 600). The SE-3200 PGM feeds the Videohub for building-wide distribution, where each output passes through a **Blackmagic Teranex Mini SDI→Audio** de-embedder to supply audio to the Tesira DSP for zone speakers.

### SE-3200 Distribution via Teranex De-Embedders

```
SE-3200 PGM ──SDI──→ Videohub Input 12 ("Worship Center Feed")
                          │
              ┌───────────┼───────────────────────────┐
              ▼           ▼                           ▼
         Classroom    Worship Center             Mac Mini
         Outputs      Sanctuary Output           Outputs
              │           │                           │
         Teranex      Teranex                    Teranex
         (de-embed)   (10.10.20.128)            (DisplayMac)
              │           │                           │
         Tesira DSP   Tesira DSP                Tesira DSP
         (zone audio) (hallway/foyer audio)     (playback audio)
```

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
