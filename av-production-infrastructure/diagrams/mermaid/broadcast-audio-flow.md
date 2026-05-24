# Broadcast Audio Signal Flow – Main Sanctuary

## Full Broadcast Audio Path (DM7 → Ableton → DM7 → SE-3200)

```mermaid
flowchart LR
	subgraph STAGE["Stage Inputs"]
		MIC[Microphones<br/>FL1-5, Pastor, MC1]
		INST[Instruments<br/>Bass, EG1-2, Acoustic]
		DRUMS[Drums<br/>Kick, Snare, Rack 1-2, Floor Tom]
		KEYS[Keys<br/>Keys L/R, Keys 2 L/R]
		CROWD[Crowd Mics<br/>Crowd 1-2]
	end

	subgraph DM7_OUT["Y001-Yamaha-DM7-c9a984<br/>(Clock Master)"]
		DM7_MIX[DM7 Mixing Engine]
		DM7_DOUT[Dante TX<br/>Direct Outs]
	end

	subgraph DANTE_NET["Dante Network (4 ms/hop)"]
		D_SEND[Dante Send<br/>4 ms]
		D_RETURN[Dante Return<br/>4 ms]
	end

	subgraph ABLETON["MGC-LC-L-AVL-001<br/>Ableton Live (DVS macOS)"]
		ABL_RX[RX Channels 1-24<br/>Individual inputs]
		ABL_PROC[Plugin Processing<br/>181 ms]
		ABL_IO[I/O + Buffers<br/>10.7 ms]
		ABL_TX[TX Channels 1-25<br/>Processed returns + FX]
	end

	subgraph DM7_IN["DM7 Return Path"]
		DM7_RX[DM7 Dante RX<br/>Processed Returns]
		DM7_BCAST[Broadcast Bus<br/>~1 ms processing]
	end

	subgraph SE3200["Datavideo SE-3200"]
		SE_AUD[Audio Input]
		SE_DELAY[Audio Delay<br/>46 ms]
		SE_PGM[PGM Output<br/>SYNCED]
	end

	subgraph VIDEO_PATH["Video Pipeline (150-160 ms)"]
		CAM[Cameras] --> SE_VID[SE-3200 Video Processing]
		SE_VID --> SE_PGM
	end

	MIC --> DM7_MIX
	INST --> DM7_MIX
	DRUMS --> DM7_MIX
	KEYS --> DM7_MIX
	CROWD --> DM7_MIX
	DM7_MIX --> DM7_DOUT
	DM7_DOUT --> D_SEND
	D_SEND --> ABL_RX
	ABL_RX --> ABL_IO
	ABL_IO --> ABL_PROC
	ABL_PROC --> ABL_TX
	ABL_TX --> D_RETURN
	D_RETURN --> DM7_RX
	DM7_RX --> DM7_BCAST
	DM7_BCAST --> SE_AUD
	SE_AUD --> SE_DELAY
	SE_DELAY --> SE_PGM
```

## Latency Breakdown Diagram

```mermaid
flowchart TD
	subgraph AUDIO["Audio Path (≈200 ms total)"]
		A1["DM7 → Dante Send<br/>4 ms"] --> A2["Ableton I/O + Buffers<br/>10.7 ms"]
		A2 --> A3["Ableton Plugin Chain<br/>181 ms ⚠️ DOMINANT"]
		A3 --> A4["Dante Return<br/>4 ms"]
		A4 --> A5["DM7 Processing<br/>~1 ms"]
	end

	subgraph VIDEO["Video Path (≈155 ms total)"]
		V1["Camera Capture"] --> V2["SE-3200 Processing<br/>≈150-160 ms"]
	end

	subgraph SYNC["Sync Compensation"]
		A5 --> COMP["SE-3200 Audio Delay<br/>46 ms"]
		V2 --> PGM["PGM Output"]
		COMP --> PGM
	end

	style A3 fill:#ff6b6b,color:#fff
	style COMP fill:#51cf66,color:#fff
```

## Ableton Channel Flow (Detail)

```mermaid
flowchart LR
	subgraph RX["Ableton RX (FROM DM7)"]
		RX_D[Drums: Kick, Snare,<br/>Rack 1-2, Floor Tom<br/>Ch 1-5]
		RX_K[Keys: Key2 L/R,<br/>Keys L/R<br/>Ch 6-7, 13-14]
		RX_I[Instruments: Bass,<br/>EG1-2, Acoustic<br/>Ch 9, 11-12, 15]
		RX_V[Vocals: FL1-5<br/>Ch 16-20]
		RX_S[Speech: MC1, Pastor<br/>Ch 21-22]
		RX_A[Ambient: Crowd 1-2<br/>Ch 23-24]
		RX_U[Utility: Click<br/>Ch 8]
	end

	subgraph PROC["Processing (181 ms)"]
		P[Lookahead Limiters<br/>Linear-Phase EQ<br/>FX Processing]
	end

	subgraph TX["Ableton TX (TO DM7)"]
		TX_D[Drums: Kick, Snare,<br/>Rack 1-2<br/>Ch 14-17]
		TX_K[Keys: Keys L/R,<br/>Keys 2 L/R<br/>Ch 18-21]
		TX_I[Instruments: Bass,<br/>EG1-2, Acoustic<br/>Ch 10-13]
		TX_V[Vocals: FL1-5<br/>Ch 1-5]
		TX_S[Speech: Pastor, MC1<br/>Ch 6-7]
		TX_A[Ambient: Crowd 1-2<br/>Ch 8-9]
		TX_F[FX: FL1-4 FX<br/>Ch 22-25]
	end

	RX_D --> P
	RX_K --> P
	RX_I --> P
	RX_V --> P
	RX_S --> P
	RX_A --> P
	RX_U --> P
	P --> TX_D
	P --> TX_K
	P --> TX_I
	P --> TX_V
	P --> TX_S
	P --> TX_A
	P --> TX_F
```

## Sync Decision Diagram

```mermaid
flowchart TD
	START["Sync Issue Detected"] --> CHECK1{"Is SE-3200 audio<br/>delay still 46 ms?"}
	CHECK1 -->|No| FIX1["Reset to 46 ms"]
	CHECK1 -->|Yes| CHECK2{"Has Ableton plugin<br/>chain changed?"}
	CHECK2 -->|Yes| MEASURE["Re-measure:<br/>Run VLC sync test"]
	CHECK2 -->|No| CHECK3{"Clock drift?<br/>Check Dante Controller"}
	CHECK3 -->|Yes| FIX3["Verify DM7 is<br/>clock master"]
	CHECK3 -->|No| CHECK4{"New device in chain?"}
	CHECK4 -->|Yes| MEASURE
	CHECK4 -->|No| DEEP["Deep investigation<br/>needed"]
	MEASURE --> CALC["New delay =<br/>Current delay − Audio offset"]
	CALC --> APPLY["Apply new value<br/>to SE-3200"]
	APPLY --> VERIFY["Verify with<br/>transient test"]
	VERIFY --> DOC["Update sync.md<br/>+ changelog.md"]
```

## Notes

- Render these diagrams on GitHub (native Mermaid support) or with any Mermaid-compatible viewer
- The broadcast audio path is the longest-latency audio chain due to the 181 ms plugin processing
- All timing values are measured, not estimated (see [Broadcast Sync](../../systems/main-sanctuary/broadcast/sync.md))
