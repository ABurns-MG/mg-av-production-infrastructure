# Network Controller Access – Agent Reference

> **⚠️ This file does NOT contain credentials.**  
> Credentials are stored encrypted at `~/.ssh/mgavl-unifi-credentials.enc.json`

---

## Access Method

| Parameter | Value |
|-----------|-------|
| **Protocol** | SSH (key-based authentication) |
| **Host** | 216.189.150.162 |
| **User** | mgavl-agent |
| **Key File** | `~/.ssh/mgavl-agent-unifi` (Ed25519) |
| **Key Fingerprint** | SHA256:p2nE3TRLcdMOUVDwUDsFfA8YR+dewXP0bLid4V9hKa0 |

## Connecting

```powershell
ssh -i "$env:USERPROFILE\.ssh\mgavl-agent-unifi" mgavl-agent@216.189.150.162
```

## Server Details

| Property | Value |
|----------|-------|
| **OS** | CentOS 7 |
| **Hostname** | wireless.altehost.com |
| **Docker Containers** | alte_controller (UniFi), alte_mongo (MongoDB 3.6), alte_logs |
| **UniFi Image** | jacobalberty/unifi:latest |
| **Controller Port** | 8443 (HTTPS), 8080 (inform) |

## Querying Data

The UniFi controller stores all data in MongoDB. Query via:

```powershell
$script = 'db.device.find({site_id:"628583ca19b9c40034b30ebb"}).forEach(function(d){printjson(d)})'
$scriptB64 = [Convert]::ToBase64String([Text.Encoding]::UTF8.GetBytes($script))
ssh -i "$env:USERPROFILE\.ssh\mgavl-agent-unifi" mgavl-agent@216.189.150.162 "echo $scriptB64 | base64 -d | docker exec -i alte_mongo mongo --quiet unifi"
```

## MercyGate Site ID

```
628583ca19b9c40034b30ebb
```

## Key Collections

| Collection | Contents |
|-----------|----------|
| `device` | Adopted network devices (switches, APs, gateway) |
| `networkconf` | VLAN/network definitions |
| `portconf` | Port profiles |
| `wlanconf` | WiFi SSID configurations |
| `site` | Site definitions |

## Encrypted Credential Store

| Property | Value |
|----------|-------|
| **Location** | `~/.ssh/mgavl-unifi-credentials.enc.json` |
| **Encryption** | AES-256-CBC |
| **Key Derivation** | SHA256 of passphrase |
| **Contents** | Host, user, key path, purpose, created date |

To decrypt (PowerShell):
```powershell
$json = Get-Content "$env:USERPROFILE\.ssh\mgavl-unifi-credentials.enc.json" | ConvertFrom-Json
$aes = [System.Security.Cryptography.Aes]::Create()
$aes.Key = [System.Security.Cryptography.SHA256]::Create().ComputeHash(
	[Text.Encoding]::UTF8.GetBytes("MercyGateAVL-UniFi-Agent-2026"))
$aes.IV = [Convert]::FromBase64String($json.iv)
$dec = $aes.CreateDecryptor()
$plainBytes = $dec.TransformFinalBlock([Convert]::FromBase64String($json.data), 0,
	[Convert]::FromBase64String($json.data).Length)
[Text.Encoding]::UTF8.GetString($plainBytes) | ConvertFrom-Json
```
