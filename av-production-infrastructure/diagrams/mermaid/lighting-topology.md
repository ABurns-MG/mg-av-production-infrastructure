# Lighting System Topology – Main Sanctuary

---

## Signal Flow

```mermaid
flowchart TD
	NX4["Obsidian Onyx NX4<br/>Lighting Console"]

	subgraph DMX["DMX-512 Outputs"]
		U1["Universe 1"]
		U2["Universe 2"]
		U3["Universe 3+"]
	end

	subgraph Spots["Moving Heads – Spots"]
		R1["Chauvet Rogue R1 Spot ×5"]
		R1X["Chauvet Rogue R1X Spot"]
		RH1["Chauvet Rogue RH1 Hybrid"]
		I475["Chauvet Intimidator 475Z ×6"]
		L300["Chauvet Legend 300E Spot ×2"]
		MIII["Martin MAC III Profile"]
		MVP["Martin MAC Viper Profile"]
	end

	subgraph Wash["Moving Heads – Wash"]
		R3W["Chauvet Rogue R3 Wash"]
		M250["Martin MAC 250 Wash"]
		MAUR["Martin MAC Aura"]
		MTW1["Martin MAC TW1"]
		M401["Martin MAC 401 Dual"]
		RUSH["Martin Rush MH 6 Wash CT"]
	end

	subgraph LED["LED & Conventional"]
		COL["Chauvet COLORado 1 Tri Tour"]
		OVA["Chauvet Ovation E-190WW"]
		M101["Martin MAC 101"]
		SB54["Martin StageBar 54"]
		SEL["ETC Selador"]
		VL["Vari-Lite VL1000 TS"]
		GEN["Generic Dimmers"]
	end

	NX4 --> U1
	NX4 --> U2
	NX4 --> U3

	U1 --> Spots
	U2 --> Wash
	U2 --> LED
	U3 --> GEN
```

---

## Fixture Position Layout

```mermaid
flowchart LR
	subgraph Grid["Lighting Grid (Plan View)"]
		direction TB
		subgraph Row1["Row 1 (GW01 / GW1) — Downstage"]
			GW101["GW1-01<br/>Rogue R1"]
			GW102["GW01-02<br/>Legend 300E"]
			GW103["GW1-03<br/>Rogue R1"]
			GW104["GW01-04<br/>Rogue R1"]
			GW106["GW1-06<br/>Rogue R1"]
			GW107["GW01-07<br/>Rogue R1"]
		end
		subgraph Row2["Row 2 (GW02 / GW2) — Upstage"]
			GW201["GW02-01<br/>Intim 475Z"]
			GW202["GW02-02<br/>Intim 475Z"]
			GW203["GW02-03<br/>Legend 300E"]
			GW204["GW02-04<br/>Intim 475Z<br/>+ RH1 Hybrid"]
			GW205["GW02-05<br/>Intim 475Z"]
			GW207["GW02-07<br/>Intim 475Z"]
			GW208["GW02-08<br/>Intim 475Z"]
		end
	end

	STAGE["🎤 Stage"] ~~~ Grid
```

---

## Cuelist Signal Flow

```mermaid
flowchart TD
	subgraph Playback["NX4 Playback"]
		FADERS["Hardware Faders"]
		TOUCH["Touchscreen"]
		GO["Go Button"]
	end

	subgraph Cuelists["Active Cuelists (Layered)"]
		POS["Position Presets<br/>(R1 STAGE, PT Off)"]
		COL["Color Cuelists<br/>(BG Col, Waves)"]
		FX["Effect Cuelists<br/>(Wave, Double Wave)"]
		INT["Intensity<br/>(Dimmer, Strobe)"]
		GLOBAL["Global Overrides<br/>(Global FX, Global Fade)"]
	end

	subgraph Priority["Priority (LTP/HTP)"]
		HTP["HTP: Intensity<br/>(highest takes precedence)"]
		LTP["LTP: Color, Position, Beam<br/>(latest takes precedence)"]
	end

	FADERS --> Cuelists
	TOUCH --> Cuelists
	GO --> Cuelists

	POS --> LTP
	COL --> LTP
	FX --> LTP
	INT --> HTP
	GLOBAL --> LTP
```

---

## Related Documents

- [Dante Full Topology](dante-full-topology.md) — Audio network diagram
- [Broadcast Audio Flow](broadcast-audio-flow.md) — Audio signal chain
