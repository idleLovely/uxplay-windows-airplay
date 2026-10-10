# UxPlay for Windows — AirPlay Receiver

<div align="center">

**A free, open-source replacement for LonelyScreen**

[![License: GPL-3.0](https://img.shields.io/badge/License-GPL--3.0-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![Windows](https://img.shields.io/badge/Windows-10%20%7C%2011-0078D4?logo=windows)](https://www.microsoft.com/windows/)
[![AirPlay 2](https://img.shields.io/badge/AirPlay-2-supported-000000?logo=apple)](https://www.apple.com/airplay/)

Mirror your iPhone, iPad, or Mac screen and audio to Windows over Wi-Fi.
No cables, no dongles, no $20 subscription.

</div>

---

## English

### What is this?

[UxPlay](https://github.com/FDH2/UxPlay) is an open-source **AirPlay 2** receiver (GPL-3.0), packaged for Windows by [leapbtw/uxplay-windows](https://github.com/leapbtw/uxplay-windows). It turns your PC into an Apple TV.

**It can:**
- Mirror your iPhone / iPad / Mac screen in real time
- Stream audio including Apple Music in lossless ALAC
- Stream video from YouTube over HLS
- Display photos

**It has:** no ads, no account, no subscription, no telemetry, no limits.

### Requirements

| Requirement | Details |
|---|---|
| Windows | Windows 10 (1809+) or Windows 11, x64 |
| **Bonjour** | **Required** — ships with [iTunes](https://www.apple.com/itunes/), or install [Bonjour for Windows](https://bonjour.apple.com/download/) standalone |
| Network | iPhone and PC on the **same Wi-Fi** |

### Quick start

1. Unzip the folder anywhere (e.g. `C:\UxPlay`)
2. Double-click **`uxplay-windows.exe`**
3. A tray icon appears in the bottom-right corner
4. On your iPhone: **Control Center** then **Screen Mirroring**
5. Tap your computer's name

> **First time only:** Windows Firewall will ask. Click **Allow access** for both Private and Public networks.

### Command-line options

```bash
uxplay-windows.exe -n MyPC -nh
```

| Option | What it does |
|---|---|
| `-n NAME` | Name shown on your iPhone |
| `-nh` | Don't append `@hostname` to the name |
| `-fs` | Fullscreen |
| `-h265` | Enable HEVC / 4K streaming |
| `-pin` | Require a 4-digit PIN to connect |
| `-s wxh[@r]` | Request a resolution (default `1920x1080@60`) |
| `-al x` | Audio latency in seconds (default `0.25`) |

Persistent settings live in one file, one option per line:

```
%APPDATA%\leapbtw\uxplay-windows\arguments.txt
```

### Troubleshooting

**Not showing up in the AirPlay menu?**

**1 - Bonjour service not running** (the most common cause):

```powershell
Get-Service 'Bonjour Service'
```

If it says `Stopped`, run PowerShell **as Administrator**:

```powershell
Start-Service 'Bonjour Service'
```

**2 - Firewall blocking it:**

Open **Windows Defender Firewall**, then *Allow an app to communicate through Windows Defender Firewall* — tick `uxplay-windows.exe` for both **Private** and **Public**.

**3 - Network profile:**

Your active network must be **Private**, not Public:

```powershell
Set-NetConnectionProfile -InterfaceAlias "Wi-Fi" -NetworkCategory Private
```

**4 - Clean restart:**

```powershell
taskkill /F /IM uxplay-windows.exe
uxplay-windows.exe
```

### Known limits

- **DRM content will not work** — Netflix, YouTube Premium and Apple TV+ use FairPlay Streaming, which is out of scope for this project.
- **Fullscreen** needs `-fs` and works with D3D11 / D3D12.
- **Default quality** is 1920x1080@60. Use `-h265` for 4K.

---

## Download

**[Download the latest ZIP](https://github.com/idleLovely/uxplay-windows-airplay/releases/latest)**

Unzip it, double-click `uxplay-windows.exe`, done.
