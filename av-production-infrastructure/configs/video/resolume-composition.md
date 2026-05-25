# Resolume Arena – LED Wall Composition

> **Source:** `MG BASE 2026.avc` (Resolume Arena 7.25.2)  
> **Export Date:** 2026-05-24  
> **Composition Resolution:** 2816 × 1024  
> **LED Wall Aspect Ratio:** ~2.75:1 (ultra-wide)

---

## Overview

Resolume Arena is the primary visual content engine for the LED wall. It outputs via DeckLink SDI to the ATEM 2 M/E (Input 1), where it's composited with ProPresenter overlays before reaching the NovaStar processor.

---

## Composition Structure

| Parameter | Value |
|-----------|-------|
| Software | Resolume Arena 7.25.2 (build 1976) |
| Output Resolution | 2816 × 1024 |
| Layers | 9 |
| Columns per Deck | 9 (PRESERVICE), 17 (WORSHIP) |
| MIDI Controller | APC 40 MK II |
| Content Resolution | Mixed: 3840×2160 (4K files), 1920×1080 (captures), 1536×1024 |

---

## Decks (Show Segments)

| Deck # | Name | Purpose | Active Layers |
|--------|------|---------|---------------|
| 1 | **PRESERVICE** | Pre-service loops and backgrounds | 1 layer, 8 clips |
| 2 | **WORSHIP** | Worship set visuals | 3 layers, 8+ clips |
| 3 | **ANNOUNCEMENTS** | Announcement graphics | — |
| 4 | **MESSAGE** | Message/sermon visuals | — |

---

## Input Sources (Capture Devices)

The WORSHIP deck uses live camera captures (CaptureDeviceVideoSource at 1920×1080) mixed with pre-rendered 4K content. This allows IMAG camera feeds to be integrated directly into the LED wall composition alongside motion backgrounds.

---

## Output Path

```
Resolume Arena (Mac Studio) ──SDI (DeckLink)──→ ATEM 2M/E Input 1
	Resolution: 2816×1024 → scaled/cropped at ATEM or NovaStar
```

---

## Workstation

| Parameter | Value |
|-----------|-------|
| Machine | Resolume Mac Studio |
| Dante IPs | DHCP (9c:76:0e:3a:58:5f, 9c:76:0e:3f:78:db) |
| Audio Output | 2ch stereo via Dante Virtual Soundcard → DM7 RX 49-50 |
| Video Output | DeckLink SDI → ATEM 2 M/E |

---

## Related Documents

- [ATEM 2 M/E Config](../switchers/atem-2me-config.md) — LED wall compositing switcher
- [IMAG Routing](../../systems/main-sanctuary/imag/routing.md) — Full LED wall signal path
- [Dante Routing](../../systems/main-sanctuary/audio/dante-routing.md) — Resolume audio channels
