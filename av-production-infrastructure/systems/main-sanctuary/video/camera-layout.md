# Main Sanctuary – Camera Layout

> **Source:** UniFi client inventory (VLAN 110)  
> **Last Updated:** 2026-05-24

---

## Camera Positions

| Camera | Model | IP | Position | Control | Notes |
|--------|-------|-----|----------|---------|-------|
| Remote Stream Camera 1 | Panasonic PTZ | 192.168.0.12 | TBD | AW-RP150 | Primary stream cam |
| Remote Stream Camera 2 | Panasonic PTZ | 192.168.0.13 | TBD | AW-RP150 | Secondary stream cam |
| Remote Stream Camera 3 | Panasonic PTZ | 192.168.0.14 | TBD | AW-RP150 | Tertiary stream cam |
| Camera 4 | Panasonic PTZ | 192.168.0.15 | Booth | AW-RP150 | Booth/wide cam |

## Controller

| Device | Model | IP | Notes |
|--------|-------|-----|-------|
| PTZ Controller | Panasonic AW-RP150 | 192.168.0.9 | VISCA/IP, controls all 4 cameras |

## Shot List

> **TODO:** Document standard shots (wide, medium, close-up, worship leader, pastor, crowd) and which camera covers each.

| Camera | Preset 1 | Preset 2 | Preset 3 | Notes |
|--------|----------|----------|----------|-------|
| Cam 1 | (TBD) | (TBD) | (TBD) | |
| Cam 2 | (TBD) | (TBD) | (TBD) | |
| Cam 3 | (TBD) | (TBD) | (TBD) | |
| Cam 4 | (TBD) | (TBD) | (TBD) | |

## Notes

- All cameras are on VLAN 110 (192.168.0.0/24) — isolated from audio Dante traffic.
- SDI output from each camera feeds the Datavideo SE-3200 switcher.
- Camera physical positions and preset assignments should be documented during next site visit.

