# 🇮🇩 Agent Analisis Sentimen Ulasan Berbahasa Indonesia (IndoBERT)

Repository ini berisi implementasi **Agent NLP berbasis Transformers** untuk mengklasifikasikan sentimen teks atau ulasan berbahasa Indonesia secara otomatis ke dalam 3 kategori: **Positive**, **Neutral**, dan **Negative**[cite: 3]. Projek ini dikembangkan untuk memenuhi tugas mata kuliah Natural Language Processing (NLP).

---

## 📌 Ringkasan Projek
- **Task NLP:** Sentiment Analysis (Klasifikasi Teks 3 Kelas)[cite: 3].
- **Pre-trained Model:** [`mdhugol/indonesia-bert-sentiment-classification`](https://huggingface.co/mdhugol/indonesia-bert-sentiment-classification) (Hasil *fine-tuning* dari IndoBERT `indobenchmark/indobert-base-p1`)[cite: 3].
- **Dataset:** [IndoNLU - SmSA](https://github.com/IndoNLP/indonlu/tree/master/dataset/smsa_doc-sentiment-prosa) (Purwarianti & Crisdayanti, 2019) dengan total 11.000 data *train* dan 1.260 data *valid*.
- **Performa Model:** Memperoleh tingkat **akurasi sebesar 93.67%** pada pengujian data validasi[cite: 5, 6].

---

## 🏗️ Alur Kerja Agent & Tokenisasi
1. **Input:** Agent menerima masukan teks ulasan atau komentar berbahasa Indonesia[cite: 3].
2. **Tokenization (WordPiece):** Teks dipetakan dan dipecah ke dalam bentuk *subwords* menggunakan algoritma tokenisasi WordPiece khas BERT (misalnya kata berimbuhan atau kata tidak baku akan dipecah secara otomatis menggunakan awalan `##`)[cite: 3, 4].
3. **Transformer Encoding:** Token yang telah dikonversi menjadi *Token IDs* diproses melintasi lapisan *Encoder* BERT untuk mengekstraksi representasi makna kontekstual teks.
4. **Classification Head & Output:** Lapisan klasifikasi akhir menerjemahkan vektor tersembunyi menjadi probabilitas kelas sentimen (`positive`, `neutral`, atau `negative`) beserta skor keyakinannya (*confidence score*).

---

## 📊 Hasil Evaluasi Performa
Berdasarkan evaluasi model pada 300 sampel data validasi SmSA[cite: 5]:
- **Akurasi Total:** `93.67%`[cite: 5, 6]
- **Classification Report:**
  | Kelas Label | Precision | Recall | F1-Score | Support |
  | :--- | :---: | :---: | :---: | :---: |
  | **Negative** | 0.93 | 0.94 | 0.93 | 96 |
  | **Neutral** | 0.88 | 0.82 | 0.85 | 34 |
  | **Positive** | 0.95 | 0.96 | 0.96 | 170 |

- **Confusion Matrix:**
  $$\begin{bmatrix} 90 & 2 & 4 \\ 2 & 28 & 4 \\ 5 & 2 & 163 \end{bmatrix}$$
*(Urutan kelas: Negative, Neutral, Positive)*[cite: 6]

---

## 📁 Struktur Repository
```text
📦 Agent-NLP-Sentimen
 ┣ 📜 README.md          # Dokumentasi lengkap projek
 ┣ 📜 notebook.ipynb     # Jupyter Notebook / Google Colab berisi kode & eksperimen
 ┗ 📜 requirements.txt   # Daftar library Python yang dibutuhkan
