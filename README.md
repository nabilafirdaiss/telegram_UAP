# 📱 Telegram Message Spam Classifier

Proyek ini adalah sistem deteksi pesan spam  menggunakan tiga model : **LSTM**, **Universal Sentence Encoder (USE)**, dan **IndoBERT**. Dashboard interaktif dibangun menggunakan **Gradio** untuk memudahkan pengguna melakukan pengujian model secara langsung.

---

## 📄 Deskripsi Proyek
Proyek ini bertujuan untuk mengatasi gangguan pesan spam pada grup atau chat pribadi Telegram. Dengan membandingkan tiga arsitektur model yang berbeda, proyek ini memberikan analisis mendalam tentang model mana yang paling efektif dalam menangkap pola bahasa spam dalam bahasa Indonesia.

## 🧪 Dataset dan Preprocessing
Dataset terdiri dari pesan teks yang diberi label `0` (Non-Spam) dan `1` (Spam).
Tahapan preprocessing meliputi:
* **Case Folding**: Mengubah semua teks menjadi huruf kecil.
* **Cleaning**: Menghapus angka, tanda baca, dan karakter khusus.
* **Filtering**: Menghapus *stopwords* (kata umum) bahasa Indonesia menggunakan library NLTK.
* **Stemming**: Mengubah kata ke bentuk dasarnya menggunakan Porter Stemmer.

## 🤖 Model yang Digunakan
1.  **LSTM (Long Short-Term Memory)**: Model RNN yang dirancang untuk mempelajari ketergantungan jangka panjang dalam teks.
2.  **Universal Sentence Encoder (USE)**: Model embedding tingkat kalimat yang kuat untuk menangkap makna semantik.
3.  **IndoBERT**: Model berbasis Transformer yang telah dilatih khusus pada korpus besar bahasa Indonesia (SOTA).

---

## 📊 Hasil Evaluasi dan Analisis Perbandingan

Berdasarkan pengujian pada data uji (973 sampel), berikut adalah ringkasan performanya:

| Model | Accuracy | F1-Score (Macro) | Keterangan |
| :--- | :---: | :---: | :--- |
| **IndoBERT** | **97.53%** | **0.9706** | **Terbaik**. Sangat presisi mendeteksi spam. |
| **USE** | **91.00%** | **0.8900** | Sangat baik dan stabil untuk penggunaan umum. |
| **LSTM** | **70.00%** | **0.4200** | Cukup cepat, namun memiliki bias tinggi ke Non-Spam. |

### Analisis Singkat:
* **IndoBERT** menjadi pemenang utama dengan kemampuan memahami konteks bahasa Indonesia yang sangat akurat.
* **LSTM** mengalami kendala *Recall* yang rendah pada kelas Spam (hanya 1%), sehingga kurang direkomendasikan untuk sistem keamanan real-time tanpa penyeimbangan data lebih lanjut.

---

## 🚀 Panduan Menjalankan Secara Lokal

### 1. Prasyarat
Pastikan Anda sudah menginstal Python 3.10+ dan library yang diperlukan:
```bash
pip install tensorflow transformers gradio nltk pandas numpy scikit-learn
