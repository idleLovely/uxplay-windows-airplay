# UxPlay for Windows — AirPlay Receiver

**بديل مجاني ومفتوح المصدر لـ LonelyScreen** — استقبل شاشة وصوت آيفونك على ويندوز عبر Wi-Fi بدون أي اشتراك.

---

## وش هذا؟

[UxPlay](https://github.com/FDH2/UxPlay) هو سيرفر AirPlay 2 مفتوح المصدر (GPL-3.0)، يشتغل على ويندوز. يقدر يسوي:

- 📱 **mirror شاشة** الآيفون / الآيباد / الماك
- 🔊 **بث صوت** (بما فيه Apple Music) بصيغة ALAC lossless
- 🎬 **بث فيديو** من يوتيوب (HLS)
- 🖼️ **عرض الصور**

**بدون:** إعلانات، حساب، اشتراك، تتبع، أو حدود.

---

## المتطلبات

| المتطلب | التفاصيل |
|---------|----------|
| ويندوز | Windows 10 (1809+) أو Windows 11, x64 |
| **Bonjour** | **مطلوب** — يجي مع iTunes أو [Bonjour for Windows](https://bonjour.apple.com/download/) |
| الشبكة | آيفونك والـ PC على نفس الـ WiFi |

> **ما عندك Bonjour؟** نزّل iTunes (مجاني) — يجي معاه Bonjour تلقائي.

---

## طريقة التشغيل

1. افتح مجلد `UxPlay`
2. دبل كليك على **`uxplay-windows.exe`**
3. بيظهر أيقونة في الـ tray (أسفل يمين الشاشة)
4. على آيفونك: **Control Center** ثم **Screen Mirroring**
5. اختار اسم الكمبيوتر من القائمة

### من سطر الأوامر

```bash
uxplay-windows.exe -n MyPC -nh
```

### أهم الخيارات

| الخيار | الوظيفة |
|--------|---------|
| `-n NAME` | اسم البث اللي يظهر على آيفونك |
| `-nh` | لا تضيف `@hostname` للاسم |
| `-fs` | شاشة كاملة |
| `-h265` | دعم 4K (HEVC) |
| `-pin` | فعّل رمز PIN من 4 أرقام |

**ملف الإعدادات:**
`%APPDATA%\leapbtw\uxplay-windows\arguments.txt` — سطر واحد لكل خيار.

---

## حلول المشاكل

**البرنامج ما طلع في قائمة AirPlay — تأكد من الثلاث:**

**1) خدمة Bonjour مشغّلة؟**

```powershell
Get-Service 'Bonjour Service'
```

لو النتيجة `Stopped` شغّلها كـ Administrator:

```powershell
Start-Service 'Bonjour Service'
```

**2) الفايروول يحجب الاتصال؟**

Windows Defender Firewall ثم Allow an app — تأكد `uxplay-windows.exe` مفعّل for TCP و UDP.

**3) الشبكة صح؟**

- الـ PC و آيفونك على **نفس** الـ WiFi
- الـ network profile خلّه **Private** مو Public

**إعادة تشغيل نظيفة:**

```powershell
taskkill /F /IM uxplay-windows.exe
uxplay-windows.exe
```

---

## حدود معروفة

- **محتوى DRM ما يشتغل:** Netflix و YouTube Premium و Apple TV+ يستخدمون FairPlay Streaming — خارج نطاق المشروع.
- **شاشة كاملة** تحتاج `-fs` (يشتغل مع D3D11 / D3D12).
- **الجودة الافتراضية** 1920x1080@60. للـ 4K استخدم `-h265`.

---

## الرخصة والمصادر

| المشروع | الرابط | الرخصة |
|---------|--------|--------|
| UxPlay (المحرك) | https://github.com/FDH2/UxPlay | GPL-3.0 |
| uxplay-windows (التغليف) | https://github.com/leapbtw/uxplay-windows | GPL-3.0 |

الملفات الثنائية في هذا الريبو (GStreamer، FFmpeg، Qt6) مبنية مسبقاً من مشاريع مفتوحة المصدر، وكلها متوافقة مع GPL/LGPL.

> **تنبيه:** أصول Apple مثل Bonjour غير موزّعة هنا — نزّلها بنفسك من Apple أو iTunes.

---

## الإصدارات الأصلية

هذي نسخة مجهّزة للويندوز. للإصدارات الرسمية última تحديث:

https://github.com/leapbtw/uxplay-windows/releases
