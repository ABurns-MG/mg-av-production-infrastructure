# Main Sanctuary – Audio Latency

## Broadcast Audio Chain (DM7 → Ableton → DM7 → SE-3200)

This is the primary measured audio path for livestream output.

### Component Breakdown

| Segment | Device/Path | Latency (ms) | Method | Date |
|---------|-------------|-------------|--------|------|
| 1 | Dante send (DM7 → Broadcast PC) | 4 | Dante network specs | 2025-01-15 |
| 2 | Ableton overall latency (I/O + buffers) | 10.7 | Ableton status bar | 2025-01-15 |
| 3 | Ableton plugin chain | 181 | Ableton track delay display | 2025-01-15 |
| 4 | Dante return (Broadcast PC → DM7) | 4 | Dante network specs | 2025-01-15 |
| 5 | DM7 internal processing | ~1 | Yamaha specs | 2025-01-15 |
| **Total** | **Full broadcast audio chain** | **≈200 ms** | **Calculated sum** | **2025-01-15** |

### Important Note on Ableton Latency Reporting

Ableton's "Overall Latency" (10.7 ms) already includes I/O and safety buffers. The plugin delay (181 ms) is **in addition** to this value. Do not double-count I/O latency.

### Latency Diagram

```
DM7 Broadcast Bus → [4 ms] → Dante Network → [10.7 ms] → Ableton I/O
    → [181 ms] → Plugin Chain → [4 ms] → Dante Return → [~1 ms] → DM7
    ─────────────────────────────────────────────────────────────────────
    Total: ≈200 ms
```

## Test Conditions

- Sample Rate: 48 kHz
- Buffer Size: (as reported by Ableton overall latency)
- Plugin Chain: Lookahead limiters, linear-phase EQ (total 181 ms reported delay)
- Dante Latency Setting: Default (4 ms per hop)

## FOH Audio Chain

| Device/Path | Latency (ms) | Method | Date |
|-------------|-------------|--------|------|
| (To be measured) | | | |

## Other Paths

(Add additional audio paths as they are measured)

| Path Name | Total Latency (ms) | Method | Date |
|-----------|-------------------|--------|------|
| | | | |

## Key Insight

The Ableton plugin chain (181 ms) is the dominant latency contributor in the broadcast audio path. This creates an "audio slower than video" condition at the SE-3200, requiring only 46 ms of audio delay compensation on the switcher (not the full pipeline difference).

## Notes

- Any change to the Ableton plugin chain will shift total audio latency
- Removing a heavy plugin makes audio arrive earlier (may require increasing SE-3200 delay)
- Adding lookahead processing makes audio arrive later (may require decreasing SE-3200 delay)
- Always re-measure after plugin changes — see [Broadcast Sync](../broadcast/sync.md)
