# ATEM 2 M/E – LED Wall Switcher Configuration

> **Source:** `ATEM-2ME-Resolume 2026-05-24 17-21-49.xml`  
> **IP:** 10.0.250.87 (VLAN 250)  
> **MAC:** 7c:2e:0d:a8:5d:a8  
> **Export Date:** 2026-05-24

---

## Role

The Blackmagic ATEM 2 M/E is dedicated to **LED wall compositing**. Resolume Arena provides the background visual content (Input 1), and ProPresenter is keyed over it using **DSK 1** (Key on Input 2, Fill on Input 3). The composed output goes to the NovaStar LED wall processor.

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

> SuperSource is available but the **primary compositing method is DSK 1**: ProPresenter Key/Fill is downstream-keyed over the Resolume background.

---

## DSK 1 – Primary Compositing (ProPresenter over Resolume)

| Parameter | Value |
|-----------|-------|
| **DSK 1 Fill** | Input 3 (Pro Presenter Fill) |
| **DSK 1 Key** | Input 2 (Pro Presenter Key) |
| **Function** | Lyrics, lower thirds, and graphics overlaid on Resolume background |

> **Live signal flow:** Resolume (Input 1) → M/E PGM → DSK 1 composites ProPresenter → Output 1 → NovaStar 600 → LED Wall

---

## Mix Effects (M/E) Keyers

Both ME 1 and ME 2 have 4 keyers configured (default/unused at export time):

| ME | Key | Type | Fill Source | Cut Source | On Air |
|----|-----|------|------------|------------|--------|
| 1 | 0–3 | Luma | Media Player | Media Player Key | Off |
| 2 | 0–3 | Luma | Media Player | Media Player Key | Off |

---

## DSK 2

| DSK | Status |
|-----|--------|
| DSK 2 | Available (not assigned) |

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
Resolume Arena (Mac Studio) ──SDI──→ ATEM Input 1 ──→ M/E PGM (background)
														  │
													   DSK 1
													 (key/fill)
														  ↑
ProPresenter (Mac Mini) ──SDI Key──→ ATEM Input 2 ────────┤
ProPresenter (Mac Mini) ──SDI Fill──→ ATEM Input 3 ───────┘
														  │
													ATEM Output 1
														  │
												   NovaStar 600
													(10.0.250.26)
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
