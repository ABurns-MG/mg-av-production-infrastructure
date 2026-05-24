# Main Sanctuary – Dante Routing

## Overview

Channel-level Dante routing for the Main Sanctuary. This document maps all Dante transmit and receive channels per device with their signal assignments.

## Device: MGC-LC-L-AVL-001 (Ableton Live – Dante Virtual Soundcard)

**Model:** Dante Virtual Soundcard (macOS) v4.5.1  
**Role:** Playback, multitrack processing, broadcast audio processing  
**Capacity:** 32 TX / 32 RX

### Transmit Channels (Ableton → Network)

These channels are sent FROM Ableton TO other Dante devices (primarily DM7).

| Dante ID | Label | Signal | Category | Notes |
|----------|-------|--------|----------|-------|
| 1 | FL1 | Front Line Vocal 1 (processed) | Vocals | Processed return |
| 2 | FL2 | Front Line Vocal 2 (processed) | Vocals | Processed return |
| 3 | FL3 | Front Line Vocal 3 (processed) | Vocals | Processed return |
| 4 | FL4 | Front Line Vocal 4 (processed) | Vocals | Processed return |
| 5 | FL5 | Front Line Vocal 5 (processed) | Vocals | Processed return |
| 6 | Pastor | Pastor mic (processed) | Speech | Processed return |
| 7 | MC1 | MC / Host mic (processed) | Speech | Processed return |
| 8 | Crowd 1 | Crowd mic 1 (processed) | Ambient | Processed return |
| 9 | Crowd 2 | Crowd mic 2 (processed) | Ambient | Processed return |
| 10 | Bass | Bass (processed) | Instruments | Processed return |
| 11 | Acoustic | Acoustic guitar (processed) | Instruments | Processed return |
| 12 | EG1 | Electric Guitar 1 (processed) | Instruments | Processed return |
| 13 | EG2 | Electric Guitar 2 (processed) | Instruments | Processed return |
| 14 | Kick | Kick drum (processed) | Drums | Processed return |
| 15 | Snare | Snare drum (processed) | Drums | Processed return |
| 16 | Rack 1 | Rack tom 1 (processed) | Drums | Processed return |
| 17 | Rack 2 | Rack tom 2 (processed) | Drums | Processed return |
| 18 | Keys L | Keys 1 Left (processed) | Keys | Processed return |
| 19 | Keys R | Keys 1 Right (processed) | Keys | Processed return |
| 20 | Keys 2L | Keys 2 Left (processed) | Keys | Processed return |
| 21 | Keys 2R | Keys 2 Right (processed) | Keys | Processed return |
| 22 | FL1 FX | Front Line 1 FX send | FX | Vocal effect return |
| 23 | FL2 FX | Front Line 2 FX send | FX | Vocal effect return |
| 24 | FL3 FX | Front Line 3 FX send | FX | Vocal effect return |
| 25 | FL4 FX | Front Line 4 FX send | FX | Vocal effect return |
| 26 | 26 | (Unassigned) | — | Available |
| 27 | 27 | (Unassigned) | — | Available |
| 28 | 28 | (Unassigned) | — | Available |
| 29 | 29 | (Unassigned) | — | Available |
| 30 | 30 | (Unassigned) | — | Available |
| 31 | 31 | (Unassigned) | — | Available |
| 32 | 32 | (Unassigned) | — | Available |

### Receive Channels (Network → Ableton)

These channels are received BY Ableton FROM other Dante devices (primarily DM7 direct outs).

| Dante ID | Label | Signal | Category | Notes |
|----------|-------|--------|----------|-------|
| 1 | Kick | Kick drum (direct out from DM7) | Drums | |
| 2 | Snare | Snare drum | Drums | |
| 3 | Rack 1 | Rack tom 1 | Drums | |
| 4 | Rack 2 | Rack tom 2 | Drums | |
| 5 | Floor Tom | Floor tom | Drums | |
| 6 | Key2 L | Keys 2 Left | Keys | |
| 7 | Key2 R | Keys 2 Right | Keys | |
| 8 | Click | Click track | Utility | Tempo reference |
| 9 | Bass | Bass | Instruments | |
| 10 | Spare | (Spare/unassigned) | — | Available |
| 11 | EG 1 | Electric Guitar 1 | Instruments | |
| 12 | EG 2 | Electric Guitar 2 | Instruments | |
| 13 | Keys L | Keys 1 Left | Keys | |
| 14 | Keys R | Keys 1 Right | Keys | |
| 15 | Acoustic | Acoustic guitar | Instruments | |
| 16 | FL1 | Front Line Vocal 1 | Vocals | |
| 17 | FL2 | Front Line Vocal 2 | Vocals | |
| 18 | FL3 | Front Line Vocal 3 | Vocals | |
| 19 | FL4 | Front Line Vocal 4 | Vocals | |
| 20 | FL5 | Front Line Vocal 5 | Vocals | |
| 21 | MC1 | MC / Host mic | Speech | |
| 22 | Pastor | Pastor mic | Speech | |
| 23 | Crowd1 | Crowd mic 1 | Ambient | |
| 24 | Crowd2 | Crowd mic 2 | Ambient | |
| 25 | 25 | (Unassigned) | — | Available |
| 26 | 26 | (Unassigned) | — | Available |
| 27 | 27 | (Unassigned) | — | Available |
| 28 | 28 | (Unassigned) | — | Available |
| 29 | 29 | (Unassigned) | — | Available |
| 30 | 30 | (Unassigned) | — | Available |
| 31 | 31 | (Unassigned) | — | Available |
| 32 | 32 | (Unassigned) | — | Available |

### Channel Summary

| Category | RX Count (into Ableton) | TX Count (out of Ableton) |
|----------|------------------------|--------------------------|
| Vocals (FL1-5) | 5 | 5 |
| Speech (Pastor, MC1) | 2 | 2 |
| Drums | 5 | 4 |
| Instruments (Bass, EG, Acoustic) | 4 | 4 |
| Keys | 4 | 4 |
| Ambient (Crowd) | 2 | 2 |
| FX Returns | 0 | 4 |
| Utility (Click) | 1 | 0 |
| **Active Total** | **23** | **25** |
| Available | 8 | 7 |

---

## Device: Y001-Yamaha-DM7-c9a984 (Yamaha DM7)

**Role:** FOH mixing, broadcast bus, clock master  
**Dante Status:** Clock Master (PTPv1)

### Transmit Channels (DM7 → Network)

> Pending full routing export. Based on Ableton RX channels, the DM7 sends at minimum:
> Kick, Snare, Rack 1, Rack 2, Floor Tom, Keys 2 L/R, Click, Bass, EG 1, EG 2, Keys L/R, Acoustic, FL1-5, MC1, Pastor, Crowd 1-2 (23 channels)

### Receive Channels (Network → DM7)

> Pending full routing export. Based on Ableton TX channels, the DM7 receives at minimum:
> FL1-5, Pastor, MC1, Crowd 1-2, Bass, Acoustic, EG1-2, Kick, Snare, Rack 1-2, Keys L/R, Keys 2L/R, FL1-4 FX (25 channels)

---

## Other Devices (Pending Full Export)

> There are 20+ additional Dante devices on this network. This section will be populated when the full routing preset (with subscriptions) is exported from Dante Controller.

### Template for Each Device

```
## Device: [Device Name]

**Model:**
**Role:**
**Capacity:** TX / RX

### Transmit Channels
| Dante ID | Label | Signal | Subscribed To |
|----------|-------|--------|---------------|

### Receive Channels
| Dante ID | Label | Signal | Source Device | Source Channel |
|----------|-------|--------|---------------|---------------|
```

---

## Routing Matrix Summary

### Confirmed Subscriptions

| Source Device | Source Channel | → | Destination Device | Destination Channel |
|--------------|---------------|---|-------------------|---------------------|
| Y001-Yamaha-DM7-c9a984 | (various direct outs) | → | MGC-LC-L-AVL-001 | RX 1-24 |
| MGC-LC-L-AVL-001 | TX 1-25 | → | Y001-Yamaha-DM7-c9a984 | (various returns) |

### Full Subscription Matrix

> Will be populated from full Dante Controller export with subscriptions enabled.

---

## Related Documents

- [Dante Network Overview](../../configs/dante/README.md) – Device inventory and clock config
- [Audio Routing](routing.md) – Full audio signal paths
- [Broadcast Audio](../broadcast/audio.md) – Broadcast audio flow detail
- [Dante Network Diagram](../../diagrams/mermaid/dante-network-overview.md) – Visual topology
