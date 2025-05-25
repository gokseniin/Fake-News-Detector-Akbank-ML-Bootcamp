# 📰 Fake News Detector – Akbank ML Bootcamp Final Project

Bu proje, **Akbank & Global AI Hub Makine Öğrenmesi Bootcamp** kapsamında gerçekleştirilmiştir.  
Amaç, sahte ve gerçek haberleri makine öğrenmesi kullanarak sınıflandırabilen bir model geliştirmektir.

---

## 📁 Kullanılan Veri Seti

- Kaynak: [Kaggle – Real and Fake News Dataset](https://www.kaggle.com/datasets/razanaqvi14/real-and-fake-news)
- Toplam veri: 44.000+ haber
- Sütunlar: `title`, `text`, `subject`, `date`
- Etiket: `label` → 0 = Gerçek haber, 1 = Sahte haber

---

## 🔍 Veri Analizi (EDA)

- Etiket dağılımı (fake/real) dengeli.
- `subject` sütunu ile etiket arasında birebir ilişki bulundu. → **veri sızıntısı tespit edildi**
- 10 karakterden kısa, içeriksiz metinler çıkarıldı.
- `date`, `text_length` gibi modellemede etkisiz sütunlar silindi.

---

## 🧹 Veri Ön İşleme

- `text` ve `title` sütunlarına **TF-IDF** uygulanmıştır.
- `text`: max_features = 5000
- `title`: max_features = 1000
- `subject` sütunu modelden çıkarılmıştır (etiketle doğrudan ilişkili olduğu için)
- Veriler eğitim (%80) ve test (%20) olarak ayrılmıştır.

---

## 🤖 Kullanılan Modeller ve Karşılaştırma

Üç farklı model test edilmiştir:

| Model               | Accuracy | F1 Score |
|---------------------|----------|----------|
| Logistic Regression | 99.25%   | 99.26%   |
| Naive Bayes         | 94.86%   | 94.97%   |
| **Support Vector Machine (SVM)** | **99.54%** | **99.54%** |

---

## ✅ Seçilen Nihai Model: Support Vector Machine (SVM)

- En yüksek başarıyı sağlamıştır.
- Metin verisi ile çalışmada SVM oldukça etkilidir.
- Eğitim ve test başarıları arasında anlamlı fark **yoktur** → **overfitting gözlemlenmemiştir**.

---

## ⚠️ Veri Sızıntısı Tespiti

EDA sırasında `subject` sütununun, etiketle doğrudan ilişkili olduğu fark edilmiştir:  
Örneğin bazı `subject` değerleri yalnızca sahte haberler içerirken, bazıları sadece gerçek haberlerden oluşmaktadır.

Bu durum modelin etiketi ezberlemesine neden olduğu için, `subject` sütunu çıkarılmıştır.

---

## 📈 Değerlendirme Metrikleri

Model performansı aşağıdaki metriklerle değerlendirilmiştir:

- **Accuracy:** Modelin genel doğru tahmin oranı.
- **Precision:** Fake seçilen haberlerin gerçekten fake olma oranı.
- **Recall:** Gerçekten fake olan haberlerin ne kadarını tespit ettiği.
- **F1 Score:** Precision ve Recall arasındaki denge.

---

## 📌 Gerçek Hayatta Kullanım Senaryoları

- Sosyal medya platformlarında sahte haber tespiti.
- Haber sitelerinde içerik doğrulama sistemleri.
- Arama motorlarında güvenilirlik filtreleme.

---

## 💡 Geliştirme Önerileri

- Gelişmiş dil modelleri (örneğin **BERT**) ile bağlamsal kelime ilişkileri daha iyi yakalanarak modelin doğruluğu artırılabilir.
- **Gözetimsiz öğrenme** algoritmaları ile haberlerin konu bazlı otomatik gruplandırılması yapılabilir.
- **Streamlit** veya benzeri bir araçla, kullanıcıların kendi haber metinlerini test edebileceği interaktif bir web arayüzü geliştirilebilir.

---

## 🔗 Proje Linki

- 📄 [Kaggle Notebook](https://www.kaggle.com/code/gokseniin/fake-news-detector-akbank-ml-bootcamp)

---

## 👨‍💻 Geliştirici

**Göksenin İrem Baş**  
Akbank & Global AI Hub  
Makine Öğrenmesi Bootcamp – Mayıs 2025
