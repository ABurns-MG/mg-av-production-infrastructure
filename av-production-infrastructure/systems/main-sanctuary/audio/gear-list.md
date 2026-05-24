# Main Sanctuary – Audio Gear List

> **Source:** UniFi client inventory, Dante XML, DM7 Editor cache  
> **Last Updated:** 2026-05-24

---

## Mixing

| Item | Model | Location | IP / Network | Notes |
|------|-------|----------|--------------|-------|
| FOH Console | Yamaha DM7 | FOH booth | 192.168.10.138 (Dante), 10.0.250.31 (Mgmt) | Clock master, 144 TX/RX |
| Control Surface | Yamaha CS-R10 (CM7) | FOH booth | 10.0.250.30 | Add-on surface for DM7 |
| Allen & Heath ME Card | Brooklyn II (Dante) | AVL rack | 192.168.10.22 | IEM backup / recorder |

## Stage Boxes

| Item | Model | Location | IP | Notes |
|------|-------|----------|-----|-------|
| Instruments | Yamaha Rio3224-D2 | AVL rack | 192.168.10.149 | 32 TX / 24 RX |
| Drums | Yamaha Rio1608-D2 | Drum riser | 192.168.10.238 | 16 TX / 8 RX |

## Wireless Microphones

| Item | Model | Location | IP | Notes |
|------|-------|----------|-----|-------|
| Receiver 1 | Shure ULXD4Q | AVL rack | 192.168.10.59 (Dante), 10.0.250.174 (Mgmt) | FL1, HDST-2, FL3, FL4 |
| Receiver 2 | Shure ULXD4Q | AVL rack | — | FL5, FL6, FL7, HDST-1 (Pastor) |

## IEM / Monitor Processing

| Item | Model | Location | IP | Notes |
|------|-------|----------|-----|-------|
| IEM Processor | KLANG (DiGiCo DMI DANTE 64@96z) | AVL rack | DHCP (Dante), 10.10.20.232 (Mgmt) | 64 TX/RX, personalized stereo mixes |
| IEM Adapters (×12) | Audinate AVIO-DAO2 | Stage / musician positions | DHCP | Stereo receive-only from KLANG |
| Broadcast Output | Audinate AVIO-DAO2 | AVL rack | DHCP | Analog out to SE-3200 |

## Workstations (Dante Virtual Soundcard)

| Item | Model | Location | IP | Role |
|------|-------|----------|-----|------|
| Broadcast Processing | Mac Mini (Ableton Live) | FOH booth | 192.168.10.10 | Broadcast audio processing (181 ms plugin chain) |
| ProPresenter Audio | Mac Mini | FOH booth | 192.168.10.79 | Presentation audio (2ch) |
| Resolume Audio | Mac Studio | FOH booth | DHCP | Video playback audio (2ch) |
| Multitrack Playback | MacBook Pro (JD) | Stage / FOH | — | 30ch stems (worship leader) |
| Backup Playback | Mac Mini | FOH booth | — | 30ch stems (secondary) |

## Zone DSP

| Item | Model | Location | IP | Notes |
|------|-------|----------|-----|-------|
| Zone Processor | BSS London | AVL rack | 10.0.250.98 | Zone DSP for lobbies/overflow |

## Networking (Audio)

| Item | Model | VLAN | Notes |
|------|-------|------|-------|
| Dante audio transport | VLAN 130 | 192.168.10.0/24 | IGMP snooping, all Dante devices |
| AVL management | VLAN 250 | 10.0.250.0/24 | Console control, device management |

