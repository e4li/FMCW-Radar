# 24 GHz FMCW Radar ve Sinyal İşleme Sistemi

Bu proje, hareketli ve sabit hedefleri algılamak, mesafe değişimlerini ölçmek ve sinyal analizi yapmak amacıyla tasarlanmış 24 GHz FMCW radar sistemidir[cite: 6]. 

<!-- ÖNERİ: Buraya PCB'nin veya osiloskop ekranının bir fotoğrafını sürükleyip bırakabilirsiniz -->

## 🛠 Donanım Özellikleri
* **Radar Modülü:** 24 GHz ISM bandında çalışan ve çift kanallı (I/Q) IF çıkışı veren RFbeam K-LC5 alıcı-verici[cite: 6, 10].
* **Kontrolcü:** Veri işleme ve modülasyon kontrolü için STM32F407G-DISC1[cite: 6, 10].
* **Analog Ön Uç (AFE):** Radar I/Q çıkışlarını koşullandırmak için TLV9062 op-amplar ile tasarlanan, 5 Hz - 5 kHz bant genişliğine ve 40 dB kazanca sahip aktif filtre devresi[cite: 10, 16, 18].
* **Baskı Devre (PCB):** 5V Type-C besleme girişli, sistem bileşenlerini bir araya getiren 2 katmanlı özel tasarım kart[cite: 7].

## 💻 Yazılım Mimarisi
* FMCW frekans taraması için mikrodenetleyicinin DAC çıkışından radar VCO girişine doğrusal testere dişi sinyal üretimi[cite: 10, 11].
* İşlemci yükünü (CPU) minimuma indiren, tamamen donanım zamanlayıcısı (TIM2, TIM6) ve DMA tabanlı veri yolu tasarımı[cite: 10].
* I ve Q kanallarının ADC üzerinden kanal başı 12.5 kSps hızında örneklenmesi[cite: 12].
* Kesintisiz veri akışı için "Ping-Pong" (çift tampon) yöntemi ve toplanan verilerin USART3 üzerinden anlık olarak bilgisayara aktarılması[cite: 12, 13].
* Donanım kesmesi (EXTI) kullanılarak fiziksel bir buton üzerinden sweep periyotlarının dinamik olarak değiştirilmesi[cite: 11, 13].

## 📊 Test ve Doğrulama
* Filtre karakteristikleri sinyal jeneratörü ve osiloskop ölçümleri ile doğrulanmıştır[cite: 14, 16, 18].
* Sistem Sürekli Dalga (CW) modunda test edilmiş olup, hareketli hedeflerden dönen sinyallerdeki Doppler kaymaları frekans spektrumunda net bir şekilde gözlemlenmiştir[cite: 17, 18].

---
**Not:** Projeye ait Altium donanım tasarım dosyaları, STM32 kaynak kodları ve test dokümanları ilgili klasörlerde yer almaktadır.
