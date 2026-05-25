# Blackmagic Videohub – SDI Routing Matrix

> **Source:** `videohub set.txt` (exported from Videohub Smart Control) + UniFi MongoDB  
> **Model:** Blackmagic Smart Videohub 40×40  
> **IP:** 10.10.20.121 | **MAC:** 7c:2e:0d:07:f7:88  
> **Export Date:** 2026-05-24

---

## Overview

The Blackmagic 40×40 SDI router distributes video from the Main Sanctuary and media sources to classrooms, hallways, foyer displays, and utility destinations throughout the facility. Each output feeds a **Blackmagic Teranex Mini** which de-embeds the SDI audio for the Tesira DSP system.

---

## Inputs (Active)

| Input # | Label | Source |
|---------|-------|--------|
| 1 | Classroom 1 | Classroom 1 local source |
| 2 | Classroom 2 | Classroom 2 local source |
| 3 | Classroom 3 | Classroom 3 local source |
| 4 | Classroom 4 | Classroom 4 local source |
| 5 | Classroom 5 | Classroom 5 local source |
| 6 | Classroom 6 | Classroom 6 local source |
| 7 | Display Mac 1 | Mac playback source 1 |
| 8 | Display Mac 2 | Mac playback source 2 |
| 9 | Display Mac 3 | Mac playback source 3 |
| 10 | Display Mac 4 | Mac playback source 4 |
| 12 | **Worship Center Feed** | Main Sanctuary PGM from SE-3200 |
| 13 | Multiview Worship Feed | Multiview output (monitoring) |

> Inputs 11, 14–40 are unused.

---

## Outputs (Active)

| Output # | Label | Destination |
|----------|-------|-------------|
| 1 | Projector 1 | Classroom projector |
| 2 | Projector 2 | Classroom projector |
| 3 | Projector 3 | Classroom projector |
| 4 | Projector 4 | Classroom projector |
| 5 | Projector 5 | Classroom projector |
| 6 | Projector 6 | Classroom projector |
| 7 | Classroom TV1 | Classroom display |
| 8 | Classroom TV2 | Classroom display |
| 9 | Classroom TV3 | Classroom display |
| 10 | Classroom TV4 | Classroom display |
| 11 | Classroom TV5 | Classroom display |
| 12 | Classroom TV6 | Classroom display |
| 13 | Foyer TV1 | Main foyer display |
| 14 | Foyer TV2 | Main foyer display |
| 15 | Kids Check in TV1 | Children's check-in area |
| 16 | Kids Check in TV2 | Children's check-in area |
| 17 | Nursery Lobby TV | Nursery lobby |
| 18 | Nursing Mothers TV | Nursing mothers room |
| 19 | Pastors Office | Pastor's office display |
| 40 | Mac Mini Audio | Audio de-embed to Mac Mini |

> Outputs 20–39 are unused.

---

## Key Routing Paths

| Source → Destination | Purpose |
|---------------------|---------|
| Worship Center Feed → Foyer TV1/TV2 | Livestream simulcast in foyer |
| Worship Center Feed → Nursery Lobby TV | Service feed for nursery parents |
| Worship Center Feed → Nursing Mothers TV | Service feed for nursing room |
| Worship Center Feed → Pastors Office | Pastor's office monitor |
| Worship Center Feed → Mac Mini Audio (Out 40) | SDI audio de-embed for Tesira/zone audio |
| Classroom 1–6 → Projector 1–6 / TV 1–6 | Local classroom content |
| Display Mac 1–4 → (various) | Centralized media playback |

---

## Integration with Tesira

The "Mac Mini Audio" output (Out 40) and each classroom/worship feed passes through a **Blackmagic Teranex Mini SDI to Audio** de-embedder. The de-embedded audio is fed to the Tesira DSP for zone distribution.

### Teranex SDI De-Embedders

| Device Name | IP | MAC | Videohub Output | Audio Destination |
|-------------|-----|-----|-----------------|-------------------|
| **Teranex Classroom 1** | 10.10.20.122 | 7c:2e:0d:07:fc:2e | Out 1/7 | Tesira (Classroom 1 audio) |
| **Teranex Classroom 2** | 10.10.20.123 | 7c:2e:0d:18:bb:cb | Out 2/8 | Tesira (Classroom 2 audio) |
| **Teranex Classroom 3** | 10.10.20.124 | 7c:2e:0d:07:fc:14 | Out 3/9 | Tesira (Classroom 3 audio) |
| **Teranex Classroom 4** | 10.10.20.125 | 7c:2e:0d:07:fc:15 | Out 4/10 | Tesira (Classroom 4 audio) |
| **Teranex Classroom 5** | 10.10.20.126 | 7c:2e:0d:17:c7:bc | Out 5/11 | Tesira (Classroom 5 audio) |
| **Teranex Classroom 6** | 10.10.20.127 | 7c:2e:0d:17:c7:d0 | Out 6/12 | Tesira (Classroom 6 audio) |
| **Teranex Worship Center** | 10.10.20.128 | 7c:2e:0d:07:fc:12 | Out 12 (Worship Center Feed) | Tesira (Worship audio for hallways/foyer) |
| **Teranex DisplayMac 1** | 10.10.21.254 | 7c:2e:0d:08:16:75 | Out (Display Mac 1) | Tesira (Mac playback audio) |
| **Teranex DisplayMac 2** | 10.10.20.13 | 7c:2e:0d:08:16:68 | Out (Display Mac 2) | Tesira (Mac playback audio) |
| **Teranex DisplayMac 4** | 10.10.21.0 | 7c:2e:0d:08:3b:ee | Out (Display Mac 4) | Tesira (Mac playback audio) |

### Signal Flow (SDI Audio De-Embed)

```
SE-3200 PGM ──SDI──→ Videohub (In 12: Worship Center Feed)
                          │
                     Videohub Out 12 ──SDI──→ Teranex Worship Center
                                                    │
                                              Analog Audio Out
                                                    │
                                              Tesira SERVER-IO (Input)
                                                    │
                                              Zone Routing → Hallways, Foyer, etc.
```

Each classroom follows the same pattern: Videohub output → Teranex → analog audio → Tesira input for local zone speaker distribution.

### Additional Blackmagic Infrastructure

| Device | IP | MAC | Role |
|--------|-----|-----|------|
| **Blackmagic 40×40 Videohub** | 10.10.20.121 | 7c:2e:0d:07:f7:88 | SDI routing matrix |
| **AVL BMD Multiview** | 10.10.20.40 | 7c:2e:0d:16:ab:e5 | Monitoring multiview |
| **MG-Cloud-Store** | 10.10.20.7 | 7c:2e:0d:a7:7a:73 | 20TB media archive |
| **MG_Hyperdeck-A** | 10.10.20.13 | 7c:2e:0d:1c:0e:5e | Podcast/streaming recorder |

---

## Related Documents

- [Video Routing](../../systems/main-sanctuary/video/routing.md) — Camera to SE-3200 switcher
- [Tesira DSP](../tesira/README.md) — Children's building zone audio
- [IMAG Routing](../../systems/main-sanctuary/imag/routing.md) — LED wall feed
