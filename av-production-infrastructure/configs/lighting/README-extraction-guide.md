# Onyx NX4 Show File Extraction Guide

> How to extract readable data from an Obsidian Onyx `.OnyxShow` file for documentation purposes.

---

## File Format

| Layer | Format | Notes |
|-------|--------|-------|
| Outer | ZIP archive | Standard ZIP container |
| Inner | SQL Server MDF | Single file named `Show` |
| Data | Relational tables + embedded XML | Fixture definitions stored as XML blobs |

---

## Extraction Workflow

### Step 1: Extract the ZIP

```powershell
& 'C:\Program Files\7-Zip\7z.exe' x "ShowFile.OnyxShow" -o"C:\Temp\onyxshow" -y
```

This produces a single file called `Show` (no extension) which is a SQL Server MDF.

### Step 2: Read Fixture Types (String Extraction)

Since attaching the MDF to LocalDB may fail due to version mismatches, use Unicode string extraction:

```powershell
$bytes = [IO.File]::ReadAllBytes('C:\Temp\onyxshow\Show')
$str = [Text.Encoding]::Unicode.GetString($bytes)

# Find fixture type XML paths (manufacturer/model/mode)
$m = [Text.RegularExpressions.Regex]::Matches($str,
	'(Chauvet|Martin|ETC|Elation|ADJ|Robe|Generic|Vari-Lite|Obsidian)/[^<\x00]{5,80}\.xml')
$m | ForEach-Object { $_.Value } | Sort-Object -Unique
```

### Step 3: Find Named Fixture Instances

```powershell
# Fixtures are named with id="Model, Position" pattern
$m = [Text.RegularExpressions.Regex]::Matches($str, 'id="([^"]{3,50})"')
$ids = @(); foreach($x in $m){ $ids += $x.Groups[1].Value }
$ids | Sort-Object -Unique | Where-Object {
	$_ -notmatch '(^[a-f0-9\-]{20,}|window|docking|element|xpointer|http|xml)'
}
```

### Step 4: Find Cuelist/Preset Names

```powershell
# name="" attributes contain cuelist names, view names, preset names
$m = [Text.RegularExpressions.Regex]::Matches($str, 'name="([^"]{2,60})"')
$names = @(); foreach($x in $m){ $names += $x.Groups[1].Value }
$names | Sort-Object -Unique | Where-Object {
	$_ -notmatch '(Channel|function|Shutter|Reset|Lamp|address|mask|offset|resolution)'
}
```

### Step 5: Find Button/Cell Labels

```powershell
# text="" attributes are used for button labels and display text
$m = [Text.RegularExpressions.Regex]::Matches($str, 'text="([^"]{2,80})"')
$texts = @(); foreach($x in $m){ $texts += $x.Groups[1].Value }
$texts | Sort-Object -Unique
```

### Step 6 (Optional): Attach to SQL Server LocalDB

If you have a compatible SQL Server version:

```powershell
sqllocaldb start MSSQLLocalDB
sqlcmd -S "(localdb)\MSSQLLocalDB" -Q "CREATE DATABASE OnyxShow ON (FILENAME='C:\Temp\OnyxShow.mdf') FOR ATTACH_REBUILD_LOG"
sqlcmd -S "(localdb)\MSSQLLocalDB" -d OnyxShow -Q "SELECT TABLE_NAME FROM INFORMATION_SCHEMA.TABLES"
```

> **Note:** This may fail if the MDF was created by a different SQL Server version than your LocalDB instance.

---

## Key Tables (when SQL access works)

| Table | Contents |
|-------|----------|
| `CueListsV2` / `CueListsV3` | Cuelist definitions, tracking settings |
| `Fixture` | Patched fixture instances with addresses |
| `FixtureType` | Fixture personality XML definitions |
| `DMXChannel` | DMX channel assignments |
| `DynamicGroup` | Fixture groups |
| `EffectMacro` | Stored effect macros |
| `DMXSnapRules` | Snapshot/preset rules |

---

## Tips

- The show file name encodes: `{ShowName}_{Date}_{Time}_Build_{Major}_{Minor}_{Build}_{Revision}.OnyxShow`
- `minBuild` in the header string indicates the minimum Onyx version required to open the file
- Fixture definitions are stored as full GDTF-style XML inside the MDF
- Position codes (GW01-xx, GW02-xx) in fixture instance names map to physical grid locations
- Color wheel, gobo wheel, and prism data are embedded in the fixture type XML

---

## Limitations

- DMX address assignments are stored in binary table rows, not easily readable via string extraction
- Cuelist cue-level data (individual cue values/timing) requires SQL query access
- Universe assignments require proper MDF attachment
- Show file must be from a compatible Onyx build version for LocalDB attachment
