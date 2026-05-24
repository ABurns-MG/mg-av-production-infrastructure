# Main Sanctuary – Lighting Console

## Console

| Parameter | Value |
|-----------|-------|
| **Model** | Obsidian Onyx NX4 |
| **Software** | Onyx Build 4.8.1237.0 |
| **Protocol** | DMX-512 (direct outputs + network) |
| **Fader Banks** | 4 motorized fader wings |
| **Playback** | Hardware faders + touchscreen cuelist directory |

## Show File

| Property | Value |
|----------|-------|
| **Current File** | `TEST_2026-05-24_1312_Build_4_8_1237_0.OnyxShow` |
| **Location (Console)** | Internal storage |
| **Location (Backup)** | `configs/lighting/` in this repository |
| **Format** | ZIP → SQL Server MDF database |
| **Size** | 2.6 MB compressed / 15 MB uncompressed |

## Key Programming

### Movement Presets

| Preset | Purpose | Notes |
|--------|---------|-------|
| R1 STAGE | Full stage coverage | Default position |
| R1.DOWN CIRCLE | Circular motion downstage | Effect preset |
| R1.DOWN CROSS | Cross pattern downstage | Effect preset |
| R1.DOWN INVERSE | Inverse cross downstage | Effect preset |
| PT Off | Pan/Tilt home | Blackout safe position |

### Color/Effects Cuelists

| Cuelist | Purpose | Notes |
|---------|---------|-------|
| BG Col Dim | Background color with dimmer | Intensity 0–100% |
| BG Col Macro | Background color macros | Automated looks |
| Rainbow Wave | Full-spectrum color chase | |
| Dark blue - Cyan/Magenta/White Wave | Blue-based chases | Multiple variants |
| DOUBLE WAVE OUT | Intensity wave effect | |
| LED Built In / Delay / Spd | LED fixture internal FX | Speed controllable |
| Global FX | Global effect master | Overrides all |
| Global Fade | Master fade time | |

### Blackout Controls

| Control | Scope |
|---------|-------|
| Blackout PT | Pan/Tilt only |
| Blackout Color | Color channels only |
| Blackout Gobo | Gobo channels only |
| Blackout Disabled | Override (prevent blackout) |

## Console Views

| View | Purpose |
|------|---------|
| Cuelist Directory | Browse/select cuelists |
| Virtual Console | Software fader emulation |
| 2D Plan | Stage plot with fixture positions |
| Image View | Visualizer output |
| PLAYBACK | Main playback panel |
| Touch Play Status | Touchscreen cuelist status |
| FX Program | Effect builder |

## Operational Notes

### Startup
1. Power on NX4 console
2. Onyx software auto-loads last show file
3. Verify DMX output active (check fixture response)

### Backup Schedule
- Export `.OnyxShow` file after any programming changes
- Store backup in `configs/lighting/` with date in filename
- Naming: `{ShowName}_{Date}_{Time}_Build_{Version}.OnyxShow`

### Calibration
The show includes per-fixture calibration presets for Beam, Dimmer, Focus, Iris, Pan, Tilt, and Zoom. Use the calibration cuelists to fine-tune fixture alignment after any rigging changes.

## Related Documents

- [Onyx Show Summary](onyx-show-summary.md) — Full fixture inventory and cuelist extraction
- [Patch](patch.md) — DMX addressing
- [Scenes](scenes.md) — Scene descriptions
