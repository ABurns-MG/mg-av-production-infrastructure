# Route Documentation Template

Use this template when documenting a new signal route (audio, video, or combined).

---

# [Room] – [Route Name]

## Route Summary

| Property | Value |
|----------|-------|
| Route type | Audio / Video / Combined |
| Source | |
| Destination | |
| Total latency | ___ ms |
| Measurement date | YYYY-MM-DD |
| Status | Active / Planned / Deprecated |

## Signal Path

```
Source
	→ [latency] → Segment 1 description
	→ [latency] → Segment 2 description
	→ [latency] → Segment N description
	→ Destination
```

## Segment Breakdown

| Segment | Source | Destination | Connection | Latency (ms) | Notes |
|---------|--------|-------------|------------|--------------|-------|
| 1 | | | | | |
| 2 | | | | | |
| N | | | | | |
| **Total** | | | | **___ ms** | |

## Processing

| Stage | Device/Plugin | Purpose | Added Latency | Notes |
|-------|--------------|---------|---------------|-------|
| | | | | |

## Sync Implications

- Regime: Audio faster / slower / matched with video
- Compensation method:
- Compensation value:
- Compensation device:

## Measurement Method

| Parameter | Value |
|-----------|-------|
| Method | (VLC test / DAW measurement / transient test) |
| Test signal | |
| Result | |
| Conditions | |

## Dependencies

- Upstream: (what feeds this route)
- Downstream: (what this route feeds)
- Clock source:

## Change Sensitivity

| Change | Expected Impact |
|--------|----------------|
| | |

## Related Documents

- [Link](path) – Description

## Last Verified

YYYY-MM-DD
