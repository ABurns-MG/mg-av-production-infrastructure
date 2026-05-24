# Dante Channel Naming Standards – Main Sanctuary

> **Purpose:** Standardize Dante channel labels across all devices for clarity in Dante Controller, routing documentation, and troubleshooting.  
> **Convention:** Names should identify the signal content and direction clearly. Max 31 characters (Dante limit).  
> ***Italicized entries*** = names that need to be assigned/updated in Dante Controller.

---

## Resolume-Mac-Studio (DVS – Mac Studio)

Currently all TX channels are labeled generically ("01", "02", etc.). Assign these names:

| TX Ch | Current Label | Suggested Name | Signal |
|-------|---------------|----------------|--------|
| 1 | 01 | ***Spotify L*** | Spotify playback left (to DM7 Ch 32) |
| 2 | 02 | ***Spotify R*** | Spotify playback right (to DM7 Ch 33) |
| 3 | 03 | ***Resolume L*** | Resolume Arena audio left (to DM7 Ch 49) |
| 4 | 04 | ***Resolume R*** | Resolume Arena audio right (to DM7 Ch 50) |
| 5-21 | 05-21 | *(leave as-is unless assigned)* | Unused |

> **Note:** DM7 subscribes to Resolume-Mac-Studio TX 1-2 for Spotify (RX 32-33 mapped to "SPOTIFY" channels) and TX 1-2 also route to Resolume L/R on DM7 RX 49-50. **Clarification needed:** Are Spotify and Resolume on separate TX pairs, or are TX 1-2 shared for both? Based on DM7 RX 49-50 subscribing to Resolume TX 01-02 in the Dante export, they appear shared. Consider separating:
> - TX 1-2 = Spotify
> - TX 3-4 = Resolume video audio
>
> Then re-subscribe DM7 RX 49-50 to TX 3-4 instead of TX 1-2.

---

## ProPresenter-MacMini (DVS – Mac Mini)

| TX Ch | Current Label | Suggested Name | Signal |
|-------|---------------|----------------|--------|
| 1 | 01 | ***ProPresenter L*** | Presentation audio left |
| 2 | 02 | ***ProPresenter R*** | Presentation audio right |

| RX Ch | Current Label | Suggested Name | Signal |
|-------|---------------|----------------|--------|
| 1 | *(unknown)* | ***Room Meas Mic*** | DBX RTA-m measurement mic (from DM7 TX 50) for REW SPL meter |

---

## JD-MG-MacBook-Pro (DVS – Primary Multitrack Playback)

TX channels already labeled with stem names (01-Drums L, etc.). No changes needed.

---

## MultiTrack-Playback-mini (DVS – Secondary Multitrack Playback)

TX channels already labeled with stem names. No changes needed.

---

## Y001-Yamaha-DM7-c9a984 (DM7 Console)

Most TX channels are properly labeled. Suggested additions/corrections:

| TX Ch | Current Label | Suggested Name | Reason |
|-------|---------------|----------------|--------|
| 36 | *(blank)* | ***MD Mic D out*** | Music Director mic direct out |
| 38 | *(blank)* | ***Crowd R D out*** | Crowd mic right direct out |
| 39 | *(blank)* | ***Crowd L D out*** | Crowd mic left direct out |
| 40 | *(blank)* | ***Choir Lf D out*** | Choir loft direct out |
| 50 | Room Measurement Mic | *(OK as-is)* | — |
| 61 | Pre BCast Audio L | *(OK as-is)* | — |
| 62 | Pre BCast Audio R | *(OK as-is)* | — |
| 64 | Pose BCast R | ***Post BCast R*** | Fix typo ("Pose" → "Post") |

---

## BCast-Audio (AVIO-DAO2)

| RX Ch | Current Label | Suggested Name | Signal |
|-------|---------------|----------------|--------|
| 1 | CH1 - BCastL | *(OK as-is)* | — |
| 2 | CH2 - BCastR | *(OK as-is)* | — |

---

## KLANG-IEM (Monitor Processor)

TX channels already labeled with musician IEM names. No changes needed.

---

## IEM AVIO Adapters (IEM1 through IEM16)

All properly named by musician position. No changes needed.

---

## ULXD4Q-ea9fd2 / ULXD4Q-eacb78 (Shure Wireless)

TX channels labeled with position names (FL1, FL3, etc.). No changes needed.

---

## Rio3224 / Rio1608 (Stage Boxes)

TX channels already labeled with instrument/mic names. No changes needed.

---

## AllenHth-2182fc (Allen & Heath – ME-1 Backup IEM Interface)

| TX Ch | Current Label | Suggested Name | Signal |
|-------|---------------|----------------|--------|
| 1-64 | *(generic)* | ***Mirror DM7 input names*** | Should match DM7 channel names for ME-1 consistency |

---

## Naming Convention Rules

1. **Format:** `[Source/Signal] [L/R if stereo]` — e.g., "Spotify L", "Post BCast R"
2. **Direct outs:** Append "D out" — e.g., "FL1 D out", "MD Mic D out"
3. **Processed returns:** Append "Processed" or "P" — e.g., "Kick Drum Processed"
4. **Buses:** Use bus name — e.g., "ST A L", "Mon A Stage"
5. **IEM mixes:** Use musician position — e.g., "BASS - IEM L"
6. **Max length:** 31 characters (Dante protocol limit)
7. **Avoid:** Special characters, abbreviations that aren't universally understood

---

## How to Apply Names in Dante Controller

1. Open **Dante Controller**
2. Navigate to **Device View** → select the device
3. Click the **Device Config** tab
4. Under **Transmit** or **Receive**, double-click the channel label
5. Type the new name and press Enter
6. Repeat for each channel
7. **Save a new preset** after all names are applied (File → Save Preset)
