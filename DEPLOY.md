# ORBIS TOUR bot — GitHub'ga push va Railway'ga deploy

Kod tayyor. `.env`, `package.json`, `locales.js`, `index.js` — hammasi ORBIS TOUR uchun sozlangan.
Quyidagilarni **o'z kompyuteringizda** bajaring (bu yerdan GitHub/Railway'ga ulanib bo'lmadi).

## 1. GitHub'da repo yaratish
1. https://github.com/new ochilsin
2. Repository name: **orbis-tour**
3. Private (yoki Public) tanlang
4. README, .gitignore, license — **hech narsa qo'shmang** (bo'sh qoldiring)
5. "Create repository" bosing

## 2. Kodni push qilish
Terminal (PowerShell yoki Git Bash) oching va quyidagilarni ketma-ket kiriting:

```
cd "C:\Users\Lenovo\Documents\orbis bot"

# eski yarim-yaratilgan .git ni o'chirib, toza boshlaymiz:
rmdir /s /q .git        REM PowerShell'da: Remove-Item -Recurse -Force .git

git init
git add .
git commit -m "ORBIS TOUR bot - Riva botidan nusxa"
git branch -M main
git remote add origin https://github.com/Dimonbek/orbis-tour.git
git push -u origin main
```

> `.env` fayl `.gitignore`da — bot tokeni GitHub'ga chiqmaydi (to'g'ri va xavfsiz).

## 3. Railway'ga deploy
1. https://railway.app → **New Project** → **Deploy from GitHub repo**
2. **Dimonbek/orbis-tour** ni tanlang (kerak bo'lsa GitHub'ni ulang)
3. Deploy boshlanadi. Keyin **Variables** bo'limiga o'ting va qo'shing:

   | Nom | Qiymat |
   |-----|--------|
   | BOT_TOKEN | 8835181378:AAE1lhUV-Qk877i9nT3N4Ymg_hBGw4ADS8g |
   | GROUP_ID | -1004490190415 |
   | SUPER_ADMIN_ID | 6220576519 |
   | ADMIN_IDS | 6220576519 |

4. **Settings → Networking → Generate Domain** bosing.
   Bu `RAILWAY_PUBLIC_DOMAIN` ni yaratadi va bot avtomatik **webhook rejimida** ishga tushadi.
5. (Ixtiyoriy, tavsiya etiladi) **Volume** qo'shing, mount path: `/app/data`
   — shunda baza (mijoz so'rovlari) restartdan keyin saqlanadi.
6. Deploy tugagach, **Logs**da `✅ WEBHOOK rejimida ishga tushdi` chiqishi kerak.

## 4. Tekshirish
- Botga Telegram'da `/start` yozing → "ORBIS TOUR botiga xush kelibsiz" chiqadi.
- `/admin` → admin panel (siz super adminsiz: 6220576519).
- Guruhga bot admin qilinganini tekshiring — so'rovlar `-1004490190415` guruhiga tushadi.

## Muhim eslatma
Bot **guruhga (-1004490190415) admin** qilingan bo'lishi shart, aks holda so'rovlar yuborilmaydi.
Admin panelda `⚙️ Sozlamalar → 🧪 Guruhni test` orqali tekshirsangiz bo'ladi.
