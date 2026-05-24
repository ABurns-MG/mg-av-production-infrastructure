# Latency Measurement Standards

## Purpose

All latency values in this repository must be based on real-world measurements, not manufacturer estimates.

## Measurement Methods

### Audio Latency

1. Generate a click/impulse at the source
2. Record both source and output simultaneously
3. Measure sample offset in DAW
4. Convert to milliseconds

### Video Latency

1. Display a high-resolution timer on source
2. Capture output with camera pointed at display
3. Compare frame timestamps
4. Account for camera shutter delay

### Audio-to-Video Sync (VLC Method)

1. Play a test file with known sync through the full chain
2. Record the output screen + speakers with a phone/camera
3. Analyze in editor for lip-sync offset
4. Document the measured offset

## Documentation Format

Always record:

- **Device**: What was measured
- **Method**: How it was measured
- **Result**: Value in milliseconds
- **Date**: When the measurement was taken
- **Conditions**: Any relevant context (plugin chain, sample rate, etc.)

## Example

```
Device: Datavideo SE-3200
Method: VLC timer capture
Result: 46 ms video delay
Date: 2024-01-15
Conditions: 1080p60, SDI input, PGM output
```

## Re-measurement Triggers

Re-measure latency whenever:

- Plugin chain changes
- Sample rate changes
- Hardware is swapped
- Firmware is updated
- Routing is modified
