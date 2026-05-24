# Main Sanctuary – Lighting Scenes & Cuelists

## Cuelist Architecture

Onyx uses **cuelists** rather than traditional scenes. Each cuelist can contain multiple cues with individual timing. Cuelists are assigned to playback faders or buttons on the NX4.

## Active Cuelists

### Position/Movement

| Cuelist | Type | Description |
|---------|------|-------------|
| R1 STAGE | Position preset | Full stage coverage — default home |
| R1.DOWN CIRCLE | Movement effect | Circular motion focused downstage |
| R1.DOWN CROSS | Movement effect | Cross pattern focused downstage |
| R1.DOWN INVERSE | Movement effect | Inverse cross focused downstage |
| PT Off | Position preset | Pan/Tilt to safe/home position |

### Color

| Cuelist | Type | Description |
|---------|------|-------------|
| BG Col Dim | Intensity | Background color with dimmer control (0–100%) |
| BG Col Macro | Automated | Background color macro cycling |
| Color Temperature | Preset | White presets: 2700K, 3200K, 4200K, 5600K, 8000K |
| CMY RGB Off | Reset | Kill all color mixing |
| Pink - White | Static | Pink to white gradient look |
| Warm White | Static | Warm white wash |

### Color Effects (Wave Chases)

| Cuelist | Colors | Type |
|---------|--------|------|
| Rainbow Wave | Full spectrum | Color chase |
| Dark blue - Cyan Wave | Blue → Cyan | Color chase |
| Dark blue - Magenta Wave | Blue → Magenta | Color chase |
| Dark blue - White Wave | Blue → White | Color chase |
| Green - Yellow Wave | Green → Yellow | Color chase |
| Red-Yellow Wave | Red → Yellow | Color chase |

### Intensity Effects

| Cuelist | Description |
|---------|-------------|
| DOUBLE WAVE OUT | Outward intensity wave from center |
| Wave | Standard intensity wave |
| z wave mid | Mid-intensity wave effect |
| Iris Wave | Iris open/close chase |

### LED Internal Effects

| Cuelist | Description |
|---------|-------------|
| LED Built In | Activate fixture internal LED effects |
| LED Built In Delay | LED effects with fixture-to-fixture offset |
| LED Built In Spd | LED effect speed control |

### Master Controls

| Cuelist | Description |
|---------|-------------|
| Global FX | Global effect master (overrides per-cuelist FX) |
| Global Fade | Master crossfade time |
| Live Time | Live timing override for manual control |
| Blackout PT | Black out pan/tilt only |
| Blackout Color | Black out color only |
| Blackout Gobo | Black out gobo only |
| Blackout Disabled | Prevent blackout (safety override) |

## Transition Notes

### Timing
- Default fade times are stored per-cuelist in the show file
- `Global Fade` cuelist can override all transition times
- `Live Time` allows real-time manual crossfade control from the fader

### Triggering
- Cuelists are triggered via:
  - Hardware playback faders on NX4
  - Go button (sequential cue advance)
  - Touchscreen cuelist directory tap
- No external MIDI/timecode triggers documented in this show file

### Effect Stacking
- Multiple cuelists can run simultaneously (HTP/LTP priority)
- Color wave cuelists override static color presets (LTP)
- Movement effects layer on top of position presets
- `Global FX` takes priority over per-cuelist effects

## Gobo Wheel Contents

Referenced in fixture definitions:

| Gobo | Notes |
|------|-------|
| Congo Star | Pattern |
| Inverted King Star | Pattern |
| Double Worms | Organic |
| Pipe Dreams | Organic |
| Triangle Cones | Geometric |
| Waves | Organic |
| Breakup | Texture |

## Related Documents

- [Console](console.md) — Hardware and programming details
- [Patch](patch.md) — Fixture addressing
- [Onyx Show Summary](onyx-show-summary.md) — Full extraction data
