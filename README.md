# Sentimen_Anlysis_BTC
Analisis Sentimen Bitcoin Terkait Konflik Iran-Israel di Twitter
Proyek ini bertujuan untuk menganalisis sentimen publik di Twitter (X) dalam bahasa Indonesia mengenai Bitcoin (BTC) sehubungan dengan konflik Iran-Israel. Analisis ini menggunakan pemrosesan bahasa alami (NLP) untuk mengklasifikasikan sentimen menjadi positif, negatif, atau netral.

Selain itu, proyek ini juga membandingkan performa tiga model machine learning klasik (Naive Bayes, Logistic Regression, dan Random Forest) dengan menggunakan hasil pelabelan dari model BERT sebagai ground truth.

📊 Alur Kerja Proyek
Proyek ini dibagi menjadi beberapa tahap utama:

1. Pengambilan Data (Crawling)
  Data tweet diambil dari Twitter menggunakan library tweet-harvest (kode disertakan tetapi dinonaktifkan/dikomentari).
  Keyword pencarian yang digunakan adalah (BTC OR Bitcoin) AND ("konflik Iran Israel" OR "perang Iran Israel") dalam bahasa Indonesia.
  Data yang digunakan dalam notebook ini telah disimpan dalam file Iran_Israel_BTC.csv dan berisi 1410 tweet.

2. Pra-pemrosesan Teks (Preprocessing)

  Teks tweet dibersihkan dari elemen-elemen yang tidak relevan seperti URL, mention (@username), dan simbol tagar (#).
  Teks juga diubah menjadi huruf kecil dan dilakukan penghapusan stopwords (kata-kata umum dalam bahasa Indonesia yang tidak memiliki makna sentimen signifikan).
  Pelabelan Sentimen dengan BERT
  Setiap tweet yang telah dibersihkan kemudian diberi label sentimen (positif, negatif, atau netral) menggunakan model BERT yang sudah dilatih untuk bahasa Indonesia           (mdhugol/indonesia-bert-sentiment-classification).
  Hasil pelabelan dari BERT ini dijadikan sebagai data dasar (ground truth) untuk melatih model-model klasik.
  Hasilnya menunjukkan bahwa sebagian besar sentimen bersifat Netral, diikuti oleh Negatif, dan terakhir Positif.
  
3. Pelatihan dan Evaluasi Model Klasik
  Data yang sudah berlabel dibagi menjadi data latih dan data uji.
  Tiga model machine learning klasik dilatih untuk memprediksi sentimen:
    - Naive Bayes
    - Logistic Regression    
    - Random Forest
  Setiap model dievaluasi performanya menggunakan metrik seperti akurasi, presisi, recall, dan F1-score.
  
4. 📈 Hasil Analisis
  Distribusi Sentimen: Mayoritas tweet yang dianalisis memiliki sentimen Netral.
  Perbandingan Model: Berdasarkan metrik evaluasi, Logistic Regression menunjukkan performa terbaik dengan akurasi ~83%, mengungguli Naive Bayes dan Random Forest.
  
  Visualisasi:
    - Word Cloud: Kata-kata yang paling sering muncul dalam tweet terkait adalah "bitcoin", "iran", "israel", "btc", "konflik", dan "perang".
    - Grafik Distribusi Sentimen: Menampilkan perbandingan jumlah tweet untuk setiap kategori sentimen.
    - Grafik Perbandingan Akurasi: Membandingkan tingkat akurasi dari ketiga model klasik yang dievaluasi.

🚀 Cara Menjalankan
1 .Pastikan semua library Python yang dibutuhkan telah terinstal. Anda dapat melihat daftar library yang diimpor di awal notebook.
2. Siapkan file data Iran_Israel_BTC.csv dalam direktori yang sama dengan notebook.
3. Jalankan sel-sel kode di dalam notebook SA_BTC.ipynb secara berurutan.
