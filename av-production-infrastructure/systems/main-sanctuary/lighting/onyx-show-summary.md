# Main Sanctuary – Lighting System

> **Console:** Obsidian Onyx NX4  
> **Show File:** `TEST_2026-05-24_1312_Build_4_8_1237_0.OnyxShow` (Build 4.8.1237.0)  
> **Source:** MDF extraction from show file  
> **Last Updated:** 2026-05-24

---

## System Overview

| Parameter | Value |
|-----------|-------|
| **Console** | Obsidian Onyx NX4 |
| **Software** | Onyx Build 4.8.1237.0 |
| **Protocol** | DMX-512 |
| **Show File Format** | `.OnyxShow` (ZIP → SQL Server MDF) |

---

## Fixture Inventory

### Moving Heads – Spots

| Fixture Type | Manufacturer | Instances | Mode | Notes |
|-------------|-------------|-----------|------|-------|
| **Rogue R1 Spot** | Chauvet | 5 | Standard | GW1-01, GW1-03, GW01-04, GW1-06, GW01-07 |
| **Rogue R1X Spot** | Chauvet | 1+ | 16 Channel | Updated R1 variant |
| **Rogue RH1 Hybrid** | Chauvet | 1+ | Standard | Spot/Beam/Wash hybrid |
| **Intimidator Spot 475Z** | Chauvet | 6 | Standard | GW02-01, -02, -04, -05, -07, -08 |
| **Legend 300E Spot** | Chauvet | 2 | Standard | GW01-02, GW02-03 |
| **MAC III Profile** | Martin | 1+ | 16 Bit | High-end profile fixture |
| **MAC Viper Profile** | Martin | 1+ | Standard | High-output profile |

### Moving Heads – Wash

| Fixture Type | Manufacturer | Instances | Mode | Notes |
|-------------|-------------|-----------|------|-------|
| **Rogue R3 Wash** | Chauvet | 1+ | 21 Channel | RGBW wash |
| **MAC 250 Wash** | Martin | 1+ | Standard | Legacy wash |
| **MAC Aura** | Martin | 1+ | Standard | Backlight wash |
| **MAC TW1** | Martin | 1+ | Standard | Tungsten wash |
| **MAC 401 Dual** | Martin | 1+ | Standard | Dual-source wash |
| **Rush MH 6 Wash CT** | Martin | 1+ | Standard | Compact CT wash |

### Conventional & LED

| Fixture Type | Manufacturer | Instances | Mode | Notes |
|-------------|-------------|-----------|------|-------|
| **COLORado 1 Tri Tour** | Chauvet | 1+ | AR1.S | RGB LED wash |
| **Ovation E-190WW** | Chauvet | 1+ | 1-Channel | LED ellipsoidal (warm white) |
| **MAC 101** | Martin | 1+ | Standard | Compact LED wash |
| **MAC 575 Krypton** | Martin | 1+ | Standard | Legacy discharge |
| **StageBar 54** | Martin | 1+ | Standard | LED bar |
| **VL1000 TS** | Vari-Lite | 1+ | Tungsten/Shutter | Tungsten spot |
| **Selador** | ETC | 1+ | Standard | LED fixture |
| **Generic Channel** | Generic | Multiple | Standard/6-ch | Conventional dimmers |

---

## Fixture Naming Convention

Fixtures are named using the format: `{Model}, {Position}`

Position codes observed:
- **GW01-xx** — Grid/Wing position, row 1
- **GW02-xx** — Grid/Wing position, row 2
- **GW1-xx** — Alternate row 1 naming (shortened)
- **GW2-xx** — Alternate row 2 naming (shortened)

---

## Cuelists & Presets

### Movement Presets (Position)

| Preset Name | Description |
|-------------|-------------|
| R1 STAGE | Stage-wide coverage position |
| R1.DOWN CIRCLE | Circular movement, downstage |
| R1.DOWN CROSS | Cross pattern, downstage |
| R1.DOWN INVERSE | Inverse cross, downstage |
| PT Off | Pan/Tilt home (blackout position) |

### Color Presets & Effects

| Preset/Cuelist | Type |
|---------------|------|
| BG Col Dim | Background color dimming |
| BG Col Macro | Background color macros |
| Color Temperature (2700K–8000K) | White presets |
| Dark blue - Cyan Wave | Color chase |
| Dark blue - Magenta Wave | Color chase |
| Dark blue - White Wave | Color chase |
| Green - Yellow Wave | Color chase |
| Rainbow Wave | Full-spectrum chase |
| Red-Yellow Wave | Color chase |
| Pink - White | Static look |
| CMY RGB Off | Color reset |

### Effect Cuelists

| Cuelist | Type |
|---------|------|
| DOUBLE WAVE OUT | Effect macro |
| Wave | Intensity wave |
| z wave mid | Mid-intensity wave |
| Iris Wave | Iris effect |
| LED Built In | Internal LED effects |
| LED Built In Delay | LED effects with offset |
| LED Built In Spd | LED effects speed control |
| FX Program | Effect programming |
| Global FX | Global effect override |
| Global Fade | Master fade control |
| Live Time | Live timing override |

### System/Control

| Cuelist | Purpose |
|---------|---------|
| Cuelist Directory | Navigation panel |
| Selected Cuelist | Active cuelist display |
| Virtual Console | Software fader view |
| PLAYBACK | Playback panel |
| Touch Play Status | Touchscreen status |
| 2D Plan | Stage layout view |
| Image View | Image rendering |

### Calibration Presets

| Preset | Purpose |
|--------|---------|
| Calibration Enable | Enter calibration mode |
| Calibration Store Beam | Store beam calibration |
| Calibration Store Dimmer | Store dimmer calibration |
| Calibration Store Focus | Store focus calibration |
| Calibration Store Iris | Store iris calibration |
| Calibration Store Pan | Store pan calibration |
| Calibration Store PT | Store pan/tilt calibration |
| Calibration Store Tilt | Store tilt calibration |
| Calibration Store Zoom | Store zoom calibration |
| Calibration Reset | Reset all calibration |
| Calibration Idle | Exit calibration |

---

## Gobo Inventory (from fixture definitions)

Gobos referenced in the show file:
- Congo Star
- Double Worms
- Inverted King Star
- Pipe Dreams
- Triangle Cones
- Waves
- Breakup

---

## Console Layout

### Panels Configured

| Panel | Purpose |
|-------|---------|
| Cuelist Directory | Main cuelist browser |
| Submaster Panel | Submaster fader view |
| Virtual Console | Software playback faders |
| 2D Plan | Stage plot / fixture layout |
| Image View | Visual rendering output |
| PLAYBACK | Main playback panel |

---

## Show File Technical Details

| Property | Value |
|----------|-------|
| **Format** | `.OnyxShow` (ZIP container → SQL Server MDF) |
| **Build Version** | 4.8.1237.0 |
| **Min Build Required** | 67634389 |
| **Original Machine** | DESKTOP-C1003GU |
| **DB Engine** | SQL Server LocalDB |
| **File Size** | 2.6 MB compressed / 15 MB uncompressed |
| **Show Name** | TEST |

### Extraction Notes

The `.OnyxShow` file is a ZIP archive containing a single SQL Server MDF database file named `Show`. The database stores all fixture definitions (as embedded XML), cuelist data, patch information, and console layout in relational tables. Key tables include:

- `CueListsV2` / `CueListsV3` — Cuelist definitions with tracking
- `Fixture` — Patched fixture instances
- `FixtureType` — Fixture personality definitions (XML)
- `DMXChannel` — DMX address assignments
- `DynamicGroup` — Fixture groups
- `EffectMacro` — Stored effects

> **Note:** Fixture instance counts shown as "1+" indicate at least one instance is patched; exact counts require attaching the MDF to a SQL Server instance for proper query access. The named instances (GW01-xx through GW2-xx) are confirmed patched fixtures.

---

## Related Documents

- [Output Zones](../audio/output-zones.md) — Physical zone routing (FOH, broadcast, etc.)
- [Dante Routing](../audio/dante-routing.md) — Network audio subscriptions
- [DM7 Channel Map](../audio/dm7-channel-map.md) — Audio console channels
