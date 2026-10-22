<div align="center">

# 🎭 Nazende Gişesi

**Eski bir semt tiyatrosunun bilet gişesi üzerine kurulu, web tabanlı bir CTF görevi**

[🌐 Canlı Önizleme](https://nazende-gisesi.vercel.app/)

</div>

---

## 📖 Hikâye

Kadife koltukları ve dar fuayesiyle eski bir semt tiyatrosu… Belediye bilet satışını internete taşımaya karar vermiş, iş de aceleyle bir stajyere kalmış. Afişte bu haftanın oyunları, vitrinde öğrencilere bir indirim duruyor.

Gişe açık, perde kalkmak üzere. Gerisi sana kalmış.

## 🎯 Görev

| | |
|---|---|
| **Kategori** | Web |
| **Flag formatı** | `TUGA{...}` |
| **Flag sayısı** | 2 |

> ⚠️ Bu ortam **eğitim amacıyla kasıtlı olarak zafiyetlidir.** Yalnızca kendi makinende ya da yetkili bir CTF ortamında çalıştır.

## ✨ Sayfalar

| Sayfa | Açıklama |
|---|---|
| 🏠 Ana sayfa | Haftanın oyunları ve afişler |
| 🎟️ Seans | Seçilen oyunun seans bilgileri ve salon planı |
| 💺 Koltuk | Salon planındaki her koltuğun boş/dolu durumu |
| 🧾 Biletlerim | Kullanıcının biletleri |

## 🛠️ Teknolojiler

| Katman | Teknoloji |
|---|---|
| Backend | Python 3.12, Flask 3.1 |
| Veritabanı | SQLite |
| Sunucu | Gunicorn 23 |
| Arayüz | Jinja2 şablonları, CSS, SVG afişler |
| Yayın | Docker / Vercel (`@vercel/python`) |

## 🚀 Kurulum

### Docker ile (önerilen)

```bash
docker compose up --build
```

Tarayıcıda aç: http://localhost:8080

Durdurmak için:

```bash
docker compose down
```

### Docker olmadan

```bash
pip install -r requirements.txt
gunicorn -b 0.0.0.0:8080 app:app
```

Veritabanı (`nazende.db`) ilk çalıştırmada otomatik oluşturulur.

## 🔐 Ortam Değişkenleri

| Değişken | Açıklama |
|---|---|
| `SECRET_KEY` | Flask oturum anahtarı. Tanımlanmazsa her açılışta rastgele üretilir. |
| `VERCEL` | Vercel ortamında otomatik tanımlıdır; veritabanı `/tmp/nazende.db` altında tutulur. |

## ☁️ Vercel

`vercel.json` tüm istekleri `api/index.py` üzerinden Flask uygulamasına yönlendirir. Proje GitHub'a bağlı olmadığı için değişiklikler otomatik yayınlanmaz, yayın elle yapılır. `SECRET_KEY` Vercel'de ortam değişkeni olarak tanımlanmalıdır.

Vercel'de `/tmp` geçici olduğu için veritabanı gerektiğinde yeniden oluşturulur.

## 📁 Proje Yapısı

```
nazende-gisesi/
├── app.py              # Flask uygulaması ve veritabanı kurulumu
├── api/
│   └── index.py        # Vercel giriş noktası
├── templates/          # Jinja2 şablonları
├── static/             # CSS ve SVG afişler
├── public/static/      # Vercel için statik dosyalar
├── Dockerfile
├── docker-compose.yml
├── requirements.txt
└── vercel.json
```
