# 🎙️ Ses İşareti Analizi ve Cinsiyet Sınıflandırma

![Python Version](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Streamlit](https://img.shields.io/badge/UI-Streamlit-FF4B4B.svg?logo=streamlit&logoColor=white)
![Librosa](https://img.shields.io/badge/Audio-Librosa-orange.svg)
![Rule Based](https://img.shields.io/badge/Algorithm-Rule_Based-success.svg)

> Zaman düzlemi analiz yöntemlerini kullanarak ses işaretlerinden öznitelik çıkaran ve **Kural Tabanlı (Rule-Based)** bir algoritma ile Cinsiyet Sınıflandırması (Erkek, Kadın, Çocuk) gerçekleştiren interaktif bir web uygulamasıdır.

Bu proje kapsamında; temel frekans ($F_0$), enerji ve ZCR özellikleri elde edilmiş, bu özelliklerin cinsiyet bazlı dağılımları incelenmiş ve makine öğrenmesi modeli kullanılmadan tamamen sinyal işleme teorilerine dayalı bir sınıflandırıcı geliştirilmiştir.

---

## ✨ Özellikler

* **📊 Zaman Düzlemi Analizi:** Kısa Süreli Enerji (STE) ve Sıfır Geçiş Oranı (ZCR) kullanılarak sinyaldeki sesli (voiced) ve sessiz (unvoiced) bölgelerin tespiti.
* **🌊 Otokorelasyon ile $F_0$ Tespiti:** Sesli pencerelerde Otokorelasyon fonksiyonu ($R_\tau$) kullanılarak sinyalin periyodik yapısının analizi ve Temel Frekans ($F_0$) hesaplaması.
* **▶️ Canlı Demo Modülü:** Arayüzden yüklenen tekil bir ses dosyasının sınıfını (E/K/Ç) tahmin etme; Otokorelasyon grafiğini ve FFT Spektrumunu yan yana görselleştirme.
* **📈 Toplu Veri Seti Analizi:** Tüm grup klasörlerindeki ses dosyalarını ve metadata Excel dosyalarını birleştirerek toplu işleme.
* **⚠️ Başarı Raporlama:** Tüm veri seti üzerindeki genel başarıyı (Accuracy) hesaplama ve Karışıklık Matrisi (Confusion Matrix) üzerinden hata analizi yapma.

---

## 📂 Proje Klasör Yapısı

Projenin sorunsuz çalışması için klasör hiyerarşisinin aşağıdaki "Dataset/" ana klasörü yapısına uygun olması gerekmektedir:

```text
├── Dataset/                  # Ana veri seti klasörü
│   ├── Grup_01/              # Her grubun kendi klasörü
│   │   ├── Grup_01.xlsx      # Metadata Excel dosyası
│   │   ├── sample1.wav       # .wav uzantılı ses dosyaları
│   │   └── ...
│   └── ...
├── app.py                    # Python tabanlı uygulama kodu
└── README.md                 # Proje dokümantasyonu
```

---

## ⚙️ Kurulum ve Gereksinimler

Projenin bağımlılıklarını izole bir ortamda kurmanız tavsiye edilir. Uygulama **Python** tabanlıdır.

**1. Depoyu Klonlayın:**
```bash
git clone [https://github.com/kullanici_adiniz/proje_adi.git](https://github.com/kullanici_adiniz/proje_adi.git)
cd proje_adi
```

**2. Gerekli Kütüphaneleri Yükleyin:**
Aşağıdaki temel kütüphanelerin yüklü olduğundan emin olun:
```bash
pip install streamlit librosa numpy pandas scipy matplotlib seaborn openpyxl
```

---

## 🧰 Kullanılan Temel Teknolojiler

| Kütüphane | Kullanım Amacı |
| :--- | :--- |
| **`streamlit`** | Web tabanlı kullanıcı arayüzü tasarımı. |
| **`librosa`** | Ses dosyalarının yüklenmesi ve işlenmesi. |
| **`numpy` & `scipy`** | Matematiksel hesaplamalar ve sinyal işleme operasyonları. |
| **`pandas`** | Excel verilerinin okunması ve yönetilmesi. |
| **`matplotlib`** | Otokorelasyon ve FFT grafiklerinin görselleştirilmesi. |

---

## 🚀 Uygulamayı Çalıştırma

Terminalde projenin bulunduğu ana dizindeyken aşağıdaki komutu çalıştırın:

```bash
streamlit run app.py
```

Komutu çalıştırdıktan sonra tarayıcınızda uygulama otomatik olarak açılacaktır. Arayüz üzerinden bir ses dosyası seçerek sınıflandırma yapabilir veya tüm veri seti üzerinde başarı analizi gerçekleştirebilirsiniz.

---

## 🧠 Algoritma ve Eşik Değerleri (Thresholds)

Sınıflandırma işlemi, Otokorelasyon yöntemiyle bulunan Ortalama $F_0$ değerlerine dayalı "Kural Tabanlı" bir algoritma ile yapılır. Sistem, hesaplanan değerleri şu aralıklara göre kategorize eder:

* 👨 **Erkek Sesi:** `85 Hz` - `175 Hz`
* 👩 **Kadın Sesi:** `175 Hz` - `280 Hz`
* 🧒 **Çocuk Sesi:** `> 280 Hz`
