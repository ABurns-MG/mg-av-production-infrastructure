# Dante Network Topology – Main Sanctuary

## Device Topology (Known Devices)

```mermaid
flowchart TD
	subgraph CLOCK["Clock Domain"]
		DM7["Y001-Yamaha-DM7-c9a984<br/>Yamaha DM7<br/>★ CLOCK MASTER<br/>FOH + Broadcast Mixing"]
	end

	subgraph WORKSTATIONS["Workstations"]
		ABL["MGC-LC-L-AVL-001<br/>Dante Virtual Soundcard (macOS)<br/>Ableton Live<br/>32 TX / 32 RX"]
	end

	subgraph PENDING["Other Devices (20+ pending full export)"]
		DEV1["Stage Box(es)?"]
		DEV2["Monitor Console?"]
		DEV3["Recording PC?"]
		DEV4["Other I/O?"]
	end

	subgraph NETWORK["Dante Network Infrastructure"]
		SW["Network Switch(es)<br/>(Model TBD)"]
	end

	DM7 <-->|"Dante<br/>48kHz"| SW
	ABL <-->|"Dante<br/>48kHz"| SW
	DEV1 <-->|"Dante"| SW
	DEV2 <-->|"Dante"| SW
	DEV3 <-->|"Dante"| SW
	DEV4 <-->|"Dante"| SW

	style DM7 fill:#4dabf7,color:#fff
	style ABL fill:#69db7c,color:#fff
	style PENDING fill:#ffe066,color:#333
```

## Audio Flow Between Known Devices

```mermaid
flowchart LR
	subgraph DM7["DM7 (Clock Master)"]
		DM7_TX["TX: 23+ channels<br/>(Direct outs to Ableton)"]
		DM7_RX["RX: 25+ channels<br/>(Processed returns from Ableton)"]
	end

	subgraph ABL["Ableton DVS"]
		ABL_RX["RX 1-24: Raw inputs<br/>Drums, Keys, Instruments,<br/>Vocals, Speech, Ambient, Click"]
		ABL_TX["TX 1-25: Processed returns<br/>+ FX sends"]
	end

	DM7_TX -->|"24 channels<br/>Direct outs + custom routes"| ABL_RX
	ABL_TX -->|"25 channels<br/>Processed + FX + Broadcast"| DM7_RX
```

## Full Network Topology (To Be Completed)

> This diagram will be expanded when the full Dante Controller export (with all 20+ devices and subscriptions) is provided.

```mermaid
flowchart TD
	DM7["Y001-Yamaha-DM7-c9a984<br/>★ Clock Master"] --- SW1["Primary Switch"]
	ABL["MGC-LC-L-AVL-001<br/>Ableton DVS"] --- SW1

	SW1 --- D3["Device 3"]
	SW1 --- D4["Device 4"]
	SW1 --- D5["Device 5"]
	SW1 --- DN["... (20+ devices)"]

	style DM7 fill:#4dabf7,color:#fff
	style ABL fill:#69db7c,color:#fff
```

## Notes

- DM7 is the preferred clock master for the entire network
- All devices operate at 48 kHz
- Default Dante latency: 4 ms per network hop
- Full topology will be documented once complete preset export is available
