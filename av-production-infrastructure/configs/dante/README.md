# Dante Network – Main Sanctuary

## Overview

The Main Sanctuary Dante network is a large-scale audio transport system carrying all digital audio between the mixing console, stage boxes, IEM processing, playback workstations, wireless receivers, and broadcast outputs. 16+ active devices, 200+ active channel subscriptions.

## Network Configuration

| Parameter | Value |
|-----------|-------|
| Clock Master | Y001-Yamaha-DM7-c9a984 (Yamaha DM7) |
| Clock Protocol | PTPv1 (Dante default) |
| Sample Rate | 48 kHz (all devices) |
| Bit Depth | 24/32-bit (varies by device) |
| Network | 192.168.10.0/24 |
| VLAN | 2 (Allen & Heath), 3 (Shure ULXD4Q) |

---

## Complete Device Inventory

### Console & Stage Boxes

| # | Device Name | Model | Manufacturer | TX/RX | IP | Role |
|---|-------------|-------|-------------|-------|-----|------|
| 1 | Y001-Yamaha-DM7-c9a984 | DM7 (V1.73) | Yamaha | 144/144 | Dynamic | ★ Clock Master, FOH + Broadcast |
| 2 | Y001-Yamaha-Rio3224-D2-25e264 | Rio3224-D2 (V1.85) | Yamaha | 32/24 | 192.168.10.149 | Stage Box (instruments, keys, choir, crowd) |
| 3 | Y002-Yamaha-Rio1608-D2-28589c | Rio1608-D2 | Yamaha | 16/8 | — | Stage Box (drums) |

### Monitor Processing

| # | Device Name | Model | Manufacturer | TX/RX | Role |
|---|-------------|-------|-------------|-------|------|
| 4 | KLANG-IEM | DiGiCo DMI DANTE 64@96z (V4.2.4) | DiGiCo | 64/64 | IEM mix processor (feeds all musician IEMs) |

### IEM Outputs (Audinate AVIO-DAO2 Adapters)

| # | Device Name | Musician | Source | Latency |
|---|-------------|----------|--------|---------|
| 5 | IEM1-FL5 | Front Line 5 | KLANG-IEM (FL5 L/R) | 1 ms |
| 6 | IEM11-FL1 | Front Line 1 | KLANG-IEM (FL1 L/R) | 1 ms |
| 7 | IEM13-FL6 | Front Line 6 | KLANG-IEM (FL6 L/R) | 1 ms |
| 8 | IEM14-FL3 | Front Line 3 | KLANG-IEM (FL3 L/R) | 1 ms |
| 9 | IEM16-FL4 | Front Line 4 | KLANG-IEM (FL4 L/R) | 1 ms |
| 10 | IEM2-BASS | Bass Player | KLANG-IEM (BASS L/R) | 1 ms |
| 11 | IEM3-EG1 | Electric Guitar 1 | KLANG-IEM (EG1 L/R) | 1 ms |
| 12 | IEM4-EG2 | Electric Guitar 2 | KLANG-IEM (EG2 L/R) | 1 ms |
| 13 | IEM5-FL7 | Front Line 7 | KLANG-IEM (FL7 L/R) | 1 ms |
| 14 | IEM6-FL2 | Front Line 2 | KLANG-IEM (FL2 L/R) | 1 ms |
| 15 | IEM7-KEYS | Keys Player | KLANG-IEM (KEYS L/R) | 1 ms |
| 16 | IEM8-ACOUS | Acoustic Player | KLANG-IEM (ACOUS L/R) | 1 ms |

### Broadcast Output

| # | Device Name | Model | Role | Source |
|---|-------------|-------|------|--------|
| 17 | BCast-Audio | AVIO-DAO2 | Broadcast audio output to SE-3200 | DM7 TX63-64 (Post BCast L/R) |

### Wireless Microphone Receivers (Shure)

| # | Device Name | Model | TX Channels | VLAN |
|---|-------------|-------|-------------|------|
| 18 | ULXD4Q-ea9fd2 | Shure ULXD4Q | FL1, HDST-2, FL3, FL4 | 3 |
| 19 | ULXD4Q-eacb78 | Shure ULXD4Q | FL5, FL6, FL7, HDST-1 | 3 |

### Workstations (Dante Virtual Soundcard)

| # | Device Name | Hardware | DVS Version | Role |
|---|-------------|----------|-------------|------|
| 20 | MG-AVL-Ableton | Mac Mini | 4.5.1 (32-bit) | Primary audio processing (Ableton Live) |
| 21 | JD-MG-MacBook-Pro | MacBook Pro | 4.5.2 (24-bit) | Multitrack playback (30ch stems to DM7) |
| 22 | MultiTrack-Playback-mini | Mac Mini | 4.5.2 (32-bit) | Secondary multitrack playback |
| 23 | Resolume-Mac-Studio | Mac Studio | 4.5.1 (24-bit) | Resolume Arena (video + audio) |
| 24 | ProPresenter-MacMini | Mac Mini | — | ProPresenter (presentation audio) |

### Other

| # | Device Name | Model | Role |
|---|-------------|-------|------|
| 25 | AllenHth-2182fc | Allen & Heath Dante Option Card (Brooklyn II) | Secondary console/recorder (receives full input set from DM7) |

---

## Clock Hierarchy

```
┌─────────────────────────────────────────┐
│  Y001-Yamaha-DM7-c9a984                 │
│  ★ Preferred Clock Master               │
│  External Word Clock: Enabled           │
│  144 TX / 144 RX                        │
└───────────────────┬─────────────────────┘
					│ PTPv1 @ 48 kHz
	┌───────┬───────┼───────┬───────┬──────────────────┐
	│       │       │       │       │                  │
	▼       ▼       ▼       ▼       ▼                  ▼
Rio3224  Rio1608  KLANG   Shure   AVIO-DAO2s      Workstations
(stage)  (drums)  (IEM)   (2x)   (13 adapters)   (5 DVS)
```

## Signal Flow Summary

### Input Sources → DM7

| Source Type | Device | Channels |
|-------------|--------|----------|
| Drums (raw) | Rio1608 | 11 ch (Kick×2, Snare×2, HiHat, Toms×4, OH×2) |
| Instruments | Rio3224 | Bass, EG1 L/R, EG2 L/R, Acoustic, Keys L/R, Aux Keys |
| Choir/Crowd | Rio3224 | Choir L/C/R, Crowd L |
| Playback | Rio3224 | Tracks L/R, Click |
| Wireless Mics | ULXD4Q ×2 | FL1-7, HDST-1, HDST-2 (8 channels total) |
| Processed Returns | MG-AVL-Ableton | 22+ channels (drums, instruments, vocals, FX, broadcast) |
| Multitrack | JD-MG-MacBook-Pro | 30 channels (stems) |
| Multitrack 2 | MultiTrack-Playback-mini | 30 channels (stems) |
| Resolume Audio | Resolume-Mac-Studio | 2 channels |
| ProPresenter Audio | ProPresenter-MacMini | 2 channels |

### DM7 → Outputs

| Destination | Device | Channels | Purpose |
|-------------|--------|----------|---------|
| FOH Speakers | Rio3224 RX 1-2 | ST A L/R (TX 135-136) | Main PA |
| Stage Monitors | Rio3224 RX 3-4 | Mon A/B Stage (TX 143-144) | Wedges |
| IEM Processing | KLANG-IEM | 49+ channels | Personal monitor mixes |
| Broadcast Output | BCast-Audio AVIO | 2 ch (TX 63-64) | Post-processed broadcast to SE-3200 |
| Ableton Processing | MG-AVL-Ableton | Via KLANG routing | Channels for processing |
| Allen & Heath | AllenHth-2182fc | 40 channels | Secondary console/recording |

---

## Preset Files in This Directory

| File | Description | Date |
|------|-------------|------|
| Dante-config-20260524.xml | Full network export (all devices + subscriptions) | 2026-05-24 |
| MGC-LC-Ableton Dante Channel Names.xml | Legacy Ableton DVS channel labels | Previous |

## Related Documents

- [Dante Routing (Main Sanctuary)](../../systems/main-sanctuary/audio/dante-routing.md) – Full subscription maps
- [Dante Full Topology Diagram](../../diagrams/mermaid/dante-full-topology.md) – Visual signal flow
- [Broadcast Audio](../../systems/main-sanctuary/broadcast/audio.md) – Broadcast path detail
- [Audio Routing](../../systems/main-sanctuary/audio/routing.md) – All audio signal paths
