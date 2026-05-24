# DM7 Processing Chain Summary – Main Sanctuary

> **Source:** DM7 Editor AppData extraction  
> **Scene:** Current production scene

---

## Processing Types Used

| Type | Category | Description |
|------|----------|-------------|
| **PRECISE** | EQ Algorithm | High-precision parametric EQ (most channels) |
| **SMOOTH** | EQ Algorithm | Smoother/analog-style EQ response |
| **AGGRESSIVE** | EQ Algorithm | More aggressive EQ curves (overheads) |
| **Smoother** | EQ Algorithm | Variant smooth EQ |
| **GATE** | Dynamics | Standard noise gate |
| **EXPANDER** | Dynamics | Soft expansion (gentler than gate) |
| **Classic Comp** | Compressor | Standard Yamaha compressor |
| **PM Comp** | Compressor | PM-style compressor (vocals) |
| **DiodeBridgeComp** | Compressor | Diode bridge emulation (guitars) |
| **dM. Band Comp** | Compressor | Multi-band compressor |

---

## Per-Channel Processing

### Drums (Ch 1–11)

| Ch | Name | EQ | Gate | Compressor | Notes |
|----|------|----|----|-----------|-------|
| 1 | KICK IN | PRECISE | GATE | Classic Comp | |
| 2 | KICK OUT | PRECISE | GATE | Classic Comp | |
| 3 | SNR TOP | PRECISE | GATE | Classic Comp | |
| 4 | SNR BTM | SMOOTH | GATE | PM Comp | Different EQ/comp from top |
| 5 | HIHAT | PRECISE | GATE | Classic Comp | |
| 6 | Tom 10" | PRECISE | GATE | Classic Comp | |
| 7 | Tom 12" | PRECISE | GATE | Classic Comp | |
| 8 | Tom 16" | PRECISE | GATE | Classic Comp | |
| 9 | Tom 18" | PRECISE | GATE | Classic Comp | |
| 10 | OH L | AGGRESSIVE | GATE | Classic Comp | Aggressive EQ for overheads |
| 11 | OH R | AGGRESSIVE | GATE | Classic Comp | Aggressive EQ for overheads |

### Instruments (Ch 12–22)

| Ch | Name | EQ | Gate | Compressor | Notes |
|----|------|----|----|-----------|-------|
| 12 | FA AUX | PRECISE | GATE | Classic Comp | Physical media input |
| 13 | BASS | PRECISE | GATE | Classic Comp | |
| 14 | EG 1 L | PRECISE | GATE | DiodeBridgeComp | Diode bridge for guitar color |
| 15 | EG1 R | PRECISE | GATE | DiodeBridgeComp | |
| 16 | EG2 L | PRECISE | GATE | DiodeBridgeComp | |
| 17 | EG2 R | PRECISE | GATE | DiodeBridgeComp | |
| 18 | ACOUSTIC | PRECISE | GATE | DiodeBridgeComp | Same comp as electrics |
| 19 | KEYS L | PRECISE | GATE | Classic Comp | |
| 20 | KEYS R | PRECISE | GATE | Classic Comp | |
| 21 | AUXKEY L | PRECISE | GATE | Classic Comp | |
| 22 | AUXKEY R | PRECISE | GATE | Classic Comp | |

### Vocals & Speech (Ch 23–37)

| Ch | Name | EQ | Gate | Compressor | Notes |
|----|------|----|----|-----------|-------|
| 23 | FL1 | PRECISE | — | PM Comp | **No gate on vocals** |
| 24 | FL2 | PRECISE | — | PM Comp | |
| 25 | FL3 | PRECISE | — | PM Comp | |
| 26 | FL4 | PRECISE | — | PM Comp | |
| 27 | JD VOX | PRECISE | — | PM Comp | Music Director |
| 28 | Cam10Mic | PRECISE | GATE | Classic Comp | Camera mic — gated |
| 29 | HDST 2 | PRECISE | GATE | PM Comp | Headset with gate |
| 30 | PASTOR | PRECISE | — | PM Comp | **No gate on pastor** |
| 31 | FL5 | PRECISE | — | PM Comp | |
| 36 | FL6 | PRECISE | — | PM Comp | |
| 37 | FL7 | PRECISE | — | PM Comp | |

> **Pattern:** All wireless vocal mics (FL1-7, Pastor, JD VOX) use **PM Comp without gate**. This prevents clipping from wireless dynamics while avoiding gate artifacts on intermittent singing.

### Digital & Playback (Ch 32–35, 42–56)

| Ch | Name | EQ | Gate | Compressor | Notes |
|----|------|----|----|-----------|-------|
| 32–33 | SPOTIFY | PRECISE | GATE | Classic Comp | |
| 34–35 | PROPRES | PRECISE | GATE | Classic Comp | |
| 38–41 | CHOIR | PRECISE | GATE | Classic Comp | |
| 42 | CLICK | PRECISE | GATE | Classic Comp | |
| 43 | TALKBACK | PRECISE | GATE | Classic Comp | |
| 49–50 | CROWD | PRECISE | GATE | Classic Comp | |
| 51–52 | BCastRet | PRECISE | GATE | Classic Comp | |
| 53–54 | TRACKS | PRECISE | GATE | Classic Comp | Focusrite stage input (guest iPad / MultiTracks) |

### Processed Returns from Ableton (Ch 57–67, 100–114)

| Ch | Name | EQ | Gate | Compressor | Notes |
|----|------|----|----|-----------|-------|
| 57–67 | Kick/Snare/Tom/OH/HiHat/Keys/Bass/Acoustic P | PRECISE | GATE | Classic Comp | Default processing (Ableton handles primary processing) |
| 100–107 | P FL1-FL7 Vx, P MD Vox | PRECISE | GATE | Classic Comp | Default (Ableton handles vocal processing) |
| 111–114 | Crowd/Choir LP/RP | PRECISE | GATE | Classic Comp | |

> **Note:** Processed returns from Ableton use default/flat console processing since the heavy lifting (EQ, compression, saturation, FX) is done in Ableton's plugin chain.

### FX Returns (Ch 115–124)

| Ch | Name | EQ | Gate | Compressor | Notes |
|----|------|----|----|-----------|-------|
| 115–116 | VOX ROOM | PRECISE | — | Classic Comp | No gate on reverb returns |
| 117–118 | VOX LONG | PRECISE | — | Classic Comp | |
| 119–120 | VOX DLY | PRECISE | — | Classic Comp | |
| 121–122 | DRUMLONG | PRECISE | — | Classic Comp | |
| 123–124 | SNR LONG | PRECISE | — | Classic Comp | |

---

## Processing Philosophy Summary

| Channel Type | EQ Style | Gate | Compressor | Rationale |
|-------------|----------|------|-----------|-----------|
| Drums | PRECISE (AGGRESSIVE on OH) | GATE | Classic Comp | Tight control, clean separation |
| Guitars | PRECISE | GATE | DiodeBridgeComp | Analog warmth/color on guitar tone |
| Vocals (wireless) | PRECISE | **None** | PM Comp | Avoid gate artifacts on dynamic wireless sources |
| Keys/Bass | PRECISE | GATE | Classic Comp | Standard clean processing |
| Playback/Digital | PRECISE | GATE | Classic Comp | Safety processing, minimal active use |
| Ableton Returns | PRECISE | GATE | Classic Comp | Flat/default — Ableton does processing |
| FX Returns | PRECISE | None | Classic Comp | No gate to preserve reverb/delay tails |

---

## DM7 Internal FX Rack

| Slot | FX Name | Type | Fed By | Returns To |
|------|---------|------|--------|-----------|
| 1–2 | VOX ROOM | Reverb (stereo) | Vocal channels | Ch 115–116 |
| 3–4 | VOX LONG | Reverb (stereo) | Vocal channels | Ch 117–118 |
| 5–6 | VOX DLY | Delay (stereo) | Vocal channels | Ch 119–120 |
| 7–8 | DRUMLONG | Reverb (stereo) | Drum channels | Ch 121–122 |
| 9–10 | SNR LONG | Reverb (stereo) | Snare channel | Ch 123–124 |

---

## Custom Fader Sends-on-Fader Banks

Extracted from Setup file — these are the quick-access mix send views:

| Bank | Assignment | Purpose |
|------|-----------|---------|
| Custom 1 | SENDS ON FADER → MIX 25 (BAY A) | Mix bus 25 sends |
| Custom 2 | SENDS ON FADER → MIX 27 (BAY A) | Mix bus 27 sends |
| Custom 3 | SENDS ON FADER → MIX 29 (BAY A) | Mix bus 29 sends |
| Custom 4 | SENDS ON FADER → MIX 31 (BAY A) | Mix bus 31 sends |
| Custom 5 | SENDS ON FADER → MIX 33 (BAY A) | Mix bus 33 sends |
| Custom 6 | SENDS ON FADER → MIX 34 (THIS BAY) | Mix bus 34 sends |
| Custom 7 | SENDS ON FADER → MATRIX 11 (THIS BAY) | Matrix 11 sends |
| Custom 8–24 | SENDS ON FADER → MIX 1–24 (THIS BAY) | Standard mix sends |

---

## Related Documents

- [DM7 Channel Map](dm7-channel-map.md) — Full channel inventory
- [Output Zones](output-zones.md) — Physical output destinations
- [Dante Routing](dante-routing.md) — Network subscriptions
