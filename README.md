# Patika

Tek dosya HTML olarak yazılmış rota ve aktivite takip uygulaması. Bisiklet, yürüyüş ve koşu için canlı GPS kaydı, kamp yeri işaretleme, yükseklik profili, GPX içe/dışa aktarma ve rozet sistemi içerir. Uzun vadeli hedef: Wikiloc benzeri bir topluluk rota keşif platformu.

## Özellikler (v1.0.0)

- **Canlı kayıt:** anlık hız, mesafe, tırmanış, hareket süresi
- **Otomatik duraklama:** ~2 km/s altında 6 sn hareketsizlikte, tekrar başlayınca otomatik devam
- **Elle duraklat/devam:** dur-kalk molalarında hız ortalamasını bozmaz
- **Harita katmanları:** Sokak (OSM), Uydu (Esri World Imagery), Topoğrafya (OpenTopoMap) — seçim hatırlanır
- **Yer işaretleme:** kamp, su, manzara, tehlike, not — yorum ve tür seçimi ile
  - Kayıt sırasında "İşaretle" butonu → mevcut konum
  - Haritaya uzun basınca → seçilen nokta
- **Rotalarım:** liste + detayda harita, istatistikler, yükseklik profili grafiği
- **GPX dışa aktarma:** işaretler waypoint olarak gömülür (Strava, Wikiloc, OsmAnd uyumlu)
- **GPX içe aktarma:** dışarıdan gelen rotayı işaretleriyle birlikte alır
- **İstatistik:** günlük (son 7 gün), haftalık (son 8 hafta), aylık (son 6 ay) toplam km, tırmanış, sürüş/yürüyüş süresi + çubuk grafik
- **10 rozet:** İlk Adım, Onluk, Yarım Yüz, 100 Kulübü, 500 Kulübü, Kampçı, Kartograf, Tırmanışçı, Şafakçı, Kararlı
- **Wake Lock:** kayıt sırasında ekranı açık tutar
- **Tüm veri IndexedDB'de yerel** — internet gerekmez

## Kurulum

1. `patika.html` dosyasını HTTPS destekli bir yere yükle (Firebase Hosting, GitHub Pages, Vercel).
2. Telefonda tarayıcıdan aç. Konum izni ver.
3. İlk açılışta ana ekrana ekle → PWA gibi çalışır.

**Not:** Tarayıcı Geolocation API'si HTTPS gerektirir. `file://` üzerinden açılırsa GPS çalışmaz.

## Yol Haritası

### v2 — Bulut ve paylaşım (Supabase)
- Kullanıcı girişi (e-posta / Google)
- Rota yayınlama (özel / herkese açık)
- **Canlı takip** — link ile başkasına konumunu paylaşma
- Bölgeye göre rota keşfi (PostGIS)
- Başlangıç/bitiş noktası bulanıklaştırma (gizlilik)

### v3 — Topluluk
- Rotalara yorum ve beğeni
- Kamu kamp yerleri ortak katmanı
- Bildirim / moderasyon
- Kullanıcı profilleri ve rozetlerin topluluğa açılması

### v4 — APK
- Capacitor ile Android paketi
- Arka plan GPS (background-geolocation eklentisi)
- Bildirim çubuğunda kayıt kontrolü
- Google Play sürümü

## Teknik yığın

- **Harita:** Leaflet 1.9.4
- **Depolama:** IndexedDB (native)
- **Yazı tipi:** Barlow + Barlow Condensed (Google Fonts)
- **Tarayıcı API'leri:** Geolocation, Wake Lock, File
- **Backend (v2+):** Supabase (Postgres + PostGIS + Realtime + Auth)
- **Paketleme (v4):** Capacitor

## Dosya yapısı

```
patika.html      # tüm uygulama (tek dosya)
README.md        # bu dosya
CHANGELOG.md     # sürüm notları
```

## Geliştirici

Kamil — Kayseri
GitHub: [kamilsaim](https://github.com/kamilsaim)
