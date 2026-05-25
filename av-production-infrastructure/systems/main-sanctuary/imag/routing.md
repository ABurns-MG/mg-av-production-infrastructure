# Main Sanctuary – IMAG Routing

> **Last Updated:** 2026-05-24

---

## Signal Flow

```
Resolume Arena (Mac Studio) ──SDI──→ ATEM 2M/E (Input 1)
ProPresenter (Mac Mini) ──SDI Key/Fill──→ ATEM 2M/E (Input 2-3)
                                              │
                                         SuperSource 1
                                         (compositing)
                                              │
                                         ATEM Output 1 ──SDI──→ NovaStar ──→ LED Wall
                                                                (10.0.250.26)

SE-3200 PGM ──SDI──→ (available ATEM Input 4 for IMAG overlay)

MVX Controller ──→ LED Wall (video mapping)
   (10.0.250.172)
```

---

## Displays

| Display | Location | Processor | Processor IP | Notes |
|---------|----------|-----------|--------------|-------|
| LED Wall | Stage center | NovaStar | 10.0.250.26 | 2816×1024 ultra-wide, fed from ATEM SS1 |

---

## ATEM 2 M/E Input Routing

| Input | Source | Content |
|-------|--------|---------|
| 1 (RES1) | Resolume Arena (Mac Studio) | Motion backgrounds, worship visuals |
| 2 (PPSK) | ProPresenter Key | Alpha/transparency channel |
| 3 (PPSF) | ProPresenter Fill | Lyrics, lower thirds, graphics |
| 4 (CAM4) | Available | IMAG camera / SE-3200 PGM |

---

## Video Processing Chain

| Device | IP | MAC | Role |
|--------|-----|-----|------|
| Resolume Mac Studio | DHCP (Dante) | 9c:76:0e:3a:58:5f | Visual content engine (Arena 7.25.2) |
| ProPresenter Mac Mini | 192.168.10.79 (Dante) | 20:a5:cb:ca:81:6a | Lyrics/graphics (DeckLink Duo 2, 1080p60) |
| ATEM 2M/E | 10.0.250.87 | 7c:2e:0d:a8:5d:a8 | SuperSource compositing |
| NovaStar Processor | 10.0.250.26 | 54:b5:6c:0c:1f:b1 | LED wall scaler/processor |
| MVX Controller | 10.0.250.172 | 18:30:24:00:74:17 | LED wall video mapping |
| Datavideo SE-3200 | 192.168.0.101 | 00:07:36:0a:85:c8 | Livestream switcher (PGM available as ATEM input) |

---

## Related Documents

- [ATEM 2 M/E Config](../../../configs/switchers/atem-2me-config.md) — Full ATEM settings
- [Resolume Composition](../../../configs/video/resolume-composition.md) — Arena deck/layer structure
- [Video Routing](../video/routing.md) — Camera to SE-3200
- [Switcher Settings](../video/switcher-settings.md) — SE-3200 config
- [IMAG Delay Alignment](delay-alignment.md) — sync with live audio
