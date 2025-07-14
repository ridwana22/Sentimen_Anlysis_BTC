# Analisis Sentimen Pasar Bitcoin: Studi Kasus Respons terhadap Konflik Geopolitik Iran-Israel
Proyek ini menyajikan sebuah analisis komprehensif mengenai sentimen pasar Bitcoin (BTC) di platform media sosial Twitter (X), dengan fokus pada diskursus berbahasa Indonesia selama periode konflik Iran-Israel. Memanfaatkan teknik *Natural Language Processing* (NLP), penelitian ini bertujuan untuk mengkuantifikasi dan mengklasifikasikan sentimen publik ke dalam tiga kategori: **positif, negatif, dan netral**.

Secara metodologis, proyek ini mengimplementasikan model *state-of-the-art* **BERT** (`mdhugol/indonesia-bert-sentiment-classification`) untuk menghasilkan anotasi sentimen yang akurat, yang kemudian berfungsi sebagai *ground truth*. Selanjutnya, dilakukan evaluasi komparatif terhadap tiga algoritma *machine learning* klasik—**Naive Bayes, Logistic Regression, dan Random Forest**—untuk mengukur efektivitas mereka dalam tugas klasifikasi sentimen pada domain spesifik ini.

## Metodologi Penelitian
Alur kerja proyek dirancang secara sistematis untuk memastikan integritas dan reprodusibilitas hasil:
1.  **Akuisisi Data**:
      * Kumpulan data tweet dalam bahasa Indonesia diperoleh melalui *crawling* dari Twitter menggunakan *query* pencarian `(BTC OR Bitcoin) AND ("konflik Iran Israel" OR
      * "perang Iran Israel")`.
      * Dataset final yang digunakan untuk analisis ini terdiri dari **1410 tweet**, yang tersimpan dalam file `Iran_Israel_BTC.csv`.

2.  **Pra-pemrosesan dan Normalisasi Teks**:
      * Dilakukan serangkaian prosedur pembersihan data untuk menghilangkan *noise*, termasuk eliminasi URL, *mention* pengguna (`@username`), dan simbol tagar (`#`).
      * Teks kemudian dinormalisasi melalui konversi ke huruf kecil (*lowercase*) dan penghapusan *stopwords* bahasa Indonesia untuk meningkatkan kualitas fitur teks.

3.  **Anotasi Sentimen Berbasis Transformer**:
      * Model **BERT** yang telah dilatih khusus untuk sentimen bahasa Indonesia diaplikasikan untuk memberikan label `Positif`, `Negatif`, atau `Netral` pada setiap tweet.
      * Hasil anotasi ini menjadi tolok ukur (*benchmark*) untuk melatih dan mengevaluasi model-model berikutnya.

4.  **Pelatihan dan Evaluasi Komparatif Model Klasik**:
      * Dataset yang telah teranotasi dibagi menjadi set pelatihan dan pengujian.
      * Tiga model klasifikasi dilatih menggunakan representasi **TF-IDF** dari teks: Naive Bayes, Logistic Regression, dan Random Forest.
      * Kinerja setiap model dievaluasi secara kuantitatif menggunakan metrik standar industri: **Akurasi, Presisi, Recall, dan F1-Score**.

## Hasil dan Pembahasan
Analisis menghasilkan beberapa temuan kunci yang signifikan:
  * **Dominasi Sentimen Netral**: Distribusi sentimen menunjukkan bahwa mayoritas diskursus bersifat **Netral**. Hal ini dapat mengindikasikan bahwa sebagian besar audiens membahas topik ini dari sudut pandang informatif atau observatif, bukan dari perspektif finansial yang spekulatif secara langsung.
  * **Kinerja Model Unggul**: Dalam evaluasi komparatif, model **Logistic Regression** menunjukkan performa paling superior dengan mencapai **akurasi sekitar 83.0%**. Hasil ini menandakan efektivitasnya dalam membedakan nuansa sentimen dalam konteks yang kompleks ini, bahkan dibandingkan dengan model ansambel seperti Random Forest.
  * **Wawasan Kontekstual**: Visualisasi *Word Cloud* mengkonfirmasi relevansi korpus data, dengan kata-kata seperti "bitcoin", "iran", "israel", "konflik", dan "perang" menjadi yang paling dominan.

## Replikasi dan Penggunaan
Untuk mereplikasi hasil analisis ini, ikuti langkah-langkah berikut:
1.  **Kloning Repositori**:
    ```bash
    git clone [URL_REPOSITORI_ANDA]
    cd [NAMA_DIREKTORI]
    ```
2.  **Instalasi Dependensi**: Pastikan semua *library* Python yang tercantum dalam *notebook* telah terpasang di lingkungan Anda.
    ```bash
    pip install -r requirements.txt
    ```
    *(Disarankan untuk membuat file `requirements.txt` untuk kemudahan instalasi)*
3.  **Struktur Direktori**: Pastikan file dataset `Iran_Israel_BTC.csv` berada di direktori yang sama dengan *notebook* `SA_BTC.ipynb`.
4.  **Eksekusi**: Jalankan setiap sel kode di dalam *notebook* secara berurutan untuk mereproduksi alur kerja analisis.
