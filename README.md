# TG2 Study — Android APK (TWA)

Wrapper Android (Trusted Web Activity) untuk situs belajar
[tg2.heyworld.fun](https://tg2.heyworld.fun) — ujian 特定技能2号
飲食料品製造業. APK di-build otomatis lewat GitHub Actions
menggunakan [Bubblewrap](https://github.com/GoogleChromeLabs/bubblewrap).

## Cara dapat APK

1. Push ke `main` (atau buka tab **Actions** → **Build APK** → **Run workflow**)
2. Tunggu ~3-5 menit
3. Di halaman run, scroll ke bawah → **Artifacts** → download `tg2-study-apk`
4. Isinya: `app-release-signed.apk` — tinggal install di Android
   (aktifkan "Install dari sumber tidak dikenal" kalau ditanya)

## Secret yang dibutuhkan (set sekali di repo)

**Settings → Secrets and variables → Actions → New repository secret**

| Name | Isi |
|---|---|
| `KEYSTORE_BASE64` | isi file `keystore.b64` (base64 keystore signing) |
| `KEYSTORE_PASSWORD` | password keystore |

> Nilai kedua secret ada di file yang dikirim terpisah (jangan di-commit!).

## Update versi app

Edit `appVersionName` / `appVersionCode` di `twa-manifest.json`, push.
Konten app selalu ambil langsung dari situs live — update materi/soal/kamus
**tidak perlu** rebuild APK.

## Catatan teknis

- Package: `fun.heyworld.tg2`
- minSdk 23 (Android 6.0+)
- Digital Asset Links sudah aktif di situs
  (`/.well-known/assetlinks.json`) → app jalan fullscreen tanpa URL bar
- Offline: sama seperti PWA (setelah kunjungan pertama)
