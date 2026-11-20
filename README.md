# İhale AI: Şartname Analizi ve Ürün Öneri Sistemi

Kamu ihalelerinin teknik şartnamelerini okuyup geçmiş ihalelerden öğrenerek, yeni bir şartnamede **hangi kaleme hangi ürünle girilmesi gerektiğini öneren** sistem. Tamamen yerelde (on-premise) çalışır ve hiçbir harici yapay zekâ servisi kullanmaz.

> Bu depo bir proje vitrinidir. Kaynak kod paylaşılmamaktadır.

## Problem

Her ihalede onlarca kalem ve her kalem için ayrı teknik maddeler yayınlanıyor. Belgeler PDF, Word, taranmış PDF veya görsel olabiliyor. Uzmanlar hangi ürünün hangi maddeye uyduğunu her seferinde baştan değerlendiriyordu.

## Akış

```
Şartname (PDF / DOCX / taranmış)
   → Metin çıkarma + OCR
   → Kalem ve teknik madde ayrıştırma
   → Embedding (yerel model) → vektör araması (Qdrant)
   → Geçmiş benzer maddeler + o maddelerde kullanılan ürünler + sonuçlar
   → Kalem bazında ürün önerisi, uygunluk skoru ve gerekçe
```

## Özellikler

- Geçmiş verilerden öğrenme: girilen ürün, kazanma durumu, uzman notları ("uyar ama riskli", "şu madde nedeniyle elenir")
- Açıklanabilir öneriler: önerinin dayandığı geçmiş maddeler gösterilir
- Çok kullanıcılı web arayüzü, belge yükleme ve ilerleme takibi
- Verinin şirket dışına çıkmadığı tam yerel mimari

## Teknolojiler

`Python` · `FastAPI` · `SQLAlchemy` · `PostgreSQL` · `Qdrant` · `sentence-transformers` · `Tesseract OCR` · `pdfplumber` · `python-docx` · `Next.js` · `TypeScript` · `Docker`
