# Troubleshooting – Sync Issues

## Symptoms

- Audio and video out of sync on stream
- IMAG appears delayed compared to live sound
- Lip-sync issues on broadcast output

## Common Causes

1. **Plugin chain latency changed** – Adding/removing plugins on the broadcast bus changes total audio delay
2. **Switcher processing delay** – SE-3200 adds ~46 ms of video latency
3. **Encoder buffering** – Streaming encoder adds variable delay
4. **Clock drift** – Mismatched clock sources cause gradual drift

## Diagnostic Steps

1. Measure current audio chain latency
2. Measure current video chain latency
3. Compare to documented baseline values
4. Identify which component changed

## Solutions

- Re-measure and update offset values
- Check clock source alignment
- Verify plugin chain matches documentation
- Apply corrective delay to the faster path

## Related Documents

- [Broadcast Sync](../systems/main-sanctuary/broadcast/sync.md)
- [Latency Measurement Standards](../standards/latency-measurement.md)
