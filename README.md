# MercyGate Church – AV Production Infrastructure

Version-controlled documentation of all live production systems at MercyGate Church, including audio, video, lighting, and broadcast signal flow, latency analysis, Dante routing maps, network topology, and device configurations.

> **Purpose:** Provide a single source of truth so the production environment is reproducible, debuggable, and trainable — whether onboarding a new volunteer or diagnosing a signal path at 7 AM on Sunday.

---

## Getting Started

1. **[Main Sanctuary Overview](av-production-infrastructure/systems/main-sanctuary/overview.md)** — high-level system map, key devices, and signal flow summary.
2. **[Dante Routing](av-production-infrastructure/systems/main-sanctuary/audio/dante-routing.md)** — complete network audio subscriptions with device cross-reference (MAC ↔ IP).
3. **[DM7 Channel Map](av-production-infrastructure/systems/main-sanctuary/audio/dm7-channel-map.md)** — every console input, its source, and processing.
4. **[Output Zones](av-production-infrastructure/systems/main-sanctuary/audio/output-zones.md)** — FOH, monitors, IEM, broadcast destinations.
5. **[Network Clients](av-production-infrastructure/configs/network/avl-clients.md)** — authoritative device inventory with IPs, MACs, and VLANs.
6. **[UniFi Network](av-production-infrastructure/configs/network/unifi-network.md)** — VLANs, switches, APs, and port profiles.

---

## Repository Structure

```
av-production-infrastructure/
├── systems/                 # Per-room system documentation
│   └── main-sanctuary/
│       ├── audio/           # DM7, Dante routing, output zones
│       ├── broadcast/       # Livestream sync & delay compensation
│       └── lighting/        # Onyx NX4 fixtures, patch, cuelists
├── configs/                 # Device configs & network reference
│   ├── dante/               # Dante Controller exports & clock config
│   ├── dm7/                 # DM7 extraction guide & editor caches
│   ├── lighting/            # Onyx show file extraction guide
│   └── network/             # UniFi VLANs, AVL clients, access guide
├── diagrams/                # Mermaid topology & signal flow diagrams
└── standards/               # Documentation conventions & templates
```

---

## Key Principles

| Principle | Practice |
|-----------|----------|
| **Source of truth** | Every IP, channel, and route is documented from real device exports — not memory. |
| **Reproducible** | A new tech can rebuild understanding from these docs alone. |
| **Auditable** | Git history shows what changed, when, and why. |
| **Secure** | Credentials are never stored in this repo. Access patterns are documented without secrets. |

---

## Quick Network Reference

| VLAN | Subnet | Purpose |
|------|--------|---------|
| 130 | 192.168.10.0/24 | Dante audio (IGMP snooping enabled) |
| 250 | 10.0.250.0/24 | AVL device control & management |
| 110 | 192.168.0.0/24 | Video camera control (VISCA/IP) |

---

## Contributing

- Keep changes small and focused (one logical change per commit).
- Follow the conventions in [`standards/`](av-production-infrastructure/standards/).
- Never commit credentials, passwords, or secret keys.
- When updating device info, cite the extraction source (Dante XML, UniFi MongoDB, DM7 Editor cache, etc.).
