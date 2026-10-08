# 24 GHz FMCW Radar ve Sinyal İşleme Sistemi

Bu proje, hareketli ve sabit hedefleri algılamak, mesafe değişimlerini ölçmek ve sinyal analizi yapmak amacıyla tasarlanmış 24 GHz FMCW radar sistemidir. 

<!-- ÖNERİ: Buraya PCB'nin veya osiloskop ekranının bir fotoğrafını sürükleyip bırakabilirsiniz -->

## 🛠 Donanım Özellikleri
* **Radar Modülü:** 24 GHz ISM bandında çalışan ve çift kanallı (I/Q) IF çıkışı veren RFbeam K-LC5 alıcı-verici.
* **Kontrolcü:** Veri işleme ve modülasyon kontrolü için STM32F407G-DISC1.
* **Analog Ön Uç (AFE):** Radar I/Q çıkışlarını koşullandırmak için TLV9062 op-amplar ile tasarlanan, 5 Hz - 5 kHz bant genişliğine ve 40 dB kazanca sahip aktif filtre devresi.
* **Baskı Devre (PCB):** 5V Type-C besleme girişli, sistem bileşenlerini bir araya getiren 2 katmanlı özel tasarım kart.

## 💻 Yazılım Mimarisi
* FMCW frekans taraması için mikrodenetleyicinin DAC çıkışından radar VCO girişine doğrusal testere dişi sinyal üretimi.
* İşlemci yükünü (CPU) minimuma indiren, tamamen donanım zamanlayıcısı (TIM2, TIM6) ve DMA tabanlı veri yolu tasarımı.
* I ve Q kanallarının ADC üzerinden kanal başı 12.5 kSps hızında örneklenmesi.
* Kesintisiz veri akışı için "Ping-Pong" (çift tampon) yöntemi ve toplanan verilerin USART3 üzerinden anlık olarak bilgisayara aktarılması.
* Donanım kesmesi (EXTI) kullanılarak fiziksel bir buton üzerinden sweep periyotlarının dinamik olarak değiştirilmesi.

## 📊 Test ve Doğrulama
* Filtre karakteristikleri sinyal jeneratörü ve osiloskop ölçümleri ile doğrulanmıştır.
* Sistem Sürekli Dalga (CW) modunda test edilmiş olup, hareketli hedeflerden dönen sinyallerdeki Doppler kaymaları frekans spektrumunda net bir şekilde gözlemlenmiştir.

---
**Not:** Projeye ait orcad donanım tasarım dosyaları, STM32 kaynak kodları ve test dokümanları ilgili klasörlerde yer almaktadır.
