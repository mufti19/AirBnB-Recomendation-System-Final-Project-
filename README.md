# Airbnb Property Clustering - Project Overview

## Masalah
- Pengguna Airbnb seringkali kesulitan memilih properti yang sesuai dengan preferensi mereka karena banyaknya pilihan yang tersedia.
- Ketidaksesuaian pencarian properti dengan preferensi pengguna dapat menurunkan tingkat kepuasan dan kepercayaan terhadap layanan.
- Diperlukan sistem yang dapat mengelompokkan properti berdasarkan karakteristik yang serupa untuk mempermudah pencarian properti yang sesuai dengan kebutuhan pengguna.

## Pertanyaan Riset
- Bagaimana cara mengelompokkan properti Airbnb berdasarkan karakteristik seperti harga, lokasi, fasilitas, dan jenis properti?
- Apakah algoritma klasterisasi dapat digunakan untuk mengidentifikasi segmen pasar yang relevan dalam data properti Airbnb?

## Tujuan
- Mengidentifikasi segmen-segmen properti berdasarkan karakteristik yang relevan.
- Mengoptimalkan strategi harga dan pemasaran dengan mengelompokkan properti ke dalam klaster-klaster yang lebih relevan.

---

## Analisis Data (Eksplorasi Data)
1. **Distribusi Harga Properti**: Harga properti cenderung memiliki distribusi yang condong ke kanan (positif skew), yang menunjukkan mayoritas properti memiliki harga terjangkau.

![alt text](https://github.com/mufti19/AirBnB-Recomendation-System-Final-Project-/blob/main/Data%20Exploration/Property%20Price%20Distribution.png)<br>
2. **Jenis Properti**: Tipe kamar *Entire home/apt* lebih banyak tersedia dibandingkan dengan jenis kamar lain seperti *Private room* dan *Shared room*.

![alt text](https://github.com/mufti19/AirBnB-Recomendation-System-Final-Project-/blob/main/Data%20Exploration/Number%20of%20Properties%20by%20Room%20Type.png)<br>
3. **Harga vs Rating Properti**: Banyak properti dengan harga tinggi memiliki rating yang baik, namun ada juga properti dengan harga rendah yang mendapatkan rating tinggi.

![alt text](https://github.com/mufti19/AirBnB-Recomendation-System-Final-Project-/blob/main/Data%20Exploration/Price%20vs%20Property%20Rating.png)<br>

---

## Data Processing
- **Penanganan Missing Values**: 
  - Variabel dengan missing values lebih dari 10% dihapus.
  - Nilai yang hilang pada variabel lain diisi dengan *mean* (untuk data numerik) atau *mode* (untuk data kategorikal).
- **Penanganan Outliers**: 
  - Metode IQR digunakan untuk mendeteksi dan menangani outliers pada kolom seperti *beds*, *bathrooms*, dan *bedrooms*.
- **Feature Engineering**: 
  - Pengkodean variabel kategorikal dilakukan untuk mempersiapkan data bagi model machine learning, seperti *host_is_superhost*, *is_location_exact*, dan *Instant_bookable*.

---

## ML Modeling
- **Algoritma yang Diterapkan**:
  - K-Means Clustering
  - Agglomerative Clustering
  - Self-Organizing Map (SOM)
  - DBSCAN
- **Pemilihan Jumlah Cluster Optimal**:
  - K-Means dan Agglomerative menggunakan 5 cluster berdasarkan metode Elbow.
  - SOM menghasilkan 3 cluster berdasarkan Indeks Dunn.
  - DBSCAN menggunakan parameter standar dengan *eps* = 0.3 dan *min_samples* = 5.

---

## Model Evaluation
- **Evaluasi Model dengan Metrik Klasterisasi**:
  - **Davies-Bouldin Index**: Menilai kedekatan antar cluster, semakin rendah nilai ini semakin baik.
  - **Silhouette Score**: Menilai kualitas pemisahan cluster.
  - **Calinski-Harabasz Index**: Mengukur seberapa kompak dan terpisah antar cluster.

- **Hasil Evaluasi**:

| Model           | Davies-Bouldin Index | Silhouette Score | Calinski-Harabasz Index |
|-----------------|----------------------|------------------|-------------------------|
| KMeans          | 0.804                | 0.492            | 4.756.113               |
| Agglomerative   | 0.807                | 0.478            | 4.348.488               |
| DBSCAN          | 0.658                | 0.187            | 152.192                 |
| SOM             | 0.927                | 0.409            | 3.648.951               |

  - **K-Means**: Metrik evaluasi menunjukkan performa terbaik dengan skor tinggi pada Davies-Bouldin Index dan Silhouette Score.
  - **DBSCAN**: Hasil kurang baik pada Silhouette Score, tetapi mampu mendeteksi beberapa outliers dengan baik.
  - **SOM**: Meskipun memadai, terdapat beberapa tumpang tindih antar cluster.
---

## Business Insight & Recommendations

#### Segmentasi Pasar:
- **Cluster 1 (Budget Single)**:
  - **Deskripsi**: Akomodasi yang terjangkau untuk 1-2 orang dengan harga $113/malam. Cluster ini menawarkan privasi penuh dengan seluruh unit yang bisa disewa, seperti *Entire Home/Apt*.
  - **Target Pasar**: Solo traveler atau pasangan yang mengutamakan harga hemat dan privasi.
  
- **Cluster 2 (Spacious Family Home)**:
  - **Deskripsi**: Properti luas untuk keluarga besar (6 orang) dengan harga $200/malam. Memiliki 3 kamar tidur yang cocok untuk grup atau keluarga yang membutuhkan ruang lebih.
  - **Target Pasar**: Keluarga atau grup yang menginginkan akomodasi yang lebih luas dan nyaman dengan harga yang masih terjangkau.
  
- **Cluster 3 (Luxury Group Stay)**:
  - **Deskripsi**: Mirip dengan Cluster 2, namun dengan harga yang lebih mahal ($202/malam) dan mencakup lebih banyak fasilitas untuk grup besar, termasuk kenyamanan tambahan.
  - **Target Pasar**: Grup besar atau keluarga yang mencari pengalaman lebih mewah dengan fasilitas lebih lengkap.
  
- **Cluster 4 (Economy Shared Room)**:
  - **Deskripsi**: Pilihan akomodasi terjangkau dengan harga $70/malam untuk kamar *Shared Room*. Cocok untuk mereka yang mengutamakan penghematan biaya namun tetap membutuhkan sedikit privasi.
  - **Target Pasar**: Pelancong dengan anggaran terbatas yang tidak membutuhkan banyak ruang pribadi, lebih memilih berbagi fasilitas.
  
- **Cluster 5 (Mid-Range Private Room)**:
  - **Deskripsi**: Opsi dengan harga $134/malam untuk 4 orang dalam kamar *Private Room*. Memberikan keseimbangan yang baik antara harga dan kenyamanan.
  - **Target Pasar**: Individu atau pasangan yang mencari privasi dan kenyamanan dengan harga menengah.

---

#### Rekomendasi Bisnis:

- **Cluster 1 (Budget Single)**:
  - **Target Market**: Solo traveler, pasangan muda, backpacker.
  - **Strategic Marketing**:
    - Fokuskan kampanye di platform seperti TikTok dan Instagram dengan tema: “#NYAMAT. NYAMAN, Harga heMAT”.
    - Gunakan micro-influencer yang membahas traveling hemat dan solo trip.
  - **Promosi**:
    - “Stay 3 nights, get 1 free” untuk tamu solo.
    - Diskon 10-15% untuk pengguna pertama.
    - Tambahkan fasilitas WiFi cepat untuk digital nomad.

- **Cluster 2 (Spacious Family Home)**:
  - **Target Market**: Keluarga besar, wisatawan lokal dengan anak-anak, reuni keluarga.
  - **Strategic Marketing**:
    - Highlight kenyamanan & kebersamaan keluarga dengan kampanye: “#Kenyamanan Keluarga di Setiap Sudut”.
    - Tampilkan video walkthrough rumah (YouTube, Facebook Ads).
  - **Promosi**:
    - Free breakfast atau airport pickup untuk keluarga minimal 4 orang.
    - Bundle deals untuk sewa 5 malam ke atas.
    - Paket “Liburan Sekeluarga” saat libur sekolah atau Lebaran.

- **Cluster 3 (Luxury Group Stay)**:
  - **Target Market**: Rombongan eksekutif, wisatawan premium, keluarga besar, outing kantor dengan budget tinggi.
  - **Strategic Marketing**:
    - Gunakan platform seperti Airbnb Luxe.
    - Gunakan strategi influencer premium dengan YouTuber travel atau lifestyle high-end.
    - Kampanye visual mewah: “Luxury Experience Together”.
  - **Promosi**:
    - Penawaran eksklusif seperti checkout atau butler service untuk unit tamu 3+ malam.
    - Paket private tour atau BBQ di rooftop sebagai bonus.
    - Upselling: tawarkan pengalaman spa, transportasi, atau chef pribadi.

- **Cluster 4 (Economy Shared Room)**:
  - **Target Market**: Backpacker, pelancong solo, mahasiswa, pekerja lepas.
  - **Strategic Marketing**:
    - Posisi sebagai “Teman Baru, Pengalaman Baru”.
  - **Promosi**:
    - “Stay more, pay less” diskon mingguan.
    - Free welcome drink atau sarapan gratis.
    - Bonus “Referral Guest” – diskon untuk bawa teman.

- **Cluster 5 (Mid-Range Private Room)**:
  - **Target Market**: Grup kecil, pasangan berlibur, pekerja remote.
  - **Strategic Marketing**:
    - Kampanye: “Privacy, Expensive? Don’t Worry”.
    - Promosikan di LinkedIn untuk menarik pekerja remote (Work from Bali).
    - Fokus di platform seperti Airbnb filter mid-range.
  - **Promosi**:
    - Diskon 15% untuk pemesanan 7 hari ke atas.
    - Include coworking day pass atau free laundry.
    - Highlight review tamu tentang kenyamanan & privasi.

---
