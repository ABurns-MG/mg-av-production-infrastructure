# DM7 Editor Data Extraction Guide

> **Purpose:** Extract readable scene/setup data from Yamaha DM7 Editor's application cache without needing to decode the proprietary `.dm7f` binary format.

## Prerequisites

- **Yamaha DM7 Editor** installed and running with the target scene loaded
- **PowerShell** (Windows) or equivalent scripting tool
- The scene must be **currently open** in DM7 Editor (the app writes live state to its cache)

## File Locations

| Data | Path | Contains |
|------|------|----------|
| **Current Scene** | `%LOCALAPPDATA%\Yamaha\DM7 Editor\Current\CurrentBackupFile.bup` | Active mixing scene (channel names, processing, routing) |
| **Setup** | `%LOCALAPPDATA%\Yamaha\DM7 Editor\Setup\SetupBackupFile.bup` | System setup (I/O patch, Dante routing, bus config) |
| **Scene Library** | `%LOCALAPPDATA%\Yamaha\DM7 Editor\Scene\UserA\` | Stored scenes |
| **Dante Input Patch Library** | `%LOCALAPPDATA%\Yamaha\DM7 Editor\Library\User\DanteInputPatch\` | Saved Dante input patches |
| **Plugin Library** | `%LOCALAPPDATA%\Yamaha\DM7 Editor\Library\User\PlugIn\` | Saved plugin presets |

### Full Directory Structure
```
%LOCALAPPDATA%\Yamaha\DM7 Editor\
├── cache\qmlcache\          (UI cache, not useful)
├── Current\                  ★ ACTIVE SCENE STATE
├── InternalStorage\
├── LastSetting\
├── Library\
│   ├── Factory\             (Factory presets)
│   └── User\                ★ USER LIBRARIES
│       ├── CHInput\
│       ├── CHOutput\
│       ├── DanteInputPatch\ ★ DANTE PATCHES
│       ├── FX\
│       ├── GEQ\
│       ├── PEQ\
│       └── PlugIn\          ★ PLUGIN PRESETS (per type)
├── PresetList\
├── Scene\                   ★ SCENE STORAGE
│   ├── UserA\
│   ├── UserB\
│   ├── _SceneUA\
│   └── _SceneUB\
├── SceneList\
├── Setup\                   ★ SYSTEM SETUP
├── System\
├── tmp\
├── Unloadable\
└── UserAccount\
```

## File Format

All `.bup` files use Yamaha's **MBDF** (Multi-Block Data Format):
- Header: `#YAMAHA MBDFBackup` or `#YAMAHA MBDFProjectFile`
- Structure: Field definitions followed by binary/compressed data blocks
- **Key insight:** Channel names, colors, icons, processing types, and bus names are stored as **plain ASCII strings** within the binary — they can be extracted with regex without full format decoding

## Extraction Method

### Step 1: Extract All Readable Strings

```powershell
$path = "$env:LOCALAPPDATA\Yamaha\DM7 Editor\Current\CurrentBackupFile.bup"
$bytes = [System.IO.File]::ReadAllBytes($path)
$enc = [System.Text.Encoding]::GetEncoding(28591)  # Latin-1 (preserves all bytes)
$str = $enc.GetString($bytes)
$m = [System.Text.RegularExpressions.Regex]::Matches($str, '[\x20-\x7E]{3,}')
$all = @()
foreach ($x in $m) { $all += $x.Value }
```

### Step 2: Extract Channel Names with Colors

Channel data follows a pattern: `[ChannelName] [Color] [Icon]` where Color is one of the Yamaha palette names.

```powershell
$colors = @('White','Red','Yellow','Green','Blue','Purple','Cyan','Orange','Pink',
			'LightYellow','LightGreen','LightBlue')

# Filter for name+color pairs, excluding known processing/parameter keywords
$exclude = 'PRECISE|SMOOTH|AGGRESSIVE|EXPANDER|GATE|COMP|SELF|NONE|STEREO|Classic|LPF|HPF|BPF|ST/M|2PAN|PM Comp'

$channels = @()
for ($i = 0; $i -lt $all.Count - 1; $i++) {
	if ($colors -contains $all[$i+1] -and 
		$all[$i].Length -ge 3 -and 
		$all[$i].Length -le 12 -and 
		$all[$i] -notmatch $exclude) {
		$channels += "$($channels.Count + 1): $($all[$i]) ($($all[$i+1]))"
	}
}
$channels
```

### Step 3: Search for Specific Signal Names

```powershell
# Find all strings matching known signal keywords
$keywords = 'Kick|Snare|Bass|FL\d|Keys|Vocal|Choir|Click|Guide|BCast|Pastor|Drum|Acoustic|EG\d|Mix|Matrix|Stereo'
$all | Where-Object { $_ -match $keywords }
```

### Step 4: Extract Processing Chain per Channel

Each channel block in order contains:
1. **Channel Name** (e.g., "KICK IN")
2. **Color** (e.g., "Yellow")
3. **Icon** (e.g., "Kick")
4. **EQ Type** (e.g., "PRECISE" repeated for each band)
5. **Gate Type** (e.g., "EXPANDER", "GATE")
6. **Compressor Type** (e.g., "Classic Comp", "PM Comp")
7. **Insert assignments** (e.g., "SELF POST EQ", "LPF", "HPF", "BPF", "NONE")
8. **Pan mode** (e.g., "ST/M", "2PAN", "STEREO")

```powershell
# Find channel start positions and extract surrounding context
for ($i = 0; $i -lt $all.Count; $i++) {
	if ($all[$i] -eq 'KICK IN') {  # Replace with target channel name
		$all[$i..($i + 40)] -join "`n"
		break
	}
}
```

## Interpreting the Channel List

### Channel Numbering Convention (DM7)
- **Ch 1-72:** Input channels (mono or stereo-paired)
- **Ch 73-144:** Additional input channels (continued)
- **Mix buses:** Appear after input channels with names like "MX37", "FOYER", "BROADCST"
- **Matrix:** Named outputs like "Mon A", "Mon B", "STAGEMON"
- **Stereo buses:** "ST A", "ST B"
- **DCAs:** Named group masters like "BAND", "VOCALS", "Drum ALL"

### Color Coding (MercyGate Convention)
| Color | Meaning |
|-------|---------|
| Yellow | Instruments & Drums (raw stage inputs) |
| Red | Vocals & Speech |
| Blue | Playback / Tracks / Digital sources |
| Purple | Processed returns (from Ableton) & Main outputs |
| Orange | Buses, FX returns, Matrix outputs, DCAs |
| White | Utility (click, talkback, measurement, crowd) |
| Pink | Special (e.g., Choir sub-channel) |

## Setup File (Dante Patch Data)

The Setup file contains I/O patching but is larger and more compressed. Use the same string extraction technique:

```powershell
$path = "$env:LOCALAPPDATA\Yamaha\DM7 Editor\Setup\SetupBackupFile.bup"
$bytes = [System.IO.File]::ReadAllBytes($path)
$str = [System.Text.Encoding]::GetEncoding(28591).GetString($bytes)
$m = [System.Text.RegularExpressions.Regex]::Matches($str, '[\x20-\x7E]{3,}')
$all = @(); foreach ($x in $m) { $all += $x.Value }

# Look for Dante-related structure
$all | Where-Object { $_ -match 'Dante|DNTINP|DNTOUT|Patch' }
```

## Limitations

- **No numeric parameter values:** Gain, frequency, threshold values are stored as binary floats — they cannot be reliably extracted with string matching alone.
- **No explicit channel-to-Dante-TX mapping:** The Dante output patch (which console bus → which Dante TX) is stored in binary form in the Setup file. Use the Dante Controller export XML to get this mapping instead.
- **Ordering assumptions:** The channel name extraction assumes names appear sequentially in memory — this has been validated for DM7 Editor v1.73 but may vary in future versions.
- **File must be current:** The `CurrentBackupFile.bup` only reflects what's actively loaded in DM7 Editor. If you load a different scene, the file updates.

## Cross-Reference with Dante Controller Export

The DM7 Editor data gives you **internal console routing** (channel names, bus assignments, processing). The **Dante Controller XML export** gives you **network-level routing** (subscriptions between devices). Together they provide the complete signal path:

```
Physical Input → DM7 HA → Console Channel (from DM7 Editor)
						 → Dante TX (from Dante export)
						 → Network → Dante RX on destination device (from Dante export)
```

## Recommended Export Workflow

1. Open scene in DM7 Editor
2. Run PowerShell extraction scripts above → save output to text files
3. Export Dante Controller preset (File → Save Preset → Include Subscriptions + All Devices)
4. Both outputs together = complete system documentation source
