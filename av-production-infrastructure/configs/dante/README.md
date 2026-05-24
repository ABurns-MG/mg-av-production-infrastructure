# Dante Network – Main Sanctuary

## Overview

The Main Sanctuary Dante network carries all digital audio between the mixing console, playback/processing workstations, stage boxes, and other audio devices. This is the primary audio transport layer.

## Network Configuration

| Parameter | Value |
|-----------|-------|
| Clock Master | Y001-Yamaha-DM7-c9a984 (Yamaha DM7) |
| Clock Type | PTPv1 (Dante default) |
| Sample Rate | 48 kHz |
| Dante Latency | 4 ms per hop (default) |
| Total Devices | 20+ |

## Device Inventory

### Confirmed Devices

| Device Name | Model | Type | Role | Channels (TX/RX) |
|-------------|-------|------|------|-------------------|
| Y001-Yamaha-DM7-c9a984 | Yamaha DM7 | Console | Clock Master, FOH + Broadcast mixing | TBD |
| MGC-LC-L-AVL-001 | Dante Virtual Soundcard (macOS) v4.5.1 | Workstation | Ableton Live – playback & broadcast processing | 32 TX / 32 RX |

### Pending Documentation (Full Export Required)

> **Note:** There are 20+ devices on this Dante network. The full routing export (with subscriptions) will populate this table completely. Use Dante Controller → File → Save Preset (with "Include subscriptions" and "Include all devices" checked).

| Device Name | Model | Type | Role | Channels (TX/RX) |
|-------------|-------|------|------|-------------------|
| (To be documented from full export) | | | | |

## Clock Hierarchy

```
┌─────────────────────────────────┐
│  Y001-Yamaha-DM7-c9a984        │
│  (Preferred Clock Master)       │
└───────────────┬─────────────────┘
				│ PTPv1
	┌───────────┼───────────────────────┐
	│           │                       │
	▼           ▼                       ▼
MGC-LC-L-AVL-001   [Device 3]      [Device N]
(Ableton DVS)      (TBD)           (TBD)
```

## Network Topology

(To be documented – switch model, VLAN configuration, redundancy)

| Component | Details |
|-----------|---------|
| Primary switch | TBD |
| Secondary/redundant | TBD |
| VLAN | TBD |
| QoS | TBD |

## Preset Files in This Directory

| File | Description | Date |
|------|-------------|------|
| MGC-LC-Ableton Dante Channel Names.xml | Ableton DVS channel labels (TX + RX) | Current |
| (Full routing preset pending) | All devices + subscriptions | Pending |

## Key Routing Paths

| Path | Source Device | Destination Device | Purpose |
|------|--------------|-------------------|---------|
| DM7 → Ableton | Y001-Yamaha-DM7-c9a984 | MGC-LC-L-AVL-001 | Individual channels for playback/processing |
| Ableton → DM7 | MGC-LC-L-AVL-001 | Y001-Yamaha-DM7-c9a984 | Processed audio + broadcast stereo return |

## Related Documents

- [Dante Routing (Main Sanctuary)](../../systems/main-sanctuary/audio/dante-routing.md) – Channel-level detail
- [Audio Routing](../../systems/main-sanctuary/audio/routing.md) – Full audio signal paths
- [Broadcast Audio](../../systems/main-sanctuary/broadcast/audio.md) – Broadcast audio flow
- [Dante Network Diagram](../../diagrams/mermaid/dante-network-overview.md) – Visual topology
