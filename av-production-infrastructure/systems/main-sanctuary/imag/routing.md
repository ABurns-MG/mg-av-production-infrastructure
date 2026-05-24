# Main Sanctuary – IMAG Routing

> **Last Updated:** 2026-05-24

---

## Signal Flow

```
SE-3200 PGM ──SDI/HDMI──→ NovaStar Processor ──→ LED Wall
                              (10.0.250.26)

SE-3200 PGM ──SDI──→ ATEM 2M/E ──→ LED Wall (Super Source)
                       (10.0.250.87)

MVX Controller ──→ LED Wall (video mapping)
   (10.0.250.172)
```

---

## Displays

| Display | Location | Processor | Processor IP | Notes |
|---------|----------|-----------|--------------|-------|
| LED Wall (main) | Stage center | NovaStar | 10.0.250.26 | Primary IMAG + graphics |
| LED Wall (super source) | Stage center | ATEM 2M/E | 10.0.250.87 | Blackmagic super source compositing |

---

## Video Processing Chain

| Device | IP | MAC | Role |
|--------|-----|-----|------|
| Datavideo SE-3200 | 192.168.0.101 | 00:07:36:0a:85:c8 | Switcher PGM output |
| NovaStar Processor | 10.0.250.26 | 54:b5:6c:0c:1f:b1 | LED wall processing |
| ATEM 2M/E | 10.0.250.87 | 7c:2e:0d:a8:5d:a8 | Super source compositing |
| MVX Controller | 10.0.250.172 | 18:30:24:00:74:17 | LED wall video mapping |

---

## Related Documents

- [Video Routing](../video/routing.md) — camera to switcher
- [Switcher Settings](../video/switcher-settings.md) — SE-3200 config
- [IMAG Delay Alignment](delay-alignment.md) — sync with live audio
