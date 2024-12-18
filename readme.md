# Chatbot Multibahasa untuk DigiTeam

## Deskripsi
Proyek ini bertujuan untuk mengembangkan **chatbot multibahasa** untuk aplikasi **Mobile** dengan menggunakan model **Feed Forward Neural Network (FFNN)** dan **IndoBERT**. Chatbot ini mengintegrasikan **kamus multibahasa** untuk mendukung interaksi dalam **bahasa Indonesia, Sunda, dan Inggris**, memberikan respons yang cepat dan akurat. 

**Fitur Utama:**
- Integrasi kamus multibahasa yang memungkinkan chatbot untuk memahami dan merespons dalam tiga bahasa.
- Penggunaan model FFNN dan IndoBERT untuk meningkatkan pemahaman konteks kalimat.
- Implementasi dalam aplikasi DigiTeam untuk memberikan akses informasi secara real-time dan data respons yang dikeluarkan dinamis karena terhubung dengan backend aplikasi.

## Tujuan
Chatbot ini dirancang untuk:
- Membantu pengguna aplikasi DigiTeam mengakses informasi secara cepat dan akurat dalam lingkungan kerja multibahasa.
- Meningkatkan efisiensi operasional dengan memberikan respons yang relevan dan tepat waktu.

## Dataset
Dataset yang digunakan dalam proyek ini terdiri dari dua komponen utama:
1. **Dataset Intens**: Dataset ini mencakup contoh percakapan dalam berbagai konteks yang relevan dengan aplikasi DigiTeam, seperti logbook, profil pengguna, dan data kehadiran.
2. **Kamus Multibahasa**: Kamus ini berisi **309 kata** yang mencakup terjemahan dan sinonim dalam bahasa Indonesia, Sunda, dan Inggris. Kamus ini digunakan untuk meningkatkan pemahaman model terhadap variasi bahasa yang digunakan oleh pengguna.

Dataset ini digunakan untuk melatih model chatbot sehingga dapat mengidentifikasi berbagai macam pertanyaan dan memberikan respons yang sesuai dalam berbagai bahasa. Selain itu, dataset juga memastikan bahwa chatbot dapat menangani percakapan dalam konteks multibahasa tanpa kehilangan akurasi.

![Dataset Intens dan Kamus](dataset.png)  

## **DISCLAIMER**
<span style="color:red">Harap dicatat bahwa data yang terdapat dalam repository ini hanya merupakan **contoh** dan **bukan data asli**. Data ini digunakan semata-mata untuk tujuan demonstrasi dan pengembangan model chatbot multibahasa. Pengguna tidak disarankan untuk menggunakan data ini untuk tujuan lain selain pengembangan dan pembelajaran.</span>

<span style="color:red">Jika Anda berencana menggunakan data ini untuk proyek lain, harap pastikan untuk mengganti dataset dengan data yang relevan dan valid. Semua data yang ada di repositori ini tidak mewakili informasi atau data dari pengguna atau sistem yang sebenarnya.</span>




## Metodologi
Proyek ini mengikuti metodologi **CRISP-DM** (Cross-Industry Standard Process for Data Mining), yang terdiri dari tahapan berikut:
1. **Data Preparation**: Dataset dibersihkan dan diproses menggunakan teknik seperti *case folding*, *stop word removal*, *stemming*, dan tokenisasi.
2. **Modeling**: Model **FFNN** dikembangkan dengan representasi **IndoBERT**, kemudian ditingkatkan dengan integrasi kamus multibahasa.
3. **Deployment**: Chatbot diintegrasikan dengan aplikasi DigiTeam, memungkinkan pengguna untuk mengakses data secara real-time.

## Integrasi Kamus Multibahasa
Untuk mendukung kemampuan chatbot dalam menangani bahasa campuran, kami mengembangkan **kamus multibahasa** yang mencakup **309 kata** dalam bahasa Indonesia, Sunda, dan Inggris. Kamus ini diintegrasikan dengan model untuk:
- **Menerjemahkan pola pertanyaan** dalam bahasa Indonesia, Sunda, dan Inggris.
- **Meningkatkan pemahaman model terhadap variasi bahasa** yang digunakan dalam interaksi sehari-hari.

### Contoh Input dan Respons
Berikut adalah contoh perbandingan input asli dan terjemahan, bersama dengan probabilitas dan tag yang diprediksi oleh model:

| **No.** | **Input (Tanpa Kamus)**            | **Probabilitas (Tanpa Kamus)** | **Tag (Tanpa Kamus)** | **Terjemahan (Dengan Kamus)**             | **Probabilitas (Dengan Kamus)** | **Tag (Dengan Kamus)** |  
|---------|-------------------------------------|---------------------------------|------------------------|---------------------------------------|---------------------------------|-------------------------|  
| 1       | *How Carana Tingali List Logbook?*  | 0.4526                          | post_logbook            | *Gimana Cara Lihat Daftar Logbook?*   | 0.9965                          | get_logbook             |  
| 2       | *Saha Wae Nu Telat Poe Ieu ?*      | 0.1554                          | satu_data_jabar         | *Siapa saja Yang Telat Hari Ini?*        | 0.9742                          | get_lateAttendance      |  
| 3       | *Tampilkan embaran profile saya*   | 0.2480                          | get_users_details       | *Perlihatkan Informasi Profile Saya*     | 0.9967                          | get_users_details       |  

### Penjelasan:
1. **Input (Tanpa Kamus)**: Kalimat yang dimasukkan oleh pengguna tanpa melalui proses penerjemahan menggunakan kamus multibahasa.
2. **Probabilitas (Tanpa Kamus)**: Probabilitas model dalam memberikan respons berdasarkan input asli tanpa bantuan kamus.
3. **Tag (Tanpa Kamus)**: Tag yang diprediksi oleh model berdasarkan input asli.
4. **Input (Dengan Kamus)**: Kalimat yang telah diterjemahkan atau dimodifikasi dengan menggunakan kamus multibahasa untuk meningkatkan pemahaman model terhadap variasi bahasa.
5. **Probabilitas (Dengan Kamus)**: Probabilitas model dalam memberikan respons setelah penerjemahan dengan kamus multibahasa.
6. **Tag (Dengan Kamus)**: Tag yang diprediksi oleh model setelah penerjemahan dan pengolahan dengan kamus multibahasa.

**Threshold**: Model hanya memberikan respons yang dianggap valid jika probabilitas prediksi tag lebih dari **0.75**. Prediksi dengan probabilitas lebih rendah dari 0.75 dianggap tidak valid atau tidak pasti.


## Hasil
**Model tanpa Kamus Multibahasa**:
- **Akurasi**: 67,02%
- **Presisi**: 67,87%
- **Recall**: 67,02%
- **F1-Score**: 65,72%

**Model dengan Integrasi Kamus Multibahasa**:
- **Akurasi**: 91,49%
- **Presisi**: 93,35%
- **Recall**: 91,49%
- **F1-Score**: 90,61%

Integrasi kamus multibahasa secara signifikan meningkatkan kemampuan model dalam memahami dan merespons variasi bahasa, menghasilkan **akurasi respons yang lebih tinggi** dan **pengurangan kesalahan klasifikasi**.

### Grafik Hasil Pelatihan:
![Hasil Akurasi dan Loss](trainvallos.png)

### Grafik Akurasi:
![Hasil Akurasi](trainvallacc.png) 

### Confusion Matrix:
![Confusion Matrix](confmatrix.png) 



## Kesimpulan
Proyek ini berhasil mengembangkan **chatbot multibahasa** untuk aplikasi DigiTeam yang dapat menangani percakapan dalam bahasa Indonesia, Sunda, dan Inggris dengan efektif. Penggunaan **model FFNN** dan **IndoBERT** yang dipadukan dengan **kamus multibahasa** memungkinkan chatbot untuk memberikan respons yang relevan dan tepat waktu, meningkatkan efisiensi operasional dalam lingkungan kerja multibahasa.

Integrasi kamus multibahasa terbukti memberikan **peningkatan akurasi yang signifikan**, memungkinkan chatbot untuk memahami dan merespons variasi bahasa pengguna dengan lebih baik. Hasil pengujian menunjukkan bahwa model yang menggunakan kamus multibahasa mampu mencapai **akurasi sebesar 91,49%**, jauh lebih baik dibandingkan dengan model tanpa kamus yang hanya mencapai **67,02%**.

Dengan penerapan teknologi ini, diharapkan aplikasi DigiTeam dapat lebih optimal dalam mendukung interaksi pengguna dari berbagai latar belakang bahasa, serta meningkatkan produktivitas dan efektivitas dalam pengambilan keputusan yang berbasis data.