# Main Sanctuary – Streaming Configuration

> **Last Updated:** 2026-05-24

---

## Signal Path

```
SE-3200 PGM (SDI) ──→ Encoder ──RTMP──→ Streaming Platform(s)
                         ↑
              Broadcast Audio (46 ms delayed, synced)
```

## Platform

> **TODO:** Confirm active platforms (YouTube Live, Facebook Live, custom RTMP, etc.) during site visit.

## Encoding Settings

> **TODO:** Document from encoder interface during site visit.

| Parameter | Value |
|-----------|-------|
| Resolution | 1080p (assumed) |
| Frame Rate | 60p or 30p (TBD) |
| Bitrate | (TBD) |
| Codec | H.264 (assumed) |
| Keyframe interval | (TBD) |

## Recording / Archive

| Device | IP | Role |
|--------|-----|------|
| MG-Cloud-Store | 10.10.20.7 | Blackmagic Media Cloud Store 20TB |
| MG_Hyperdeck-A | 10.10.20.13 | Podcast streaming HyperDeck |

## Redundancy

> **TODO:** Document backup stream config if applicable.

## Related Documents

- [Broadcast Audio](audio.md) — audio chain to SE-3200
- [Broadcast Sync](sync.md) — delay compensation
- [Switcher Settings](../video/switcher-settings.md) — SE-3200 output config
