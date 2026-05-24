# AV Production Infrastructure

This repository contains version-controlled documentation of all audio, video, lighting, and broadcast systems across MercyGate facilities.

## Purpose

To provide a single source of truth for:

- Signal flow and routing
- Latency and sync alignment
- Device configurations
- Troubleshooting procedures

This ensures consistency across systems and enables rapid debugging and training.

---

## Systems Covered

- Main Sanctuary
- Kids Ministry
- Youth
- Event Center
- Future expansions

Each system includes documentation for:

- Audio
- Video
- IMAG
- Broadcast audio
- Lighting

---

## Structure Overview

- `systems/` – Detailed documentation per room/system
- `standards/` – Organization-wide technical standards
- `configs/` – Device configuration files
- `diagrams/` – Visual signal flow diagrams
- `troubleshooting/` – Known issues and solutions

---

## Key Principles

### 1. Version Control Everything

All changes to routing, latency, or configuration should be committed.

### 2. Measure, Don't Assume

Latency and sync values should always be based on real-world testing.

### 3. Document Signal Flow Clearly

If someone cannot trace a signal in under 2 minutes, the documentation is incomplete.

### 4. Keep It Practical

Documentation should help someone fix a problem during a live service.

---

## Example Use Cases

- Fixing audio/video sync issues
- Rebuilding a system after failure
- Training new technicians
- Auditing latency across rooms
- Planning upgrades

---

## Tools Used

- Yamaha DM7
- Dante / Dante Virtual Soundcard
- Ableton Live
- Datavideo SE‑3200
- Various lighting systems

---

## Contribution Guidelines

- Use consistent naming conventions
- Update both `.md` and `.html` versions when possible
- Include diagrams for complex routing
- Document *why*, not just *what*

---

## Notes

This repository is intended for internal technical use. Accuracy and clarity are critical.
