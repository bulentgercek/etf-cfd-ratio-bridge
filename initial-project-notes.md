Proje: ETF–CFD Ratio & Companion Price Indicator (TradingView / Pine Script)
🎯 Hedef (Başlangıç Niyeti)

Bu projenin amacı, ETF ile CFD/spot enstrümanlar arasındaki fiyat ilişkisini tek bakışta görünür kılmaktı. Özellikle:

SPY ↔ US500

GLD ↔ XAUUSD

SLV ↔ XAGUSD

çiftleri için;

Anlık fiyat ratio’larını (ETF / CFD) hesaplamak

Her iki enstrümanın son aktif fiyatlarını birlikte göstermek

Trader’ın hangi grafikte olduğuna bağlı olarak, karşılık gelen enstrümanın fiyatını da görsel olarak sunmak

Bunu yaparken:

Chart ölçeğini bozmamak

Ek çizgi / clutter yaratmamak

“Mental conversion” ihtiyacını ortadan kaldırmak

Temel motivasyon:

“XAUUSD 2410 iken, bu GLD’de neye denk geliyor?”
“US500 6900 iken, SPY kaç eder?”

🧠 Tasarlanan Mimari

request.security() ile her sembolün son fiyatı çekiliyor

Ratio = ETF_price / CFD_price

Sağ üst köşede table:

Ratio

“ETF – CFD” fiyat çiftleri

Chart’a göre dinamik davranış:

US500 chart → SPY karşılığı

XAU chart → GLD karşılığı

vb.

🚧 Karşılaşılan Temel Teknik Engel

TradingView / Pine Script platformunun bilinçli kısıtları:

Scale price chart only açıkken

Indicator plot’ları price scale’e dahil edilmiyor

İkinci bir “price column” veya scale label üretmek mümkün değil

plot() ile:

Dinamik başlık (title) verilemiyor

Aynı scale’de farklı büyüklükte fiyatlar (690 vs 6900) etiketsiz kalabiliyor

Sonuç:

“Gerçek price scale üzerinde ikinci fiyat” platform tarafından engelleniyor

Bu noktada scale ile “savaşmak” yerine sağlam workaround tercih edildi.

✅ Ulaşılan Çözüm (Gerçekçi & Stabil)

Scale’den vazgeçilerek:

Table çözümü → tamamen stabil, doğru, hızlı

Companion price = label çözümü:

Chart’ın son bar’ında

Sağda veya solda

Fiyat tag’i gibi

Scale’i bozmadan

Her zaman görünür

Yani:

“Price-scale kolon değil ama price-tag hissi veren, trader dostu bir görsel çözüm.”

Bu yaklaşım:

TradingView limitleriyle uyumlu

Profesyonel kullanımda sürdürülebilir

Görsel karmaşa yaratmıyor

📌 Projenin Şu Anki Durumu

✅ Ratio hesaplama çalışıyor

✅ Multi-symbol table çalışıyor

✅ Broker bağımsız sembol eşleşme çözüldü

✅ Scale bozmayan companion price gösterimi tasarlandı

❌ TradingView’da gerçek “ikinci price scale kolonu” imkânsız (bilinçli kısıt)

🔑 Özet Cümle

Bu proje, ETF–CFD fiyat dönüşümünü zihinsel hesap olmadan yapmayı hedefledi; TradingView’ın scale kısıtları nedeniyle, bu hedef table + price-tag label kombinasyonu ile en temiz ve sürdürülebilir şekilde hayata geçirildi.