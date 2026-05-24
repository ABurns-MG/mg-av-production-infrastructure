# Main Sanctuary – Complete Dante Routing

> **Source:** `Dante-config-20260524.xml` — Full network export with all subscriptions  
> **Date:** 2026-05-24  
> **Total Devices:** 25 | **Active Subscriptions:** 200+

---

## Device Cross-Reference (Dante ↔ UniFi Network)

Dante device names encode the **last 3 bytes of the Dante NIC MAC address** as a suffix (e.g., `c9a984` → `ac:44:f2:c9:a9:84`). This table maps each Dante device to its UniFi-observed network identity.

| Dante Device Name | MAC (Dante NIC) | Dante IP (VLAN 130) | Mgmt IP (VLAN 250) | Manufacturer |
|-------------------|----------------|---------------------|---------------------|--------------|
| Y001-Yamaha-DM7-c9a984 | ac:44:f2:c9:a9:84 | 192.168.10.138 | 10.0.250.31 | Yamaha |
| Y001-Yamaha-Rio3224-D2-25e264 | 00:1d:c1:25:e2:64 | 192.168.10.149 | — | Audinate |
| Y002-Yamaha-Rio1608-D2-28589c | 00:1d:c1:28:58:9c | 192.168.10.238 | — | Audinate |
| AllenHth-2182fc | 00:1d:c1:21:82:fc | 192.168.10.22 | — | Audinate (A&H ME card) |
| ULXD4Q-ea9fd2 | — | 192.168.10.59 | 10.0.250.174 | Shure |
| ULXD4Q-eacb78 | — | — | — | Shure |
| KLANG-IEM (0FC611) | 00:04:c4:0f:c6:11 | DHCP | 10.10.20.232 | Audiotonix |
| MG-AVL-Ableton | 14:98:77:83:07:1d | 192.168.10.10 | — | Apple (Mac Mini) |
| ProPresenter-MacMini | 20:a5:cb:ca:81:6a | 192.168.10.79 | — | Apple |
| Resolume-Mac-Studio | 9c:76:0e:3a:58:5f | DHCP | — | Apple |
| BCast-Audio | 00:1d:c1:xx:xx:xx | DHCP | — | Audinate (AVIO-DAO2) |
| IEM AVIO Adapters (×12) | 00:1d:c1:54/55:xx:xx | DHCP | — | Audinate (AVIO-DAO2) |

> **Note:** The DLive C3500 (`192.168.10.5` / `10.0.250.8`, MAC `00:04:c4:09:0f:68`) appears in UniFi as a saved fixed address but has been **relocated to MercyGate League City**. It is not part of the active Main Sanctuary Dante network.

> **Cross-reference source:** [`configs/network/avl-clients.md`](../../../configs/network/avl-clients.md)

---

## Table of Contents

1. [DM7 (Console – Clock Master)](#y001-yamaha-dm7-c9a984)
2. [MG-AVL-Ableton (Processing)](#mg-avl-ableton)
3. [Rio3224 (Stage Box – Instruments)](#y001-yamaha-rio3224-d2-25e264)
4. [Rio1608 (Stage Box – Drums)](#y002-yamaha-rio1608-d2-28589c)
5. [KLANG-IEM (Monitor Processor)](#klang-iem)
6. [Shure ULXD4Q Wireless](#shure-wireless-receivers)
7. [BCast-Audio (Broadcast Output)](#bcast-audio)
8. [AllenHth-2182fc (Allen & Heath)](#allenhth-2182fc)
9. [IEM AVIO Adapters](#iem-avio-adapters)
10. [Workstations (DVS)](#workstations)

---

## Y001-Yamaha-DM7-c9a984

**Model:** Yamaha DM7 (V1.73) | **Capacity:** 144 TX / 144 RX | **Role:** ★ Clock Master, FOH + Broadcast Console  
**Dante IP:** 192.168.10.138 | **Console Net IP:** 10.0.250.31  
**Preferred Master:** Yes | **External Word Clock:** Yes | **Encoding:** 32-bit | **Unicast Latency:** 5 ms

### DM7 Transmit Channels (Key Outputs)

| TX Ch | Label | Signal | Destination(s) |
|-------|-------|--------|----------------|
| 1-30 | 01-30 | Direct outs / bus outputs | AllenHth-2182fc, KLANG-IEM |
| 31 | FL1 D out | Front Line 1 direct out | AllenHth, KLANG |
| 32 | FL2 D out | Front Line 2 direct out | AllenHth, KLANG |
| 33 | FL3 D out | Front Line 3 direct out | KLANG |
| 34 | FL4 D out | Front Line 4 direct out | KLANG |
| 35 | MD Vox D out | Music Director vocal direct out | AllenHth, KLANG |
| 36 | (unnamed) | MD Mic | AllenHth |
| 37 | Talkback D out | Talkback mic direct out | AllenHth, KLANG |
| 38-40 | (unnamed) | Various | AllenHth, KLANG |
| 41-43 | (unnamed) | Choir L/C/R (from DM7 processing) | KLANG |
| 44 | LV1 D out | Lavelier mic 1 direct out | KLANG |
| 45 | HDST-1 D out | Headset 1 (Pastor) direct out | — |
| 46 | Tracks Group L | Tracks group bus L | KLANG |
| 47 | Tracks Group R | Tracks group bus R | KLANG |
| 50 | Room Measurement Mic | Measurement reference | — |
| 51 | FL5 D out | Front Line 5 direct out | KLANG |
| 52 | FL6 D out | Front Line 6 direct out | KLANG |
| 53 | FL7 D out | Front Line 7 direct out | KLANG |
| 61 | Pre BCast Audio L | Pre-processed broadcast L | — |
| 62 | Pre BCast Audio R | Pre-processed broadcast R | — |
| 63 | Post BCast L | **Post-processed broadcast L** | **BCast-Audio (RX1)** |
| 64 | Pose BCast R | **Post-processed broadcast R** | **BCast-Audio (RX2)** |
| 65 | Instrument Bus L | Instrument group bus L | KLANG (RX55) |
| 66 | Instrument Bus R | Instrument group bus R | KLANG (RX56) |
| 77 | VOX Harmonics | Vocal harmonics FX send | KLANG |
| 78 | VOX Reverb | Vocal reverb FX send | KLANG |
| 135 | ST A L | Stereo A Left (FOH main) | Rio3224 (RX1) |
| 136 | ST A R | Stereo A Right (FOH main) | Rio3224 (RX2) |
| 137 | T Click D(O) | Click direct out | KLANG (RX49) |
| 138 | T Guide D(O) | Guide track direct out | KLANG (RX48) |
| 143 | Mon A Stage | Monitor A stage bus | Rio3224 (RX3) |
| 144 | Mon B Stage | Monitor B stage bus | Rio3224 (RX4) |

### DM7 Receive Channels (Inputs to Console)

#### From MG-AVL-Ableton (Processed Returns)

| RX Ch | Name | Ableton TX | Signal |
|-------|------|-----------|--------|
| 1 | Kick Processed | 01 - Kick Drum Processed | Drum processing |
| 2 | Snare Processed | 02 - Snare Drum Processed | Drum processing |
| 3 | Tom L Processed | 03 - Toms L Processed | Drum processing |
| 4 | Tom R Processed | 04 - Toms R Processed | Drum processing |
| 5 | Overhead L Processed | 05 - Overhead L Processed | Drum processing |
| 6 | Overhead R Processed | 06 - Overhead R Processed | Drum processing |
| 7 | Bass Processed | 07 - Bass Processed | Instrument processing |
| 8 | Acoustic Processed | 08 - Acoustic Processed | Instrument processing |
| 9 | HiHat Processed | 42 - HiHat Processed | Drum processing |
| 31 | Keys L Processed | 21 - Keys L Processed | Keys processing |
| 32 | Keys R Processed | 22 - Keys R Processed | Keys processing |
| 45 | Choir L Processed | 29 - Choir L | Choir processing |
| 46 | Choir R Processed | 30 - Choir R | Choir processing |
| 64 | FL1 Processed | 09 - FL1 Processed | Vocal processing |
| 65 | FL2 Processed | 10 - FL2 Processed | Vocal processing |
| 66 | FL3 Processed | 11 - FL3 Processed | Vocal processing |
| 67 | FL4 Processed | 12 - FL4 Processed | Vocal processing |
| 68 | FL5 Processed | 13 - FL5 Processed | Vocal processing |
| 69 | FL6 Processed | 14 - FL6 Processed | Vocal processing |
| 70 | FL7 Processed | 15 - FL7 Processed | Vocal processing |
| 74 | PD Mic Processed | 23 - PD Vox Processed | Pastor vocal |
| 77 | Vox Harmonics RT | 19 - Vox Harmonics RT | FX return |
| 78 | Vox Reverb RT | 20 - Vox Reverb RT | FX return |
| 79 | Crowd L Processed | 31 - Crowd L | Ambient processing |
| 80 | Crowd R Processed | 32 - Crowd R | Ambient processing |
| 81 | Broadcast L Processed | 47 - Broad L Processed | **Broadcast** |
| 82 | Broadcast R Processed | 48 - Broadcast R Processed | **Broadcast** |

#### From Rio3224 (Stage Box – Instruments/Vocals)

| RX Ch | Name | Rio3224 TX | Signal |
|-------|------|-----------|--------|
| 10 | (Choir R) | SB10 - Choir R | Choir mic R |
| 11 | — | 20 | Spare |
| 12 | (Choir L) | SB12 - Choir L | Choir mic L |
| 13 | (Choir C) | SB13 - Choir C | Choir mic C |
| 14 | (Crowd L) | SB14 - Crowd L | Crowd mic L |
| 15 | EG1 L | SB17 - EG1 L | Electric Guitar 1 L |
| 16 | EG1 R | SB18 - EG1 R | Electric Guitar 1 R |
| 17 | EG2 L | SB5 - EG2 L | Electric Guitar 2 L |
| 18 | EG2 R | SB6 - EG2 R | Electric Guitar 2 R |
| 19 | Acoustic | 19 - Acoustic | Acoustic guitar |
| 21 | — | 21 | (Spare) |
| 22 | Aux Keys | SB22 - Aux Keys | Auxiliary keyboard |
| 23 | Tracks L | SB23 - Tracks L | Playback tracks L |
| 24 | Tracks R | SB24 - Tracks R | Playback tracks R |
| 25 | Click | SB25 - Click | Click track |
| 26 | Bass | SB26 - Bass | Bass guitar |
| 27 | Keys L | SB27 - Keys L | Keyboard L |
| 28 | Keys R | SB28 - Keys R | Keyboard R |
| 29 | MD Mic | SB29 - MD Mic | Music Director mic |
| 44 | Click (duplicate) | SB25 - Click | Click (for processing) |

#### From Rio1608 (Drum Stage Box)

| RX Ch | Name | Rio1608 TX | Signal |
|-------|------|-----------|--------|
| 33 | Kick In | Kick in | Kick drum inside |
| 34 | Kick Out | Kick Out | Kick drum outside |
| 35 | Snare Top | Snare Top | Snare top |
| 36 | Snare Bottom | Snare Bottom | Snare bottom |
| 37 | HiHat | HiHat | Hi-hat |
| 38 | Rack 1 | Rack 1 | Rack tom 10" |
| 39 | Rack 2 | Rack 2 | Rack tom 12" |
| 40 | Floor 1 | Floor 1 | Floor tom 16" |
| 41 | Floor 2 | Floor 2 | Floor tom 18" |
| 42 | OH L | OH L | Overhead L |
| 43 | OH R | OH R | Overhead R |
| 48 | — | 16 | (Spare from Rio1608) |

#### From Shure Wireless (ULXD4Q)

| RX Ch | Name | Source Device | Source Ch | Signal |
|-------|------|--------------|-----------|--------|
| 53 | FL1 | ULXD4Q-ea9fd2 | FL1 | Front Line 1 wireless |
| 54 | HDST-2 | ULXD4Q-ea9fd2 | HDST-2 | Headset 2 |
| 55 | FL3 | ULXD4Q-ea9fd2 | FL3 | Front Line 3 wireless |
| 56 | FL4 | ULXD4Q-ea9fd2 | FL4 | Front Line 4 wireless |
| 57 | FL5 | ULXD4Q-eacb78 | FL5 | Front Line 5 wireless |
| 58 | FL6 | ULXD4Q-eacb78 | FL6 | Front Line 6 wireless |
| 59 | FL7 | ULXD4Q-eacb78 | FL7 | Front Line 7 wireless |
| 60 | HDST-1 | ULXD4Q-eacb78 | HDST-1 | Headset 1 (Pastor) |

#### From Workstations

| RX Ch | Name | Source Device | Source Ch | Signal |
|-------|------|--------------|-----------|--------|
| 49 | Resolume L | Resolume-Mac-Studio | 01 | Video software audio L |
| 50 | Resolume R | Resolume-Mac-Studio | 02 | Video software audio R |
| 51 | ProPresenter L | ProPresenter-MacMini | 01 | Presentation audio L |
| 52 | ProPresenter R | ProPresenter-MacMini | 02 | Presentation audio R |

#### From JD-MG-MacBook-Pro (Multitrack Playback – 30ch)

| RX Ch | Name | Source Ch | Signal |
|-------|------|-----------|--------|
| 84 | T Drum L | 01-Drums L | Drum stems L |
| 85 | T Drum R | 02-Drums R | Drum stems R |
| 86 | T Perc L | 03-Perc L | Percussion L |
| 87 | T Perc R | 04-Perc R | Percussion R |
| 88 | T Loop L | 05-Loops L | Loops L |
| 89 | T Loop R | 06-Loops R | Loops R |
| 90 | T Bass L | 07-Bass L | Bass stems L |
| 91 | T Bass R | 08-Bass R | Bass stems R |
| 92 | T Piano L | 09-Piano L | Piano L |
| 93 | T Piano R | 10-Piano R | Piano R |
| 94 | T Keys L | 11-Keys L | Keys L |
| 95 | T Keys R | 12-Keys R | Keys R |
| 96 | T Gtr L | 13-Gtr L | Guitar L |
| 97 | T Gtr R | 14-Gtr R | Guitar R |
| 98 | T Acous L | 15-Acous L | Acoustic L |
| 99 | T Acous R | 16-Acous R | Acoustic R |
| 100 | T Horn L | 17-Horns L | Horns L |
| 101 | T Horn R | 18-Horns R | Horns R |
| 102 | T Strg L | 19-Strg L | Strings L |
| 103 | T Strg R | 20-Strg R | Strings R |
| 104 | T Pad L | 21-Pad L | Pad L |
| 105 | T Pad R | 22-Pad R | Pad R |
| 106 | T Vox L | 23-Vox L | Vocals L |
| 107 | T Vox R | 24-Vox R | Vocals R |
| 108 | T FX L | 25-FX L | FX L |
| 109 | T FX R | 26-FX R | FX R |
| 110 | T Aux L | 27-Aux L | Aux L |
| 111 | T Aux R | 28-Aux R | Aux R |
| 112 | T Guide | 29-Guide | Guide track |
| 113 | T Click | 30-Click | Click track |

#### From MultiTrack-Playback-mini (Secondary Playback – 30ch)

| RX Ch | Name | Source Ch | Signal |
|-------|------|-----------|--------|
| 114-144 | T Drums/Perc/Loops/Bass/Piano/Keys/Gtr/Acous/Horns/Strings/Pad/Vox/FX/Aux/Guide/Click | Various stems | Secondary multitrack (30 channels, same stem layout) |

---

## MG-AVL-Ableton

**Model:** Dante Virtual Soundcard (macOS) v4.5.1 | **Hardware:** Mac Mini | **Encoding:** 32-bit  
**Dante IP:** 192.168.10.10  
**Role:** Primary audio processing — receives raw channels, returns processed audio to DM7

### Ableton TX Channels (Processed Returns → DM7)

| TX Ch | Label | → DM7 RX | Signal |
|-------|-------|----------|--------|
| 01 | Kick Drum Processed | RX 1 | Processed kick |
| 02 | Snare Drum Processed | RX 2 | Processed snare |
| 03 | Toms L Processed | RX 3 | Processed toms L |
| 04 | Toms R Processed | RX 4 | Processed toms R |
| 05 | Overhead L Processed | RX 5 | Processed overhead L |
| 06 | Overhead R Processed | RX 6 | Processed overhead R |
| 07 | Bass Processed | RX 7 | Processed bass |
| 08 | Acoustic Processed | RX 8 | Processed acoustic |
| 09 | FL1 Processed | RX 64 | Processed Front Line 1 |
| 10 | FL2 Processed | RX 65 | Processed Front Line 2 |
| 11 | FL3 Processed | RX 66 | Processed Front Line 3 |
| 12 | FL4 Processed | RX 67 | Processed Front Line 4 |
| 13 | FL5 Processed | RX 68 | Processed Front Line 5 |
| 14 | FL6 Processed | RX 69 | Processed Front Line 6 |
| 15 | FL7 Processed | RX 70 | Processed Front Line 7 |
| 19 | Vox Harmonics RT | RX 77 | Vocal harmonics effect |
| 20 | Vox Reverb RT | RX 78 | Vocal reverb effect |
| 21 | Keys L Processed | RX 31 | Processed keys L |
| 22 | Keys R Processed | RX 32 | Processed keys R |
| 23 | PD Vox Processed | RX 74 | Processed pastor vocal |
| 29 | Choir L | RX 45 | Processed choir L |
| 30 | Choir R | RX 46 | Processed choir R |
| 31 | Crowd L | RX 79 | Processed crowd L |
| 32 | Crowd R | RX 80 | Processed crowd R |
| 42 | HiHat Processed | RX 9 | Processed hi-hat |
| 47 | Broad L Processed | RX 81 | **Broadcast L** |
| 48 | Broadcast R Processed | RX 82 | **Broadcast R** |

---

## Y001-Yamaha-Rio3224-D2-25e264

**Model:** Yamaha Rio3224-D2 (V1.85) | **Capacity:** 32 TX / 24 RX | **IP:** 192.168.10.149  
**Role:** Main stage box (instruments, keys, choir, crowd, playback)  
**Redundancy:** Enabled (dual network interface)

### Rio3224 TX Channels (Stage → Network)

| TX Ch | Label | Signal | Subscribed By |
|-------|-------|--------|---------------|
| 5 | SB5 - EG2 L | Electric Guitar 2 Left | DM7 (RX17), KLANG (RX16) |
| 6 | SB6 - EG2 R | Electric Guitar 2 Right | DM7 (RX18), KLANG (RX17) |
| 10 | SB10 - Choir R | Choir mic Right | DM7 (RX10) |
| 12 | SB12 - Choir L | Choir mic Left | DM7 (RX12) |
| 13 | SB13 - Choir C | Choir mic Center | DM7 (RX13) |
| 14 | SB14 - Crowd L | Crowd mic Left | DM7 (RX14) |
| 17 | SB17 - EG1 L | Electric Guitar 1 Left | DM7 (RX15), KLANG (RX14) |
| 18 | SB18 - EG1 R | Electric Guitar 1 Right | DM7 (RX16), KLANG (RX15) |
| 19 | 19 - Acoustic | Acoustic Guitar | DM7 (RX19), KLANG (RX18) |
| 22 | SB22 - Aux Keys | Auxiliary Keyboard | DM7 (RX22), KLANG (RX22) |
| 23 | SB23 - Tracks L | Playback Tracks L | DM7 (RX23), KLANG (RX23) |
| 24 | SB24 - Tracks R | Playback Tracks R | DM7 (RX24), KLANG (RX24) |
| 25 | SB25 - Click | Click Track | DM7 (RX25, RX44), KLANG (RX25) |
| 26 | SB26 - Bass | Bass Guitar | DM7 (RX26), KLANG (RX13) |
| 27 | SB27 - Keys L | Keyboard Left | DM7 (RX27), KLANG (RX19) |
| 28 | SB28 - Keys R | Keyboard Right | DM7 (RX28), KLANG (RX20) |
| 29 | SB29 - MD Mic | Music Director Mic | DM7 (RX29) |

### Rio3224 RX Channels (Network → Stage Outputs)

| RX Ch | Name | Source Device | Source Ch | Purpose |
|-------|------|--------------|-----------|---------|
| 1 | ST A L | DM7 | TX 135 - ST A L | **FOH Main L** |
| 2 | ST A R | DM7 | TX 136 - ST A R | **FOH Main R** |
| 3 | Mon A Stage | DM7 | TX 143 - Mon A Stage | Stage Monitor A |
| 4 | Mon B Stage | DM7 | TX 144 - Mon B Stage | Stage Monitor B |
| 16 | — | DM7 | TX 132 | (Spare output) |

---

## Y002-Yamaha-Rio1608-D2-28589c

**Model:** Yamaha Rio1608-D2 | **IP:** 192.168.10.238 | **Role:** Drum stage box (all drum microphones)

### Rio1608 TX Channels (Drums → Network)

| TX Ch | Label | Signal | Subscribed By |
|-------|-------|--------|---------------|
| 1 | Kick in | Kick Drum (inside mic) | KLANG (RX1), DM7 (RX33) |
| 2 | Kick Out | Kick Drum (outside mic) | KLANG (RX2), DM7 (RX34) |
| 3 | Snare Top | Snare Top | KLANG (RX3), DM7 (RX35) |
| 4 | Snare Bottom | Snare Bottom | KLANG (RX4), DM7 (RX36) |
| 5 | HiHat | Hi-Hat | KLANG (RX5), DM7 (RX37) |
| 6 | Rack 1 | Rack Tom 10" | KLANG (RX6), DM7 (RX38) |
| 7 | Rack 2 | Rack Tom 12" | KLANG (RX7), DM7 (RX39) |
| 8 | Floor 1 | Floor Tom 16" | KLANG (RX8), DM7 (RX40) |
| 9 | Floor 2 | Floor Tom 18" | KLANG (RX9), DM7 (RX41) |
| 10 | OH L | Overhead Left | KLANG (RX10), DM7 (RX42) |
| 11 | OH R | Overhead Right | KLANG (RX11), DM7 (RX43) |

---

## KLANG-IEM

**Model:** DiGiCo DMI DANTE 64@96z (V4.2.4) | **Capacity:** 64 TX / 64 RX  
**Dante IP:** DHCP (VLAN 130) | **Management IP:** 10.10.20.232  
**Role:** In-Ear Monitor mix processor — receives all inputs, creates personalized stereo mixes for each musician

### KLANG TX Channels (IEM Mixes → AVIO Adapters)

| TX Ch | Label | → Device |
|-------|-------|----------|
| 1-2 | DRUM - IEM 1 L/R | (Drum IEM – not in export as separate AVIO) |
| 3-4 | BASS - IEM L/R | IEM2-BASS |
| 5-6 | EG1 - IEM L/R | IEM3-EG1 |
| 7-8 | EG2 - IEM L/R | IEM4-EG2 |
| 9-10 | FL5 - IEM L/R | IEM1-FL5 |
| 11-12 | FL2 - IEM L/R | IEM6-FL2 |
| 13-14 | KEYS - IEM L/R | IEM7-KEYS |
| 15-16 | ACOUS - IEM L/R | IEM8-ACOUS |
| 17-18 | FL6 - IEM L/R | IEM13-FL6 |
| 19-20 | FL7 - IEM L/R | IEM5-FL7 |
| 21-22 | FL1 - IEM L/R | IEM11-FL1 |
| 23-24 | MIX 12 L/R | (Additional mix) |
| 25-26 | MIX 13 L/R | (Additional mix) |
| 27-28 | FL3 - IEM L/R | IEM14-FL3 |
| 29-30 | MIX 15 L/R | (Additional mix) |
| 31-32 | FL4 - IEM L/R | IEM16-FL4 |

### KLANG RX Channels (Inputs from Network)

| RX Ch | Name | Source Device | Source Ch | Signal |
|-------|------|--------------|-----------|--------|
| 1-11 | Drums | Rio1608 | Kick In through OH R | All drum mics |
| 12 | — | DM7 | TX 12 | (DM7 output) |
| 13 | BASS | Rio3224 | SB26 - Bass | Bass guitar |
| 14-15 | EG1 L/R | Rio3224 | SB17-18 | Electric Guitar 1 |
| 16-17 | EG2 L/R | Rio3224 | SB5-6 | Electric Guitar 2 |
| 18 | ACOUSTIC | Rio3224 | 19 - Acoustic | Acoustic guitar |
| 19-20 | KEYS L/R | Rio3224 | SB27-28 | Keyboard |
| 21-22 | AUXKEY L/R | DM7/Rio3224 | 21/SB22 | Auxiliary keyboard |
| 23-24 | TRACKS L/R | DM7 | TX 23-24 | Playback tracks |
| 25 | CLICK | DM7 | TX 25 | Click track |
| 26-27 | PROPRES L/R | DM7 | TX 26-27 | ProPresenter audio |
| 28 | Announce | DM7 | TX 28 | Announcement |
| 29 | Bass P | DM7 | TX 29 | Bass processed |
| 31 | FL1 | ULXD4Q-ea9fd2 | FL1 | Front Line 1 wireless |
| 32 | FL2 | DM7 | 32 - FL2 D out | Front Line 2 |
| 33 | FL3 | ULXD4Q-ea9fd2 | FL3 | Front Line 3 wireless |
| 34 | FL4 | ULXD4Q-ea9fd2 | FL4 | Front Line 4 wireless |
| 35 | JD VOX | DM7 | 35 - MD Vox D out | Music Director vocal |
| 36 | MD MIC | DM7 | TX 36 | MD mic |
| 37 | TALKBACK | DM7 | 37 - Talkback D out | Talkback |
| 39 | CROWD L | DM7 | TX 39 | Crowd mic L |
| 40 | CROWD R | DM7 | TX 40 | Crowd mic R |
| 41-43 | CHOIR L/C/R | DM7 | TX 41-43 | Choir mics |
| 44 | LV | DM7 | 44 - LV1 D out | Lavelier 1 |
| 45 | Pastor's HDST | ULXD4Q-eacb78 | HDST-1 | Pastor headset |
| 46-47 | Tracks Group L/R | DM7 | Tracks Group L/R | Tracks bus |
| 48-49 | Playback Click/Guide | DM7 | 138/137 | Click & guide from DM7 |
| 51-53 | FL5/FL6/FL7 | ULXD4Q-eacb78 | FL5/FL6/FL7 | Front Line 5-7 wireless |
| 55-56 | Instrument Bus L/R | DM7 | 65-66 | Instrument group bus |

---

## Shure Wireless Receivers

### ULXD4Q-ea9fd2

| TX Ch | Label | Signal | Subscribed By |
|-------|-------|--------|---------------|
| 1 | FL1 | Front Line 1 | DM7 (RX53), KLANG (RX31) |
| 2 | HDST-2 | Headset 2 | DM7 (RX54) |
| 3 | FL3 | Front Line 3 | DM7 (RX55), KLANG (RX33) |
| 4 | FL4 | Front Line 4 | DM7 (RX56), KLANG (RX34) |

### ULXD4Q-eacb78

| TX Ch | Label | Signal | Subscribed By |
|-------|-------|--------|---------------|
| 1 | FL5 | Front Line 5 | DM7 (RX57), KLANG (RX51) |
| 2 | FL6 | Front Line 6 | DM7 (RX58), KLANG (RX52) |
| 3 | FL7 | Front Line 7 | DM7 (RX59), KLANG (RX53) |
| 4 | HDST-1 | Headset 1 (Pastor) | DM7 (RX60), KLANG (RX45) |

---

## BCast-Audio

**Model:** Audinate AVIO-DAO2 | **Role:** Broadcast audio output (analog out to SE-3200 switcher)

| RX Ch | Name | Source Device | Source Ch | Signal |
|-------|------|--------------|-----------|--------|
| 1 | CH1 - BCastL | Y001-Yamaha-DM7-c9a984 | 63 - Post BCast L | **Broadcast Left** |
| 2 | CH2 - BCastR | Y001-Yamaha-DM7-c9a984 | 64 - Pose BCast R | **Broadcast Right** |

> This is the final audio output to the Datavideo SE-3200 switcher for livestream. The 46 ms audio delay is applied in the SE-3200.

---

## AllenHth-2182fc

**Model:** Allen & Heath Dante Option Card (Brooklyn II) | **Capacity:** 64 TX / 64 RX  
**IP:** 192.168.10.22 (static) | **VLAN:** 2  
**Role:** Secondary console or multitrack recorder — receives full input set

### Allen & Heath RX (Inputs – All from DM7 and Wireless)

Receives 40 active channels: DM7 direct outs (RX 1-30), wireless mics via DM7 routing (FL1-4, JD VOX, MD MIC, Talkback, Crowd), plus FL1/FL3/FL4 directly from ULXD4Q-ea9fd2.

---

## IEM AVIO Adapters

All 12 IEM AVIO-DAO2 adapters are receive-only (2 channels each, stereo) and are fed exclusively by KLANG-IEM:

| Device | Musician | KLANG TX Ch | Latency Setting |
|--------|----------|-------------|-----------------|
| IEM1-FL5 | Front Line 5 | 9-10 | 1 ms |
| IEM2-BASS | Bass | 3-4 | 1 ms |
| IEM3-EG1 | Electric Guitar 1 | 5-6 | 1 ms |
| IEM4-EG2 | Electric Guitar 2 | 7-8 | 1 ms |
| IEM5-FL7 | Front Line 7 | 19-20 | 1 ms |
| IEM6-FL2 | Front Line 2 | 11-12 | 1 ms |
| IEM7-KEYS | Keys | 13-14 | 1 ms |
| IEM8-ACOUS | Acoustic | 15-16 | 1 ms |
| IEM11-FL1 | Front Line 1 | 21-22 | 1 ms |
| IEM13-FL6 | Front Line 6 | 17-18 | 1 ms |
| IEM14-FL3 | Front Line 3 | 27-28 | 1 ms |
| IEM16-FL4 | Front Line 4 | 31-32 | 1 ms |

---

## Workstations

### JD-MG-MacBook-Pro
- **Role:** Primary multitrack playback (worship leader's machine)
- **TX:** 30 channels of stems (Drums, Perc, Loops, Bass, Piano, Keys, Guitar, Acoustic, Horns, Strings, Pad, Vox, FX, Aux, Guide, Click)
- **→ DM7:** RX 84-113

### MultiTrack-Playback-mini
- **Role:** Secondary/backup multitrack playback
- **TX:** 30 channels (same stem layout)
- **→ DM7:** RX 114-144

### Resolume-Mac-Studio
- **Role:** Resolume Arena video software (audio output)
- **TX:** 2 channels (stereo)
- **→ DM7:** RX 49-50

### ProPresenter-MacMini
- **Role:** ProPresenter presentation software (audio output)
- **TX:** 2 channels (stereo)
- **→ DM7:** RX 51-52

---

## Related Documents

- [Dante Network Overview](../../../configs/dante/README.md) – Device inventory and clock config
- [Audio Routing](routing.md) – Full audio signal paths
- [Broadcast Audio](../broadcast/audio.md) – Broadcast audio flow detail
- [Broadcast Sync](../broadcast/sync.md) – A/V sync compensation
- [Dante Full Topology Diagram](../../../diagrams/mermaid/dante-full-topology.md) – Visual topology
