# Troubleshooting – Video Delay

## Symptoms

- Video noticeably behind audio
- IMAG screens show delay vs. live action
- Stream viewers report lip-sync issues

## Common Causes

1. **Switcher processing** – All video switchers add frame-based delay
2. **Scaler processing** – Resolution conversion adds latency
3. **Display processing** – Consumer displays add significant delay
4. **Encoder latency** – Software/hardware encoding adds delay

## Diagnostic Steps

1. Measure video delay at each stage of the pipeline
2. Compare against documented baseline
3. Identify which component is adding unexpected delay
4. Check if any new devices were added to the chain

## Solutions

- Enable "game mode" or low-latency mode on displays
- Minimize scalers in the signal path
- Use hardware encoders over software where possible
- Add compensating audio delay to match video pipeline
- Document all new measured values

## Known Values

| Device | Measured Delay | Date |
|--------|---------------|------|
| SE-3200 | 46 ms | |

## Related Documents

- [Switcher Settings](../systems/main-sanctuary/video/switcher-settings.md)
- [IMAG Delay Alignment](../systems/main-sanctuary/imag/delay-alignment.md)
- [Broadcast Sync](../systems/main-sanctuary/broadcast/sync.md)
