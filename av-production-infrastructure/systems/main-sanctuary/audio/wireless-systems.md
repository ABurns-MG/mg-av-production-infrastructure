# Main Sanctuary – Wireless Systems (Shure)

> **Source:** WWB7 Show File (`MG-WWB7.shw`) + Inventory Report  
> **WWB Version:** 7.5.0.181  
> **Export Date:** 2026-05-24  
> **WWB Computer IP:** 10.0.250.226

---

## Receiver Inventory

| Device ID | Model | Band | Network IP | Dante IP | MAC | Serial |
|-----------|-------|------|-----------|----------|-----|--------|
| **Q2** | ULXD4Q | G57 | 10.0.250.59 | 192.168.10.11 | 00:0E:DD:AB:E5:D5 | 4251480578 |
| **Q1** | ULXD4Q | G57 | 10.0.250.60 | 192.168.10.117 | 00:0E:DD:AB:E6:65 | 4251480650 |
| **S1** | QLXD4 | G50 | 10.0.250.174 | n/a | 00:0E:DD:A5:1E:3B | 4231600751 |
| **S2** | QLXD4 | G50 | 10.0.250.137 | n/a | 00:0E:DD:4E:21:A9 | 4202381259 |
| **Pstr Bay** | — | — | 10.0.250.173* | n/a | 00:0E:DD:AC:A2:F2 | — |

> **Note:** Q2's Dante MAC is `00:0E:DD:EA:9F:D2` (matches Dante name `ULXD4Q-ea9fd2`).  
> Q1's Dante MAC is `00:0E:DD:EA:CB:78` (matches Dante name `ULXD4Q-eacb78`).

### IP Address Corrections from WWB7

The WWB7 export reveals different IPs than what UniFi reported:

| Device | UniFi Reported | WWB7 Reported | Dante IP (WWB7) |
|--------|---------------|---------------|-----------------|
| ULXD4Q [Q2] | 192.168.10.59 (Dante only) | 10.0.250.59 (Mgmt) | 192.168.10.11 |
| ULXD4Q [Q1] | — | 10.0.250.60 (Mgmt) | 192.168.10.117 |
| QLXD4 [S1] | 10.0.250.174 | 10.0.250.174 | n/a (no Dante) |
| QLXD4 [S2] | — | 10.0.250.137 | n/a (no Dante) |

---

## Wireless Microphone Channels

### ULXD4Q [Q2] — Dante: `ULXD4Q-ea9fd2` (192.168.10.11)

| Ch | Name | Frequency (MHz) | Dante → DM7 RX | Role |
|----|------|-----------------|-----------------|------|
| 1 | FL1 | 508.475 | RX 53 | Front Line 1 |
| 2 | HDST-2 | 607.650 | RX 54 | Headset 2 |
| 3 | FL3 | 525.300 | RX 55 | Front Line 3 |
| 4 | FL4 | 527.900 | RX 56 | Front Line 4 |

### ULXD4Q [Q1] — Dante: `ULXD4Q-eacb78` (192.168.10.117)

| Ch | Name | Frequency (MHz) | Dante → DM7 RX | Role |
|----|------|-----------------|-----------------|------|
| 1 | FL5 | 566.950 | RX 57 | Front Line 5 |
| 2 | FL6 | 560.950 | RX 58 | Front Line 6 |
| 3 | FL7 | 566.575 | RX 59 | Front Line 7 |
| 4 | HDST-1 | 475.775 | RX 60 | Headset 1 (Pastor) |

### QLXD4 [S1] — Analog (no Dante) | IP: 10.0.250.174

| Ch | Name | Frequency (MHz) | Connection | Role |
|----|------|-----------------|------------|------|
| 1 | FL2 | 533.150 | Analog → DM7 Omni In | Front Line 2 |

### QLXD4 [S2] — Analog (no Dante) | IP: 10.0.250.137

| Ch | Name | Frequency (MHz) | Connection | Role |
|----|------|-----------------|------------|------|
| 1 | LV1 | 529.000 | Analog → DM7 Omni In | Lavalier 1 |

---

## IEM Transmitters (Shure PSM900 – Band G6)

All PSM900 units are RF transmitters for in-ear monitors. Audio feed comes from KLANG via AVIO-DAO2 adapters (Dante), converted to analog, then fed to PSM900 inputs.

> **AVIO Adapter IPs:** All AVIO-DAO2 adapters are on VLAN 130 (192.168.10.0/24) with DHCP-assigned addresses. No static IPs are configured. Dante device names (e.g., `IEM6-FL2`) are the authoritative identifiers.

| IEM Unit | Musician | Frequency (MHz) | KLANG TX Ch | AVIO Adapter |
|----------|----------|-----------------|-------------|--------------|
| IEM 11 | FL1 | 492.550 | 21-22 | IEM11-FL1 |
| IEM 6 | FL2 | 487.225 | 11-12 | IEM6-FL2 |
| IEM 14 | FL3 | 491.225 | 27-28 | IEM14-FL3 |
| IEM 16 | FL4 | 496.200 | 31-32 | IEM16-FL4 |
| IEM 1 | FL5 | 476.225 | 9-10 | IEM1-FL5 |
| IEM 7 | KEYS | 499.125 | 13-14 | IEM7-KEYS |
| IEM 3 | EG1 | 496.800 | 5-6 | IEM3-EG1 |
| IEM 4 | EG2 | 472.475 | 7-8 | IEM4-EG2 |
| IEM 2 | BASS | 471.425 | 3-4 | IEM2-BASS |
| IEM 8 | ACOUS | 471.025 | 15-16 | IEM8-ACOUS |
| IEM 13 | FL6 | 474.550 | 17-18 | IEM13-FL6 |
| IEM 5 | FL7 | 486.675 | 19-20 | IEM5-FL7 |

---

## RF Frequency Bands

| Band | Range | Used By |
|------|-------|---------|
| G50 | 470–534 MHz | QLXD4 receivers (S1, S2) |
| G57 | 470–608 MHz | ULXD4Q receivers (Q1, Q2) |
| G6 | 470–514 MHz | PSM900 IEM transmitters |

---

## Related Documents

- [Dante Routing](dante-routing.md) — ULXD4Q Dante subscriptions
- [DM7 Channel Map](dm7-channel-map.md) — Console channel assignments
- [AVL Clients](../../../configs/network/avl-clients.md) — Network inventory
