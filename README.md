# Final Project - Airbnb Property Clustering

## Perkenalan
Halo, nama saya Mufti Habibie Alayubi. ini Merupakan final project saya di Rakamin Academy. Proyek ini bertujuan untuk mengidentifikasi segmen-segmen properti yang relevan di platform Airbnb menggunakan teknik klasterisasi berdasarkan dataset Seattle Airbnb Open Data. Dalam proyek ini, saya menerapkan berbagai algoritma klasterisasi seperti K-Means, Agglomerative, Self-Organizing Map (SOM), dan DBSCAN untuk mengelompokkan properti berdasarkan harga, lokasi, fasilitas, dan jenis properti.

## Tujuan Proyek
- **Mengidentifikasi Segmen Properti**: Menggunakan algoritma klasterisasi untuk mengelompokkan properti berdasarkan karakteristik yang serupa.
- **Mengoptimalkan Strategi Platform**: Menyesuaikan harga dan strategi pemasaran berdasarkan hasil klasterisasi.
- **Menetapkan Harga Berdasarkan Klaster**: Menyesuaikan harga properti untuk setiap segmen pasar.
- **Memilih Model Klasterisasi Terbaik**: Membandingkan dan memilih algoritma klasterisasi terbaik untuk analisis data.

## Dataset
Proyek ini menggunakan **Seattle Airbnb Open Data**, yang mencakup lebih dari 3818 baris data dan 20 variabel, termasuk harga per malam, jenis properti, fasilitas, dan lokasi. Data ini memberikan gambaran tentang pasar akomodasi di Seattle, namun juga memerlukan pembersihan data untuk memastikan kualitas analisis.

## Metode Klasterisasi
Algoritma yang digunakan dalam proyek ini meliputi:
- **K-Means**: Membagi data ke dalam cluster berdasarkan jarak rata-rata dari pusat cluster.
- **Agglomerative Clustering**: Menggabungkan cluster yang paling mirip secara hierarkis.
- **Self-Organizing Map (SOM)**: Jaringan saraf untuk mengelompokkan data secara alami.
- **DBSCAN**: Algoritma berbasis densitas yang mendeteksi cluster dengan kepadatan tinggi.

## Proses Data
Proses pembersihan dan analisis data termasuk:
- Penanganan missing values dengan imputasi menggunakan mean atau mode.
- Penanganan duplikasi dan outliers dengan metode IQR dan SOM.
- Feature encoding untuk variabel kategorikal dan seleksi fitur berdasarkan korelasi dengan variabel target.

## Evaluasi Model
Evaluasi dilakukan menggunakan tiga metrik utama:
- **Davies-Bouldin Index**: Menilai pemisahan antar cluster.
- **Silhouette Score**: Mengukur seberapa baik data berada dalam cluster yang sesuai.
- **Calinski-Harabasz Index**: Mengukur seberapa kompak dan terpisah cluster yang terbentuk.

Hasil evaluasi menunjukkan bahwa **K-Means** adalah model klasterisasi yang terbaik berdasarkan metrik tersebut.

## Hasil dan Rekomendasi
Hasil klasterisasi menghasilkan lima segmen pasar yang berbeda:
1. **Budget Single**: Properti terjangkau untuk solo traveler atau pasangan muda.
2. **Spacious Family Home**: Properti luas untuk keluarga besar.
3. **Luxury Group Stay**: Properti mewah untuk grup besar dengan anggaran tinggi.
4. **Economy Shared Room**: Kamar bersama dengan harga terjangkau untuk backpacker.
5. **Mid-Range Private Room**: Kamar pribadi dengan harga menengah.

Rekomendasi bisnis meliputi personalisasi pengalaman pelanggan, promosi yang lebih tepat sasaran, dan penetapan harga dinamis berdasarkan segmen pasar.

## Tantangan dan Keterbatasan
- Beberapa variabel yang tidak memiliki korelasi kuat menghambat analisis lebih dalam.
- Keterbatasan dalam menampilkan visualisasi gambar properti pada Streamlit.
- Data yang tidak lengkap atau konsisten mengurangi akurasi analisis.
