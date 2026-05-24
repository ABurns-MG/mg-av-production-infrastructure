# Main Sanctuary – Audio Routing

## Overview

All audio signal paths for the Main Sanctuary including Dante network audio, analog connections, and processing inserts.

## Dante Routing

### Summary

The Main Sanctuary Dante network carries 24 channels from DM7 → Ableton and 25 channels from Ableton → DM7. Full channel-level detail is in the [Dante Routing](dante-routing.md) document.

### DM7 → Ableton (24 active channels)

| Category | Channels | Signals |
|----------|----------|---------|
| Drums | RX 1-5 | Kick, Snare, Rack 1, Rack 2, Floor Tom |
| Keys | RX 6-7, 13-14 | Keys 2 L/R, Keys L/R |
| Instruments | RX 9, 11-12, 15 | Bass, EG 1, EG 2, Acoustic |
| Vocals | RX 16-20 | FL1, FL2, FL3, FL4, FL5 |
| Speech | RX 21-22 | MC1, Pastor |
| Ambient | RX 23-24 | Crowd 1, Crowd 2 |
| Utility | RX 8 | Click |

### Ableton → DM7 (25 active channels)

| Category | Channels | Signals |
|----------|----------|---------|
| Vocals | TX 1-5 | FL1-5 (processed) |
| Speech | TX 6-7 | Pastor, MC1 (processed) |
| Ambient | TX 8-9 | Crowd 1-2 (processed) |
| Instruments | TX 10-13 | Bass, Acoustic, EG1, EG2 (processed) |
| Drums | TX 14-17 | Kick, Snare, Rack 1, Rack 2 (processed) |
| Keys | TX 18-21 | Keys L/R, Keys 2 L/R (processed) |
| FX | TX 22-25 | FL1-4 FX returns |

### Broadcast Audio Path

| Channel | Source | Destination | Notes |
|---------|--------|-------------|-------|
| DM7 Direct Outs (24ch) | DM7 | Broadcast PC (Ableton) | Dante send, 4 ms |
| Ableton Returns (25ch) | Broadcast PC (Ableton) | DM7 | Dante return, 4 ms |
| Broadcast Bus | DM7 | SE-3200 Audio Input | Final broadcast feed |

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
| Dante Clock Master | Y001-Yamaha-DM7-c9a984 (DM7) | Preferred master, PTPv1 |
| Sample Rate | 48 kHz | All devices synced |

## Related Documents

- [Dante Routing (Channel Detail)](dante-routing.md) – Full channel maps per device
- [Dante Network Overview](../../configs/dante/README.md) – All devices and clock config
- [Audio Latency](latency.md) – Measured latency per segment
- [Broadcast Sync](../broadcast/sync.md) – A/V sync compensation
- [Broadcast Audio Flow Diagram](../../diagrams/mermaid/broadcast-audio-flow.md) – Mermaid diagrams
- [Console Settings](console-settings.md) – DM7 configuration
