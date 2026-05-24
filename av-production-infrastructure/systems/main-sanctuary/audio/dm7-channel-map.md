# DM7 Console Channel Map – Main Sanctuary

> **Source:** DM7 Editor AppData (`CurrentBackupFile.bup`) — extracted 2026-05-24  
> **Console:** Yamaha DM7 | **Scene:** Current (live production)  
> **Total Active Channels:** 144 input + buses + DCAs

---

## Channel Categories

| Color | Category | Description |
|-------|----------|-------------|
| 🟡 Yellow | Stage Instruments | Raw microphone/DI inputs from stage boxes |
| 🔴 Red | Vocals & Speech | Wireless mics, wired vocals, camera mics |
| 🔵 Blue | Playback & Digital | Tracks, Spotify, ProPresenter, spare digital |
| 🟣 Purple | Processed Returns | Signals returned from Ableton after processing |
| 🟠 Orange | Buses & FX | Mix buses, matrix outputs, FX returns, DCAs |
| ⚪ White | Utility | Click, talkback, measurement, crowd mics |
| 🩷 Pink | Special | Sub-categories (e.g., Choir loft) |

---

## Input Channels (1–72)

### Drums (Ch 1–11) — From Rio1608 Stage Box

| Ch | Name | Color | Icon | Source | Dante Source |
|----|------|-------|------|--------|--------------|
| 1 | KICK IN | Yellow | Kick | Rio1608 TX 1 | Kick drum inside mic |
| 2 | KICK OUT | Yellow | Kick | Rio1608 TX 2 | Kick drum outside mic |
| 3 | SNR TOP | Yellow | Snare | Rio1608 TX 3 | Snare top mic |
| 4 | SNR BTM | Yellow | Snare | Rio1608 TX 4 | Snare bottom mic |
| 5 | HIHAT | Yellow | — | Rio1608 TX 5 | Hi-hat mic |
| 6 | Tom 10" | Yellow | — | Rio1608 TX 6 | Rack tom 10" |
| 7 | Tom 12" | Yellow | — | Rio1608 TX 7 | Rack tom 12" |
| 8 | Tom 16" | Yellow | — | Rio1608 TX 8 | Floor tom 16" |
| 9 | Tom 18" | Yellow | — | Rio1608 TX 9 | Floor tom 18" |
| 10 | OH L | Yellow | — | Rio1608 TX 10 | Overhead left |
| 11 | OH R | Yellow | — | Rio1608 TX 11 | Overhead right |

### Instruments (Ch 12–22) — From Rio3224 Stage Box + Omni

| Ch | Name | Color | Icon | Source | Dante Source |
|----|------|-------|------|--------|--------------|
| 12 | FA AUX | Red | — | DM7 Omni In (XLR→1/8") | Physical media device (iPod, etc.) |
| 13 | BASS | Yellow | E.Bass | Rio3224 TX 26 | Bass guitar DI |
| 14 | EG 1 L | Yellow | E.Guitar | Rio3224 TX 17 | Electric guitar 1 left |
| 15 | EG1 R | Yellow | E.Guitar | Rio3224 TX 18 | Electric guitar 1 right |
| 16 | EG2 L | Yellow | E.Guitar | Rio3224 TX 5 | Electric guitar 2 left |
| 17 | EG2 R | Yellow | E.Guitar | Rio3224 TX 6 | Electric guitar 2 right |
| 18 | ACOUSTIC | Yellow | A.Guitar | Rio3224 TX 19 | Acoustic guitar |
| 19 | KEYS L | Yellow | Keyboard | Rio3224 TX 27 | Keyboard left |
| 20 | KEYS R | Yellow | Keyboard | Rio3224 TX 28 | Keyboard right |
| 21 | AUXKEY L | Yellow | Organ | Rio3224 TX 22 | Auxiliary keyboard left |
| 22 | AUXKEY R | Yellow | Organ | Rio3224 (TBD) | Auxiliary keyboard right |

### Vocals & Speech (Ch 23–31, 36–37) — From Shure ULXD4Q Wireless

| Ch | Name | Color | Icon | Source | Signal |
|----|------|-------|------|--------|--------|
| 23 | FL1 | Red | — | ULXD4Q-ea9fd2 TX 1 | Front Line vocal 1 |
| 24 | FL2 | Red | — | DM7 direct (wired) | Front Line vocal 2 |
| 25 | FL3 | Red | — | ULXD4Q-ea9fd2 TX 3 | Front Line vocal 3 |
| 26 | FL4 | Red | — | ULXD4Q-ea9fd2 TX 4 | Front Line vocal 4 |
| 27 | JD VOX | Red | — | Rio3224 TX 29 | Music Director vocal (wired) |
| 28 | Cam10Mic | Red | — | DM7 Omni In (from SE-3200 Audio Out 1) | Canon R6 II camera mic via Teradek→HDMI→SE-3200 |
| 29 | HDST 2 | Red | Headset | ULXD4Q-ea9fd2 TX 2 | Headset mic 2 |
| 30 | PASTOR | Red | Headset | ULXD4Q-eacb78 TX 4 | Pastor headset (HDST-1) |
| 31 | FL5 | Red | — | ULXD4Q-eacb78 TX 1 | Front Line vocal 5 |
| 36 | FL6 | Red | — | ULXD4Q-eacb78 TX 2 | Front Line vocal 6 |
| 37 | FL7 | Red | — | ULXD4Q-eacb78 TX 3 | Front Line vocal 7 |

### Digital Playback (Ch 32–35) — From Resolume-Mac-Studio & ProPresenter-MacMini

| Ch | Name | Color | Icon | Source | Signal |
|----|------|-------|------|--------|--------|
| 32 | SPOTIFY | Blue | — | Resolume-Mac-Studio TX 1 | Spotify playback left (shared TX with Resolume) |
| 33 | SPOTIFY | Blue | — | Resolume-Mac-Studio TX 2 | Spotify playback right (shared TX with Resolume) |
| 34 | PROPRES | Blue | — | ProPresenter-MacMini TX 1 | ProPresenter audio left |
| 35 | PROPRES | Blue | — | ProPresenter-MacMini TX 2 | ProPresenter audio right |

### Choir & Ambient (Ch 38–50)

| Ch | Name | Color | Icon | Source | Signal |
|----|------|-------|------|--------|--------|
| 38 | CHOIR L | Red | Choir | Rio3224 TX 12 | Choir mic left |
| 39 | CHOIR C | Red | Choir | Rio3224 TX 13 | Choir mic center |
| 40 | CHOIR R | Red | Choir | Rio3224 TX 10 | Choir mic right |
| 41 | Choir Lf | Pink | — | (TBD) | Choir loft mic |
| 42 | CLICK | White | — | Rio3224 TX 25 | Click track (from playback rig) |
| 43 | TALKBACK | White | Podium | DM7 talkback mic | Engineer talkback |
| 44 | MD MIC | White | — | (TBD) | Music Director communication mic |
| 45 | Rm Meas | White | — | DM7 TX 50 (loopback) | DBX RTA-m measurement mic → REW SPL meter via ProPresenter-MacMini |
| 46 | ROOM LC | White | — | (TBD) | Room measurement left-center |
| 47 | ROOM RC | White | — | (TBD) | Room measurement right-center |
| 48 | ROOM R | Purple | — | (TBD) | Room measurement right |
| 49 | CROWD L | White | — | Rio3224 TX 14 | Crowd/ambient mic left |
| 50 | CROWD R | White | — | (TBD) | Crowd/ambient mic right |

### Broadcast & Playback (Ch 51–56)

| Ch | Name | Color | Icon | Source | Signal |
|----|------|-------|------|--------|--------|
| 51 | BCastRet | White | — | MG-AVL-Ableton TX 47 | Broadcast processed return left |
| 52 | BCastRet | White | — | MG-AVL-Ableton TX 48 | Broadcast processed return right |
| 53 | TRACKS L | Blue | — | Rio3224 TX 23 | Focusrite stage input left (guest iPad / MultiTracks Playback) |
| 54 | TRACKS R | Blue | — | Rio3224 TX 24 | Focusrite stage input right (guest iPad / MultiTracks Playback) |
| 55 | FA L Aux | Red | — | DM7 Omni In (XLR→1/8") | Foldback aux left (physical media) |
| 56 | FA R Aux | Red | — | DM7 Omni In (XLR→1/8") | Foldback aux right (physical media) |

---

## Input Channels (57–114) — Processed & Tracks

### Ableton Processed Returns (Ch 57–67) — From MG-AVL-Ableton

| Ch | Name | Color | Icon | Ableton TX | Signal |
|----|------|-------|------|-----------|--------|
| 57 | Kick P | Purple | Kick | TX 01 | Processed kick drum |
| 58 | Snare P | Purple | Snare | TX 02 | Processed snare |
| 59 | Tom L P | Purple | — | TX 03 | Processed toms left |
| 60 | Tom R P | Purple | — | TX 04 | Processed toms right |
| 61 | Ovhd L P | Purple | Cymbal | TX 05 | Processed overhead left |
| 62 | Ovhd R P | Purple | Cymbal | TX 06 | Processed overhead right |
| 63 | HiHat P | Purple | — | TX 42 | Processed hi-hat |
| 64 | Keys LP | Purple | Keyboard | TX 21 | Processed keys left |
| 65 | Keys RP | Purple | Keyboard | TX 22 | Processed keys right |
| 66 | Bass P | Purple | E.Bass | TX 07 | Processed bass |
| 67 | Akustc P | Purple | A.Guitar | TX 08 | Processed acoustic |

### Spare / REW (Ch 68)

| Ch | Name | Color | Icon | Source | Signal |
|----|------|-------|------|--------|--------|
| 68 | REW L O> | White | — | (TBD) | REW output / reference |

### Multitrack Stems (Ch 69–98) — From JD-MG-MacBook-Pro

| Ch | Name | Color | Icon | Source TX | Signal |
|----|------|-------|------|----------|--------|
| 69 | T Drum L | Blue | DrumKit | 01-Drums L | Drum stems left |
| 70 | T Drum R | Blue | DrumKit | 02-Drums R | Drum stems right |
| 71 | T Perc L | Blue | — | 03-Perc L | Percussion left |
| 72 | T Perc R | Blue | — | 04-Perc R | Percussion right |
| 73 | T Loop L | Blue | — | 05-Loops L | Loops left |
| 74 | T Loop R | Blue | — | 06-Loops R | Loops right |
| 75 | T Bass L | Blue | E.Bass | 07-Bass L | Bass stems left |
| 76 | T Bass R | Blue | E.Bass | 08-Bass R | Bass stems right |
| 77 | T Pian L | Blue | Piano | 09-Piano L | Piano left |
| 78 | T Pian R | Blue | Piano | 10-Piano R | Piano right |
| 79 | T Keys L | Blue | Keyboard | 11-Keys L | Keys left |
| 80 | T Keys R | Blue | Keyboard | 12-Keys R | Keys right |
| 81 | T Gtr L | Blue | E.Guitar | 13-Gtr L | Guitar left |
| 82 | T Gtr R | Blue | E.Guitar | 14-Gtr R | Guitar right |
| 83 | T Akus L | Blue | A.Guitar | 15-Acous L | Acoustic left |
| 84 | T Akus R | Blue | A.Guitar | 16-Acous R | Acoustic right |
| 85 | T Horn L | Blue | Trumpet | 17-Horns L | Horns left |
| 86 | T Horn R | Blue | Trumpet | 18-Horns R | Horns right |
| 87 | T Strg L | Blue | — | 19-Strg L | Strings left |
| 88 | T Strg R | Blue | — | 20-Strg R | Strings right |
| 89 | T Pad L | Blue | Organ | 21-Pad L | Pad left |
| 90 | T Pad R | Blue | Organ | 22-Pad R | Pad right |
| 91 | T Voc L | Blue | BG Vocal | 23-Vox L | Vocals left |
| 92 | T Voc R | Blue | BG Vocal | 24-Vox R | Vocals right |
| 93 | T FX L | Blue | — | 25-FX L | FX left |
| 94 | T FX R | Blue | — | 26-FX R | FX right |
| 95 | T Aux L | Blue | — | 27-Aux L | Aux left |
| 96 | T Aux R | Blue | — | 28-Aux R | Aux right |
| 97 | T Click | White | — | 29-Guide | Click track |
| 98 | T Guide | White | — | 30-Click | Guide track |

### Spare (Ch 99)

| Ch | Name | Color | Signal |
|----|------|-------|--------|
| 99 | ch105 | Blue | Spare/unused |

### Ableton Processed Vocals (Ch 100–107) — From MG-AVL-Ableton

| Ch | Name | Color | Icon | Ableton TX | Signal |
|----|------|-------|------|-----------|--------|
| 100 | P FL1 Vx | Purple | — | TX 09 | Processed Front Line 1 |
| 101 | P FL2 Vx | Purple | — | TX 10 | Processed Front Line 2 |
| 102 | P FL3 Vx | Purple | — | TX 11 | Processed Front Line 3 |
| 103 | P FL4 Vx | Purple | — | TX 12 | Processed Front Line 4 |
| 104 | P MD Vox | Purple | — | TX 23 | Processed Music Director vocal |
| 105 | P FL5 Vx | Purple | BG Vocal | TX 13 | Processed Front Line 5 |
| 106 | P FL6 Vx | Purple | BG Vocal | TX 14 | Processed Front Line 6 |
| 107 | P FL7 Vx | Purple | BG Vocal | TX 15 | Processed Front Line 7 |

### Spare (Ch 108–110)

| Ch | Name | Color | Signal |
|----|------|-------|--------|
| 108 | ch114 | Blue | Spare |
| 109 | ch115 | Blue | Spare |
| 110 | ch116 | Blue | Spare |

### Ableton Processed Ambient (Ch 111–114) — From MG-AVL-Ableton

| Ch | Name | Color | Icon | Ableton TX | Signal |
|----|------|-------|------|-----------|--------|
| 111 | Crowd LP | White | — | TX 31 | Processed crowd left |
| 112 | Crowd RP | White | — | TX 32 | Processed crowd right |
| 113 | Choir LP | Purple | Choir | TX 29 | Processed choir left |
| 114 | Choir RP | Purple | Choir | TX 30 | Processed choir right |

---

## FX Returns (Ch 115–128)

| Ch | Name | Color | Type | Signal |
|----|------|-------|------|--------|
| 115 | VOX ROOM | Orange | FX Return L | Vocal room reverb left |
| 116 | VOX ROOM | Orange | FX Return R | Vocal room reverb right |
| 117 | VOX LONG | Orange | FX Return L | Vocal long reverb left |
| 118 | VOX LONG | Orange | FX Return R | Vocal long reverb right |
| 119 | VOX DLY | Orange | FX Return L | Vocal delay left |
| 120 | VOX DLY | Orange | FX Return R | Vocal delay right |
| 121 | DRUMLONG | Orange | FX Return L | Drum long reverb left |
| 122 | DRUMLONG | Orange | FX Return R | Drum long reverb right |
| 123 | SNR LONG | Orange | FX Return L | Snare long reverb left |
| 124 | SNR LONG | Orange | FX Return R | Snare long reverb right |
| 125 | HrmnyVOX | Purple | Ableton Return | Vocal harmonics (from Ableton TX 19) |
| 126 | Snare P | Purple | Ableton Return | Snare reverb processed |
| 127 | Toms P | Purple | Ableton Return | Toms processed left |
| 128 | Toms P R | Purple | Ableton Return | Toms processed right |

---

## Mix Buses & Monitor Feeds (Ch 129–136)

| Ch | Name | Color | Signal |
|----|------|-------|--------|
| 129 | Track IE | White | Tracks IEM feed left |
| 130 | Track IE | White | Tracks IEM feed right |
| 131 | IEM 4 | Blue | IEM mix 4 left (spare/overflow) |
| 132 | IEM 4R | Blue | IEM mix 4 right |
| 133 | CHOIRMON | Blue | Choir monitor mix |
| 134 | VARI | Orange | Variable-use bus |
| 135 | Inst Bus | White | Instrument bus left |
| 136 | Inst Bus | White | Instrument bus right |

---

## Matrix Outputs (Ch 137–159)

| Ch | Name | Color | Destination | Signal |
|----|------|-------|-------------|--------|
| 137–148 | MX37–MX48 | Orange | (Unassigned matrix) | Spare matrix buses |
| 149 | FOYER | Orange | Crown CDi 1000 Ch A (70V) via Omni XLR | Foyer zone audio |
| 150 | BROADCST | Orange | BCast-Audio AVIO → SE-3200 | Broadcast left |
| 151 | BROADCST | Orange | BCast-Audio AVIO → SE-3200 | Broadcast right |
| 152 | STAGEMON | Orange | Rio3224 RX (stage wedges) | Stage monitor bus |
| 153 | ProP SPK | Orange | (TBD) | ProPresenter speaker feed |
| 154 | SptfyOnl | Orange | Foyer + Broadcast (preservice mode) | Spotify-only left |
| 155 | SptfyOnl | Orange | Foyer + Broadcast (preservice mode) | Spotify-only right |
| 156 | Mon A | Orange | Rio3224 RX 3 → stage | Monitor A |
| 157 | Mon B | Orange | Rio3224 RX 4 → stage | Monitor B |
| 158 | REFMONL | Orange | (TBD) | Reference monitor left |
| 159 | REFMONR | Orange | (TBD) | Reference monitor right |

---

## Stereo Buses (Ch 160–163)

| Ch | Name | Color | Destination | Signal |
|----|------|-------|-------------|--------|
| 160 | ST A | Purple | Rio3224 RX 1 → FOH Main L | **Main house left** |
| 161 | ST A | Purple | Rio3224 RX 2 → FOH Main R | **Main house right** |
| 162 | ST B | Orange | (TBD) | Stereo B left |
| 163 | ST B | Orange | (TBD) | Stereo B right |

---

## DCA Groups (Ch 164–175)

| DCA | Name | Color | Members | Purpose |
|-----|------|-------|---------|---------|
| 1 | BAND | Orange | All instruments (raw + processed) | Master band level |
| 2 | VOCALS | Orange | All vocals (raw + processed) | Master vocals level |
| 3 | Drum ALL | Orange | Ch 1–11 + 57–63 | All drum channels |
| 4 | Drum P | Orange | Ch 57–63 | **Processed drums (from Ableton)** |
| 5 | Drum O | Orange | Ch 1–11 | **Original drums (direct, failsafe)** |
| 6 | P Inst | Orange | Ch 64–67 | **Processed instruments (from Ableton)** |
| 7 | O Inst | Orange | Ch 13–22 | **Original instruments (direct, failsafe)** |
| 8 | Tracks | Orange | Ch 69–98 | Multitrack playback stems |
| 9 | VOX FX | Orange | Ch 115–120 | Vocal FX returns |
| 10 | BAND FX | Orange | Ch 121–124 | Band FX returns |
| 11 | P Vocals | Orange | Ch 100–107 | **Processed vocals (from Ableton)** |
| 12 | O Vocals | Orange | Ch 23–31, 36–37 | **Original vocals (direct, failsafe)** |

### Failsafe Architecture (P/O Redundancy)

```
Normal Operation:     "P" DCAs UP (4, 6, 11) → Ableton processed audio active
					  "O" DCAs DOWN (5, 7, 12) → Direct audio muted

Ableton Failure:      "P" DCAs DOWN → Processed audio silenced
					  "O" DCAs UP → Direct stage audio takes over immediately

Recovery:             Restart Ableton → verify processed returns → swap DCAs back
```

> **Operator Action:** If Ableton crashes or audio drops, pull down DCA 4/6/11 and push up DCA 5/7/12. No patching changes required — all inputs are always live on both paths, only the DCA master level differs.

---

## Stereo Pairs

Based on channel naming patterns, these channels are likely stereo-linked:

| Pair | Channels | Signal |
|------|----------|--------|
| KEYS | 19–20 | Keyboard L/R |
| AUXKEY | 21–22 | Aux keyboard L/R |
| SPOTIFY | 32–33 | Spotify L/R |
| PROPRES | 34–35 | ProPresenter L/R |
| TRACKS | 53–54 | Playback tracks L/R |
| FA Aux | 55–56 | Foldback aux L/R |
| All multitrack | 69–96 (paired) | Stem pairs |
| BCastRet | 51–52 | Broadcast return L/R |
| Crowd L/P | 111–112 | Processed crowd L/R |
| Choir L/P | 113–114 | Processed choir L/R |
| FX returns | 115–124 (paired) | FX L/R pairs |
| ST A | 160–161 | Main house L/R |
| ST B | 162–163 | Stereo B L/R |
| BROADCST | 150–151 | Broadcast L/R |
| SptfyOnl | 154–155 | Spotify-only L/R |

---

## Related Documents

- [Dante Routing (Network Layer)](dante-routing.md) — Channel-level Dante subscriptions
- [Dante Network Overview](../../../configs/dante/README.md) — Device inventory
- [Channel Naming Standards](../../../configs/dante/channel-naming-standards.md) — Suggested Dante label updates
- [DM7 Data Extraction Guide](../../../configs/dm7/README-extraction-guide.md) — How this data was obtained
