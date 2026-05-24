# Main Sanctuary – Lighting Patch

## DMX Universes

| Universe | Protocol | Use | Notes |
|----------|----------|-----|-------|
| 1 | DMX-512 | Moving heads (spots) | Primary movers |
| 2 | DMX-512 | Moving heads (wash) + LED | Wash fixtures and color |
| 3+ | DMX-512 | Conventional / dimmer racks | Generic channels |

> **Note:** Exact universe assignments require attaching the show MDF to SQL Server LocalDB for full query access. The above is inferred from fixture count and typical NX4 layouts.

## Fixture Patch

### Moving Heads – Spots

| Fixture | Position ID | Mode | Ch Count |
|---------|-------------|------|----------|
| Chauvet Rogue R1 Spot | GW1-01 | Standard | 16+ |
| Chauvet Rogue R1 Spot | GW1-03 | Standard | 16+ |
| Chauvet Rogue R1 Spot | GW01-04 | Standard | 16+ |
| Chauvet Rogue R1 Spot | GW1-06 | Standard | 16+ |
| Chauvet Rogue R1 Spot | GW01-07 | Standard | 16+ |
| Chauvet Rogue R1X Spot | — | 16 Channel | 16 |
| Chauvet Rogue RH1 Hybrid | GW2-04 | Standard | 20+ |
| Chauvet Intimidator Spot 475Z | GW02-01 | Standard | 16+ |
| Chauvet Intimidator Spot 475Z | GW02-02 | Standard | 16+ |
| Chauvet Intimidator Spot 475Z | GW02-04 | Standard | 16+ |
| Chauvet Intimidator Spot 475Z | GW02-05 | Standard | 16+ |
| Chauvet Intimidator Spot 475Z | GW02-07 | Standard | 16+ |
| Chauvet Intimidator Spot 475Z | GW02-08 | Standard | 16+ |
| Chauvet Legend 300E Spot | GW01-02 | Standard | 16+ |
| Chauvet Legend 300E Spot | GW02-03 | Standard | 16+ |
| Martin MAC III Profile | — | 16 Bit | 26 |
| Martin MAC Viper Profile | — | Standard | 26 |

### Moving Heads – Wash

| Fixture | Position ID | Mode | Ch Count |
|---------|-------------|------|----------|
| Chauvet Rogue R3 Wash | — | 21 Channel | 21 |
| Martin MAC 250 Wash | — | Standard | 14 |
| Martin MAC Aura | — | Standard | 19 |
| Martin MAC TW1 | — | Standard | 14 |
| Martin MAC 401 Dual | — | Standard | 20 |
| Martin Rush MH 6 Wash CT | — | Standard | 12 |

### LED & Conventional

| Fixture | Position ID | Mode | Ch Count |
|---------|-------------|------|----------|
| Chauvet COLORado 1 Tri Tour | — | AR1.S | 6 |
| Chauvet Ovation E-190WW | — | 1-Channel | 1 |
| Martin MAC 101 | — | Standard | 9 |
| Martin MAC 575 Krypton | — | Standard | 14 |
| Martin StageBar 54 | — | Standard | 6 |
| Vari-Lite VL1000 TS | — | Tungsten/Shutter | 8 |
| ETC Selador | — | Standard | 7 |
| Generic Channel | Multiple | Standard | 1 |
| Generic MultiChannel | Multiple | 6-Channel | 6 |

## Position Naming Convention

| Code | Meaning |
|------|---------|
| GW01-xx | Grid/Wing row 1, fixture number xx |
| GW02-xx | Grid/Wing row 2, fixture number xx |
| GW1-xx | Shortened row 1 |
| GW2-xx | Shortened row 2 |

> Positions map to physical hanging locations on the lighting grid. Exact stage plot coordinates are visible in the console's 2D Plan view.

## Network Configuration

| Parameter | Value |
|-----------|-------|
| **Primary Protocol** | DMX-512 (hardwired from NX4 outputs) |
| **Console Outputs** | 4× DMX-512 (5-pin XLR) on NX4 rear panel |
| **Network Protocol** | sACN / Art-Net capable (if needed for expansion) |
| **IP (if networked)** | TBD |

## Related Documents

- [Console](console.md) — Console details and programming
- [Onyx Show Summary](onyx-show-summary.md) — Full extraction results
- [Scenes](scenes.md) — Scene/cuelist descriptions
