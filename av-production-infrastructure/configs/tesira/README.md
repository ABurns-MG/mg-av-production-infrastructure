# Biamp Tesira – Children's Building DSP

> **Source:** Tesira software export (`MercyGate Children's Building Final 12172017_DL260524_16_50_49`)  
> **Firmware:** 3.11.1.3  
> **Export Date:** 2026-05-24  
> **Original Design:** 2017-12-17

---

## System Overview

The Tesira system provides zone audio distribution and source selection for the **Children's Building** (not Main Sanctuary). It handles hallway audio, classroom feeds, foyer distribution, resource room, and pastor's office.

> **Note:** This is a separate system from the Main Sanctuary BSS London (10.0.250.98). The Tesira handles the children's wing independently.

---

## Hardware

| Unit | Model | Hostname | IP | MAC (Control) | Role |
|------|-------|----------|-----|---------------|------|
| 1 | **SERVER-IO** | TesiraServer02986182 | 10.10.20.101 | 00:90:5E:1A:55:7E | Main DSP server (AVB) |
| 2 | **EX-MOD** | EX-MOD-02987774 | 10.10.20.102 | 00:90:5E:1A:57:EC | Rack-mount expander |
| 3 | **EX-OUT** | EX-OUT-02978490 | 10.10.20.103 | 00:90:5E:1A:40:D0 | Remote output expander |

### AVB (Audio Video Bridging) Network

| Unit | AVB Primary MAC | AVB Secondary MAC |
|------|----------------|-------------------|
| SERVER-IO | 00:90:5E:1A:5F:42 | 00:90:5E:1A:5F:43 |
| EX-MOD | 00:90:5E:1A:57:ED | 00:90:5E:1A:57:EE |
| EX-OUT | 00:90:5E:1A:40:D1 | 00:90:5E:1A:40:D2 |

---

## Zone Architecture (Partitions)

| Partition | Zones/Rooms Covered |
|-----------|-------------------|
| **Master** | Global source routing, hallway presets, main input processing |
| **Pastor's Office** | Pastor's office speakers (LR + Sub) |
| **Hallways** | Hall 101, Hall 123, Hall 131, Foyer, Resource Room |
| **Room 5&6** | Classrooms 5 and 6 |
| **Room 1-4** | Classrooms 1 through 4 |

---

## Source Selection

Each zone can select from the following sources:

| Source | Description |
|--------|-------------|
| Computer | Local PC audio input |
| Media Player | Dedicated media playback |
| Room-1 through Room-6 | Cross-feed from other classrooms |
| Worship Center Feed | Main Sanctuary program audio (via videohub SDI de-embed) |

---

## Audio Routing

### Inputs (SERVER-IO)

| Input | Channels | Source |
|-------|----------|--------|
| Input 4 Channel | 4 | Local sources (computer, media player) |
| PCTx Mains | — | PC transmit audio from control software |

### Outputs

| Output Block | Unit | Channels | Destination |
|-------------|------|----------|-------------|
| Output 4 Channel (Partition: Pastor's Office) | EX-OUT (Unit 3) | 4 | Pastor's office LR + Sub + Office speakers |
| Output 6 Channel (Partition: Hallways) | EX-MOD (Unit 2) | 6 | Hall 101, Hall 123, Hall 131, Foyer, Resource Room, + spare |
| Output 1 Channel (Master) | Unit 1 | 1 | Leveler output |

### Matrix Mixing

| Mixer | Size | Partition | Purpose |
|-------|------|-----------|---------|
| Matrix Mixer 12×4 | 12 in / 4 out | Pastor's Office | Source mixing for office zones |
| Matrix Mixer 10×5 | 10 in / 5 out | Hallways | Source mixing for hallways + foyer |

---

## Control (TEC-1 Panels)

| Panel | Location | Function |
|-------|----------|----------|
| TEC-1 "Resource" | Resource Room | Source select + volume for resource room |
| (Additional TEC-1s) | Hallways | Source select per hallway zone |

### Preset Groups

| Preset Button | Scope |
|--------------|-------|
| All Hall Presets | Global reset for all hallway zones |
| Hall 101 Source Presets | Source selection for Hallway 101 |
| Hall 123 Source Presets | Source selection for Hallway 123 |
| Hall 131 Source Presets | Source selection for Hallway 131 |
| Foyer Source Presets | Source selection for Foyer |
| Resource Room Presets | Source selection for Resource Room |
| Pastor's Office Presets | Source selection for Pastor's office |

---

## Network Placement

| Network | Subnet | Devices |
|---------|--------|---------|
| LAN (Native VLAN) | 10.10.20.0/23 | Tesira SERVER-IO (.101), EX-MOD (.102), EX-OUT (.103) |
| AVB (media) | Dedicated AVB stream | MOTU AVB Switch interconnects units |

> The MOTU AVB Switch (pictured in exports) provides the AVB audio transport between Tesira units.

---

## Related Documents

- [Videohub Routing](videohub-routing.md) — SDI distribution (Worship Center Feed to Children's Building)
- [Output Zones](../../systems/main-sanctuary/audio/output-zones.md) — Main Sanctuary zone outputs
- [AVL Clients](../network/avl-clients.md) — Full network inventory
