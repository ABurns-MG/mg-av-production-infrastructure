# Main Sanctuary – Overview

## Purpose

Primary worship space with live IMAG and broadcast (livestream) feed. This is the mission-critical production environment.

## Priority Outputs

1. **Livestream** – Primary broadcast feed via SE-3200
2. **IMAG** – In-house magnification for congregation
3. **FOH Audio** – Live sound in room
4. **Recording** – Archive capture

## Signal Flow Summary

### Broadcast Audio Path

```
DM7 Broadcast Bus → Dante → Ableton (processing) → Dante → DM7 → SE-3200 → Stream
```

Total latency: ≈200 ms (dominated by 181 ms plugin chain in Ableton)

### Video Path

```
Cameras → SE-3200 → PGM Output → Encoder → Stream
```

Total latency: ≈150–160 ms

### Sync Compensation

Audio is slower than video by ≈45 ms. SE-3200 audio delay set to **46 ms** to align.

## Key Devices

| Device | Role | Notes |
|--------|------|-------|
| Yamaha DM7 | FOH + Broadcast mixing | 144 ch, Dante clock master |
| Ableton Live (Broadcast PC) | Broadcast audio processing | 181 ms plugin chain |
| Datavideo SE-3200 | Video switcher + stream output | 46 ms audio delay applied |
| Obsidian Onyx NX4 | Lighting console | DMX-512, 20+ fixture types |
| KLANG-IEM | IEM processor | 12 musicians, Dante I/O |
| Yamaha Rio3224-D2 | Stage box | 32 in / 24 out, Dante |
| Yamaha Rio1608-D2 | Stage box | 16 in / 8 out, Dante |
| BCast-Audio (AVIO) | Broadcast DA converter | Dante → analog → SE-3200 |
| Crown CDi 1000 | Foyer amplifier | 70V distributed |
| Biamp Tesira | Hallway DSP | Zone routing from SDI de-embed |
| Blackmagic 40×40 | SDI distribution | Program to hallways/rooms |

## Latency & Sync Summary

| Path | Latency | Notes |
|------|---------|-------|
| Broadcast audio chain | ≈200 ms | DM7 → Dante → Ableton → Dante → DM7 → SE-3200 |
| Video pipeline | ≈150–160 ms | Camera → SE-3200 PGM |
| SE-3200 audio delay | 46 ms | Compensates audio-slower-than-video |
| Net sync error | <5 ms | Within acceptable range |

## Known Issues

- **Sync drift when changing plugin chain** – Any Ableton plugin change shifts broadcast audio latency. Must re-measure and update SE-3200 delay. See [Broadcast Sync](broadcast/sync.md).
- Plugin removal makes audio arrive earlier (increase delay)
- Plugin addition makes audio arrive later (decrease delay)

## Detailed Documentation

### Audio
- [Dante Routing](audio/dante-routing.md) — Network subscriptions
- [DM7 Channel Map](audio/dm7-channel-map.md) — Full 144-channel console map
- [DM7 Processing](audio/dm7-processing.md) — Per-channel EQ/dynamics
- [Output Zones](audio/output-zones.md) — Physical signal flow to rooms
- [Audio Routing](audio/routing.md)
- [Audio Latency](audio/latency.md)

### Broadcast
- [Broadcast Audio](broadcast/audio.md)
- [Broadcast Sync](broadcast/sync.md)

### Lighting
- [Console](lighting/console.md) — Onyx NX4 details
- [Patch](lighting/patch.md) — Fixture inventory and DMX
- [Scenes](lighting/scenes.md) — Cuelists and effects
- [Show Summary](lighting/onyx-show-summary.md) — Full show file extraction

### Video
- [Switcher Settings](video/switcher-settings.md)
- [Camera Layout](video/camera-layout.md)

### Diagrams
- [Dante Topology](../../diagrams/mermaid/dante-full-topology.md)
- [Broadcast Audio Flow](../../diagrams/mermaid/broadcast-audio-flow.md)

## Last Updated

2026-05-24
