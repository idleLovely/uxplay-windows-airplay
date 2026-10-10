# UxPlay for Windows

<div align="center">

**بديل مجاني ومفتوح المصدر لـ LonelyScreen**

Mirrors your iPhone screen to Windows — بدون أسلاك، بدون محوّلات، بدون اشتراك.

</div>

---

## العربية

### وش هذا؟

[UxPlay](https://github.com/FDH2/UxPlay) هو مستقبل **AirPlay 2** مفتوح المصدر برخصة GPL-3.0، جهّزه للويندوز فريق [leapbtw/uxplay-windows](https://github.com/leapbtw/uxplay-windows). يحوّل جهازك إلى Apple TV.

**يقدر يسوي:**
- يعكس شاشة الآيفون أو الآيباد أو الماك لحظة بلحظة
- يبث الصوت، بما فيه Apple Music، بصيغة ALAC بدون ضغط
- يبث فيديو من يوتيوب عبر HLS
- يعرض الصور

**وما فيه:** إعلانات، حساب، اشتراك، تتبع، ولا حدود.

### المتطلبات

| المتطلب | التفاصيل |
|---|---|
| ويندوز | Windows 10 (1809+) أو Windows 11, x64 |
| **Bonjour** | **مطلوب** — يجي مع [iTunes](https://www.apple.com/itunes/) أو نزّل [Bonjour for Windows](https://bonjour.apple.com/download/) لحاله |
| الشبكة | آيفونك والـ PC على **نفس** الواي فاي |

### تشغيل سريع

1. فك الضغط عن المجلد في أي مكان، مثل `C:\UxPlay`
2. دبل كليك على **`uxplay-windows.exe`**
3. بتظهر أيقونة في شريط النظام، أسفل يمين الشاشة
4. على آيفونك: **Control Center** ثم **Screen Mirroring**
5. اضغط على اسم جهازك

> **أول مرة بس:** ويندوز بيسألك عن الجدار الناري. اضغط **Allow access** لكل من Private و Public.

### خيارات سطر الأوامر

```bash
uxplay-windows.exe -n MyPC -nh
```

| الخيار | الوظيفة |
|---|---|
| `-n NAME` | الاسم اللي يظهر على آيفونك |
| `-nh` | ما يضيف `@hostname` للاسم |
| `-fs` | شاشة كاملة |
| `-h265` | يفعّل HEVC و 4K |
| `-pin` | يطلب رمز PIN من أربعة أرقام |
| `-s wxh[@r]` | يحدد دقة معيّنة، افتراضي `1920x1080@60` |
| `-al x` | تأخير الصوت بالثواني، افتراضي `0.25` |

الإعدادات الدائمة في ملف واحد، خيار واحد في كل سطر:

```
%APPDATA%\leapbtw\uxplay-windows\arguments.txt
```

### حل المشاكل

**ما يطلع في قائمة AirPlay؟**

**1 - خدمة Bonjour متوقفة**، وهي السبب الأكثر شيوعا:

```powershell
Get-Service 'Bonjour Service'
```

لو النتيجة `Stopped`، افتح PowerShell **كمشرف** ثم:

```powershell
Start-Service 'Bonjour Service'
```

**2 - الجدار الناري يحجب الاتصال:**

افتح **Windows Defender Firewall** ثم *Allow an app to communicate*، وتأكد `uxplay-windows.exe` مفعّل لكل من **Private** و **Public**.

**3 - نوع الشبكة:**

شبكتك النشطة لازم تكون **Private** مو Public:

```powershell
Set-NetConnectionProfile -InterfaceAlias "Wi-Fi" -NetworkCategory Private
```

**4 - إعادة تشغيل نظيفة:**

```powershell
taskkill /F /IM uxplay-windows.exe
uxplay-windows.exe
```

### حدود معروفة

- **محتوى DRM ما يشتغل** — Netflix و YouTube Premium و Apple TV+ يستخدمون FairPlay Streaming، وهذا خارج نطاق المشروع.
- **شاشة كاملة** تحتاج `-fs` وتعمل مع D3D11 و D3D12.
- **الجودة الافتراضية** 1920x1080@60. للـ 4K استخدم `-h265`.

---

## التحميل

**[نزّل آخر نسخة ZIP](https://github.com/idleLovely/uxplay-windows-airplay/releases/latest)**

فك الضغط، دبل كليك على `uxplay-windows.exe`، وخلصت.

---

## [| English README](README_EN.md)**

---

## الرخصة

هذا البرنامج حر ومفتوح المصدر، تحت رخصة **GNU General Public License v3.0**.

<!--
SPDX-License-Identifier: GPL-3.0-or-later
-->
