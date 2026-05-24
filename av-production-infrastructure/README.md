# MercyGate Church – AV Production Infrastructure

> **Branch:** `feat/av-production-infrastructure`  
> **Last Updated:** 2026-05-24  
> **Maintainer:** AVL Team

The single source of truth for all audio, video, lighting, and broadcast systems at MercyGate Church. Every signal path, IP address, channel assignment, and configuration change is tracked here so the production environment is reproducible, debuggable, and trainable.

---

## Getting Started

### For New Technicians

1. **Start with the [Main Sanctuary Overview](systems/main-sanctuary/overview.md)** — high-level system map, key devices, and latency summary.
2. **Trace a signal:** Pick any source (e.g., a vocal mic) and follow it through:
   - [DM7 Channel Map](systems/main-sanctuary/audio/dm7-channel-map.md) — find the console channel
   - [Dante Routing](systems/main-sanctuary/audio/dante-routing.md) — see how it gets there over the network
   - [Output Zones](systems/main-sanctuary/audio/output-zones.md) — see where it goes (FOH, IEM, broadcast, etc.)
3. **Understand the network:** [UniFi Network](configs/network/unifi-network.md) shows VLANs, and [AVL Clients](configs/network/avl-clients.md) maps every device IP.

### For Troubleshooting

| Problem | Start Here |
|---------|-----------|
| Audio not reaching broadcast | [Output Zones](systems/main-sanctuary/audio/output-zones.md) → Zone 4 (Broadcast) |
| IEM musician can't hear | [Output Zones](systems/main-sanctuary/audio/output-zones.md) → Zone 3 (IEM) |
| Audio/video out of sync | [Broadcast Sync](systems/main-sanctuary/broadcast/sync.md) |
| Device offline on Dante | [AVL Clients](configs/network/avl-clients.md) — verify IP and VLAN 130 |
| Lighting fixture not responding | [Lighting Patch](systems/main-sanctuary/lighting/patch.md) |
| Network connectivity issue | [UniFi Network](configs/network/unifi-network.md) — check VLAN and switch |

### For AI Agents / Automation

This repository is designed to be machine-readable. Key extraction guides:
- [DM7 AppData Extraction](configs/dm7/README-extraction-guide.md) — PowerShell workflow to read Yamaha console data
- [Onyx Show File Extraction](configs/lighting/README-extraction-guide.md) — How to parse `.OnyxShow` files
- [Network Controller Access](configs/network/README-access-guide.md) — SSH + MongoDB query patterns

---

## Repository Structure

```
av-production-infrastructure/
├── systems/                          # Per-room documentation
│   └── main-sanctuary/
│       ├── overview.md               # System summary + device list
│       ├── audio/
│       │   ├── dante-routing.md      # Complete Dante subscription map
│       │   ├── dm7-channel-map.md    # 144-channel console map + DCAs
│       │   ├── dm7-processing.md     # Per-channel EQ/dynamics/compressors
│       │   └── output-zones.md       # Physical signal flow (9 zones)
│       ├── broadcast/
│       │   └── sync.md              # Audio/video sync + 46ms compensation
│       ├── lighting/
│       │   ├── console.md           # Onyx NX4 programming
│       │   ├── patch.md             # Fixture inventory + DMX addressing
│       │   └── scenes.md           # Cuelists + effects
│       └── video/
│           └── ...
├── configs/                          # Raw exports + extraction guides
│   ├── dante/                       # Dante Controller XML exports
│   ├── dm7/                         # DM7 scene files + extraction guide
│   ├── lighting/                    # Onyx show files + extraction guide
│   └── network/                     # UniFi network docs + access guide
├── diagrams/mermaid/                 # Visual topology diagrams
├── standards/                        # Naming conventions, latency standards
└── troubleshooting/                  # Known issues + solutions
```

---

## Systems Covered

| System | Status | Key Docs |
|--------|--------|----------|
| **Main Sanctuary** | ✅ Documented | [Overview](systems/main-sanctuary/overview.md) |
| Kids Ministry | 🔲 Pending | — |
| Youth | 🔲 Pending | — |
| Event Center | 🔲 Pending | — |

---

## Network Quick Reference

| VLAN | Subnet | Purpose | Key Devices |
|------|--------|---------|-------------|
| **130** | 192.168.10.0/24 | Dante Audio | DM7, Rio, KLANG, AVIO, ULXD, workstations |
| **250** | 10.0.250.0/24 | AVL Control | DM7 console, NX4, LED wall, DSP |
| **110** | 192.168.0.0/24 | Camera Control | PTZ cameras, AW-RP150, SE-3200 |
| **150** | 192.172.150.0/24 | NDI Video | NDI cameras/sources |

Full details: [UniFi Network](configs/network/unifi-network.md) | [AVL Clients](configs/network/avl-clients.md)

---

## Equipment Summary

### Audio
| Device | VLAN 130 IP | VLAN 250 IP | Role |
|--------|-------------|-------------|------|
| Yamaha DM7 | 192.168.10.138 | 10.0.250.31 | FOH + Broadcast console (clock master) |
| CS-R10/CM7 Surface | — | 10.0.250.30 | DM7 expansion control surface |
| Rio3224-D2 | 192.168.10.149 | — | Stage box (instruments, 32in/24out) |
| Rio1608-D2 | 192.168.10.238 | — | Stage box (drums, 16in/8out) |
| KLANG-IEM | DHCP | — | IEM processor (12 musicians) |
| Allen & Heath ME Card | 192.168.10.22 | — | Backup IEM (ME-1 system) |
| Shure ULXD4Q | 192.168.10.59 | 10.0.250.174 | Wireless mic receivers |
| BCast-Audio (AVIO) | DHCP | — | Broadcast DA → SE-3200 |

### Processing & Playback
| Device | VLAN 130 IP | Role |
|--------|-------------|------|
| AVL-Broadcast-Mac | 192.168.10.10 | Ableton broadcast processing |
| Resolume Mac Studio | DHCP | Video playback + Spotify audio |
| ProPresenter Mac Mini | 192.168.10.79 | Presentation audio |

### Video
| Device | VLAN 110 IP | Role |
|--------|-------------|------|
| Datavideo SE-3200 | 192.168.0.101 | Video switcher (+46ms audio delay) |
| Panasonic AW-RP150 | 192.168.0.9 | PTZ controller |
| PTZ Cameras (×4) | .12, .13, .14, .15 | Remote cameras |

### Lighting & LED
| Device | VLAN 250 IP | Role |
|--------|-------------|------|
| Onyx NX4 Lighting PC | 10.0.250.49 | DMX-512 lighting console |
| NovaStar LED Processor | 10.0.250.26 | LED wall processing |
| ATEM 2M/E | 10.0.250.87 | LED wall super source |
| MVX LED Controller | 10.0.250.172 | LED wall video control |

### DSP & Distribution
| Device | IP | Role |
|--------|-----|------|
| BSS London DSP | 10.0.250.98 | Zone processing |
| DLive C3500 | 192.168.10.5 / 10.0.250.8 | Allen & Heath console (dual NIC) |
| Blackmagic Cloud Store | 10.10.20.7 | 20TB media storage |

---

## Key Principles

1. **Version Control Everything** — All routing, latency, or config changes are committed with descriptive messages.
2. **Measure, Don't Assume** — Latency and sync values are based on real-world measurement, not spec sheets.
3. **Document Signal Flow Clearly** — If you can't trace a signal in under 2 minutes, the docs are incomplete.
4. **Keep It Practical** — Documentation should help fix problems during a live service.
5. **Small Commits** — Each change is a focused, human-digestible commit for easy review.

---

## Contribution Guidelines

- Follow [naming conventions](standards/naming-conventions.md)
- Include Mermaid diagrams for any new signal path
- Document *why* (rationale), not just *what* (settings)
- When updating configs, also update the corresponding `.md` documentation
- Test signal paths after any routing change and update latency measurements

---

## Related Extraction Workflows

| System | Guide | Source Data |
|--------|-------|-------------|
| Yamaha DM7 | [Extraction Guide](configs/dm7/README-extraction-guide.md) | AppData cache (PowerShell) |
| Onyx NX4 | [Extraction Guide](configs/lighting/README-extraction-guide.md) | .OnyxShow ZIP → MDF (7-Zip + regex) |
| UniFi Network | [Access Guide](configs/network/README-access-guide.md) | SSH → MongoDB (base64 queries) |
| Dante Controller | Export `.xml` from Dante Controller → `configs/dante/` | Direct XML parse |
| Shure WWB7 | Pending `.wwb7` upload | XML-based project file |
| Biamp Tesira | Pending `.tsc` export | TBD |
