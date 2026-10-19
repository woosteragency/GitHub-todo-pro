# نشر OpenSEO على سيرفر هوستنجر (VPS)

ملفات هذا المجلد جاهزة — تنفّذها أنت عبر SSH على سيرفرك (ما أقدر أوصل سيرفرك من هنا بدون بيانات دخوله، وهذا أسلم لك).

## 0) تأكد أولاً

افتح **hPanel** → تأكد أن خطتك **"VPS Hosting"** (لا "Web/Shared Hosting"). بدون VPS لن يعمل Docker ولا شيء من هذا.

## 1) اتصل بالسيرفر

```bash
ssh root@YOUR_SERVER_IP
```

## 2) ثبّت Docker (إن لم يكن مثبّتاً)

```bash
curl -fsSL https://get.docker.com | sh
```

## 3) انقل هذا المجلد للسيرفر

من جهازك (أو استنسخ المستودع كامل على السيرفر مباشرة):

```bash
git clone https://github.com/woosteragency/GitHub-todo-pro.git
cd GitHub-todo-pro/openseo-selfhost
```

## 4) اضبط المفاتيح

```bash
cp .env.example .env
nano .env
```

ضع `DATAFORSEO_API_KEY` (راجع `docs/DATAFORSEO_API_KEY.md` في مستودع OpenSEO نفسه — تحتاج حساب DataForSEO وشحن $50 كحد أدنى).

## 5) شغّله

```bash
docker compose up -d
docker compose logs -f   # تابع حتى يجهز (أول مرة تاخذ 1-2 دقيقة)
```

## 6) الوصول الآمن (هذه الخطوة لا تتجاوزها)

⚠️ النسخة الذاتية هنا **بدون تسجيل دخول** (`AUTH_MODE=local_noauth`). لا تفتح المنفذ 3001 على الإنترنت مباشرة.

**الطريقة الأسهل والأأمن لاستخدامك الشخصي — SSH tunnel:**

على جهازك (لا على السيرفر):

```bash
ssh -L 3001:localhost:3001 root@YOUR_SERVER_IP
```

ثم افتح `http://localhost:3001` من متصفحك — يبقى يعمل طول ما الـ tunnel مفتوح.

**إذا تحتاج وصول دائم من أي مكان** (فريق، أو ربط MCP من كلود مباشرة بدون tunnel): ضع nginx أمامه مع HTTPS + basic auth أو IP allowlist. قل لي إذا تحتاج هذا وأجهزه لك.

## 7) ربطه بكلود (بعد ما يصير متاحاً على دومين/IP ثابت مع حماية)

في `claude.ai → Settings → Connectors → Add custom connector`:

```
https://YOUR_DOMAIN_OR_TUNNEL/mcp
```

## الصيانة

```bash
docker compose pull && docker compose up -d   # تحديث
docker compose down                           # إيقاف
docker compose logs -f                        # مراقبة الأخطاء
```
