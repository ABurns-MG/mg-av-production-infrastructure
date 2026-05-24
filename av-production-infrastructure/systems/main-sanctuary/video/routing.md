# Main Sanctuary – Video Routing

> **Source:** UniFi client inventory + Datavideo SE-3200 configuration  
> **Last Updated:** 2026-05-24

---

## Signal Flow

```
PTZ Cameras (×4, VLAN 110) ──SDI/IP──→ Datavideo SE-3200 ──PGM──→ Streaming / LED Wall / IMAG
                                              ↑
                    Panasonic AW-RP150 ───── Control (VISCA/IP)
```

---

## Camera Network (VLAN 110 – 192.168.0.0/24)

| Device | IP | MAC | Manufacturer | Role |
|--------|-----|-----|--------------|------|
| **Panasonic AW-RP150** | 192.168.0.9 | a8:13:74:c5:33:96 | Panasonic | PTZ remote controller |
| **Remote Stream Camera 1** | 192.168.0.12 | a8:13:74:c5:1d:17 | Panasonic | PTZ camera |
| **Remote Stream Camera 2** | 192.168.0.13 | a8:13:74:c5:1d:69 | Panasonic | PTZ camera |
| **Remote Stream Camera 3** | 192.168.0.14 | a8:13:74:c6:55:bd | Panasonic | PTZ camera |
| **Camera 4** | 192.168.0.15 | a8:13:74:c6:55:bb | Panasonic | Remote cam (booth) |
| **Datavideo SE-3200** | 192.168.0.101 | 00:07:36:0a:85:c8 | Datavideo | HD video switcher |

---

## Inputs (SE-3200)

| Input # | Source | Connection | IP | Notes |
|---------|--------|------------|-----|-------|
| 1 | Remote Stream Camera 1 | SDI | 192.168.0.12 | PTZ – controlled via AW-RP150 |
| 2 | Remote Stream Camera 2 | SDI | 192.168.0.13 | PTZ – controlled via AW-RP150 |
| 3 | Remote Stream Camera 3 | SDI | 192.168.0.14 | PTZ – controlled via AW-RP150 |
| 4 | Camera 4 | SDI | 192.168.0.15 | Booth camera – controlled via AW-RP150 |

> **Note:** Additional non-IP inputs (graphics, playback) may occupy other SE-3200 inputs — document as discovered.

---

## Outputs (SE-3200)

| Output # | Destination | Connection | Notes |
|----------|-------------|------------|-------|
| PGM | Livestream encoder | SDI | Primary program output |
| PGM | LED Wall (NovaStar) | SDI/HDMI | IMAG feed to NovaStar processor |
| AUX | Confidence monitors | SDI | Stage confidence / green room |
| Audio embed | BCast-Audio (AVIO-DAO2) | Analog from DM7 TX 63-64 | 46 ms delay compensation applied in SE-3200 |

---

## Control

- **PTZ Controller:** Panasonic AW-RP150 at `192.168.0.9`
- **Protocol:** VISCA over IP (VLAN 110)
- **All 4 cameras** are registered to the RP150 for preset recall and live control during broadcast.

---

## Related Documents

- [Camera Layout](camera-layout.md) — physical positions and shot assignments
- [Broadcast Sync](../broadcast/sync.md) — audio/video delay compensation
- [AVL Network Clients](../../../configs/network/avl-clients.md) — full device inventory
- [Switcher Settings](switcher-settings.md) — SE-3200 configuration details
