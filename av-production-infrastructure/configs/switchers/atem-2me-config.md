# ATEM 2 M/E – LED Wall Switcher Configuration

> **Source:** `ATEM-2ME-Resolume 2026-05-24 17-21-49.xml`  
> **IP:** 10.0.250.87 (VLAN 250)  
> **MAC:** 7c:2e:0d:a8:5d:a8  
> **Export Date:** 2026-05-24

---

## Role

The Blackmagic ATEM 2 M/E is dedicated to **LED wall compositing** using SuperSource. It receives Resolume Arena output and ProPresenter key/fill for overlay compositing, then sends the composed output to the NovaStar LED wall processor.

---

## Inputs

| Input # | Short Name | Long Name | Port Type | Source |
|---------|-----------|-----------|-----------|--------|
| 1 | RES1 | Resolume | SDI | Resolume Arena (Mac Studio) — main visual content |
| 2 | PPSK | Pro Presenter Key | SDI | ProPresenter key signal (alpha channel) |
| 3 | PPSF | Pro Presenter Fill | SDI | ProPresenter fill signal (RGB content) |
| 4 | CAM4 | Camera 4 | SDI | Available for IMAG feed |
| 5–20 | CAM5–CM20 | Camera 5–20 | SDI | Unused (default labels) |

> **Active inputs:** Only 1–3 are actively used. Input 4 may receive SE-3200 PGM for IMAG overlay.

---

## Outputs

| Output ID | Short Name | Long Name | Destination |
|-----------|-----------|-----------|-------------|
| 8001 | OUT1 | Output 1 | NovaStar LED wall processor (10.0.250.26) |
| 8002–8012 | OUT2–OT12 | Outputs 2–12 | Available / unused |
| 6000 | SS1 | SuperSource 1 | Internal — composited to PGM |
| 7001 | CFD1 | Clean Feed 1 | Available |
| 7002 | CFD2 | Clean Feed 2 | Available |

---

## SuperSource Configuration

| Parameter | Value |
|-----------|-------|
| Art Fill Input | Media Player (3010) |
| Art Key Input | Media Player Key (3011) |
| Art Option | Background |
| Art Pre-Multiplied | No |
| Art Clip | 50% |
| Art Gain | 70% |

> SuperSource is used to composite Resolume visuals with ProPresenter overlays (lyrics, lower thirds) for the LED wall.

---

## Mix Effects (M/E) Keyers

Both ME 1 and ME 2 have 4 keyers configured:

| ME | Key | Type | Fill Source | Cut Source | On Air |
|----|-----|------|------------|------------|--------|
| 1 | 0–3 | Luma | Media Player | Media Player Key | Off |
| 2 | 0–3 | Luma | Media Player | Media Player Key | Off |

> Keys are pre-configured but not actively on-air at export time. Likely used for DSK overlays during live production.

---

## DSK (Downstream Keyers)

| DSK | Available |
|-----|-----------|
| DSK 1 | Yes (mask configured) |
| DSK 2 | Yes (mask configured) |

---

## MultiView

| MV Index | Layout | Notes |
|----------|--------|-------|
| 0 | 12-window | Primary monitoring |
| 1 | 15-window | Extended monitoring |

---

## Video Format

- Core video modes supported: 720p50 through 1080p60
- Operating at **1080p60** (matching SE-3200 and Resolume output)

---

## Signal Flow

```
Resolume Arena (Mac Studio) ──SDI──→ ATEM Input 1
ProPresenter (Mac Mini) ──SDI Key──→ ATEM Input 2
ProPresenter (Mac Mini) ──SDI Fill──→ ATEM Input 3
										 │
									SuperSource 1
									(compositing)
										 │
									ATEM Output 1 ──SDI──→ NovaStar (10.0.250.26)
															  │
														 LED Wall
```

---

## ProPresenter Mac Mini (DeckLink Duo 2)

From the Blackmagic Desktop Video Status Report:

| Parameter | Value |
|-----------|-------|
| Machine | avlpropresenter-macmini.local |
| Card | DeckLink Duo 2 |
| Output Label | LED Wall Output |
| Video Output | SDI, 1080p60, 8-bit YUV 4:2:2 |
| OS | macOS 13.3.0 |
| RAM | 16 GB |
| CPU | 10 cores (Apple Silicon Mac14,12 = Mac Mini M2 Pro) |

---

## Related Documents

- [IMAG Routing](../../systems/main-sanctuary/imag/routing.md) — Full LED wall signal path
- [Video Routing](../../systems/main-sanctuary/video/routing.md) — Camera to SE-3200
- [AVL Clients](../network/avl-clients.md) — Device IPs
