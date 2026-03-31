# 🎙️ Ses İşareti Analizi ve Cinsiyet Sınıflandırma

![Python Version](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Streamlit](https://img.shields.io/badge/UI-Streamlit-FF4B4B.svg?logo=streamlit&logoColor=white)
![Librosa](https://img.shields.io/badge/Audio-Librosa-orange.svg)
![Rule Based](https://img.shields.io/badge/Algorithm-Rule_Based-success.svg)

> [cite_start]Zaman düzlemi sinyal analiz yöntemleri kullanılarak `.wav` uzantılı ses kayıtlarından öznitelik çıkarımı yapan ve **Kural Tabanlı (Rule-Based)** bir algoritma ile cinsiyet tahmini (Erkek, Kadın, Çocuk) gerçekleştiren interaktif web uygulaması. [cite: 3, 9]

[cite_start]Uygulama arayüzü **Streamlit** kullanılarak geliştirilmiştir.  [cite_start]Makine öğrenmesi modeli (Machine Learning) *kullanılmamış*, sınıflandırma işlemi tamamen **sinyal işleme teorilerine** ve literatürdeki temel frekans ($F_0$) eşik değerlerine dayandırılmıştır. 

---

## ✨ Özellikler

* **📊 Zaman Düzlemi Analizi:** Kısa Süreli Enerji (STE) ve Sıfır Geçiş Oranı (ZCR) kullanılarak sinyaldeki sesli (voiced) ve sessiz (unvoiced) bölge ayrımı. [cite: 23, 57]
* **🌊 Otokorelasyon ile $F_0$ Tespiti:** Sesli pencerelerde otokorelasyon fonksiyonu kullanılarak Temel Frekans (Pitch - $F_0$) hesaplaması. [cite: 27, 30]
* **▶️ Canlı Demo Modülü:** Arayüzden yüklenen tekil bir `.wav` dosyasını anında analiz etme; [cite_start]$F_0$ değerini hesaplama, FFT Spektrumu ve Otokorelasyon grafiklerini görselleştirme. [cite: 34, 44, 67]
* **📈 Toplu Veri Seti Analizi:** Excel meta verilerini okuyarak tüm ses dosyalarını toplu işleme, sistem başarı oranını (Accuracy) hesaplama ve **Karışıklık Matrisi (Confusion Matrix)** çıkarma. [cite: 11, 44, 60]
* **⚠️ Hata Takip Sistemi:** Okunamayan, bozuk veya sinyal kalitesi yetersiz olan dosyaları otomatik tespit edip arayüzde raporlama. 

---

## 📂 Proje Klasör Yapısı

Projenin sorunsuz çalışması için klasör hiyerarşisinin aşağıdaki gibi olması beklenmektedir: [cite: 15]

```text
├── Dataset/                  # Ana veri seti klasörü
│   ├── Grup_01/
│   │   ├── Grup_01_MetaVeri.xlsx
│   │   ├── G01_D01_E_21_Mutlu.wav
│   │   └── ...
│   └── Grup_17/
│       ├── Grup_17_MetaVeri.xlsx
│       ├── G17_D01_E_21_Notr_C1.wav
│       └── ...
├── app.py                    # Ana Streamlit uygulama kodu
└── README.md                 # Proje dokümantasyonu
