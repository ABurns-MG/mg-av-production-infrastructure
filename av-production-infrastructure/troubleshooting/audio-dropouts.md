# Troubleshooting – Audio Dropouts

## Symptoms

- Intermittent audio cuts or glitches
- Dante channel dropping momentarily
- Crackling or stuttering in output

## Common Causes

1. **Network issues** – Switch overload, bad cable, VLAN misconfiguration
2. **Clock sync lost** – Dante clock master changed or lost
3. **Buffer underrun** – DAW buffer too small for current load
4. **CPU overload** – Too many plugins or processing

## Diagnostic Steps

1. Check Dante Controller for clock errors
2. Check network switch for packet loss
3. Monitor CPU usage on processing machines
4. Check buffer settings in DAW

## Solutions

- Verify Dante clock master is stable
- Check and replace suspect network cables
- Increase buffer size if CPU allows
- Reduce plugin count if CPU is overloaded
- Ensure network switches are configured for real-time audio (QoS)

## Related Documents

- [Audio Routing](../systems/main-sanctuary/audio/routing.md)
- [Console Settings](../systems/main-sanctuary/audio/console-settings.md)
