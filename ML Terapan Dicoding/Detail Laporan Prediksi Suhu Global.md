# Detail Laporan

## 1. Domain Proyek

Pemanasan global adalah isu penting yang mempengaruhi planet kita. Dengan memahami bagaimana suhu bumi berubah sepanjang waktu, kita dapat lebih baik memahami dan merespons perubahan iklim. Salah satu cara untuk melakukan ini adalah dengan menggunakan teknik pemodelan prediktif untuk memahami tren suhu di masa mendatang. [^1^][1] 
Dengan diprediksinya tren pemanasan global dapat meningkatkan kualitas antisipasi pencegahan yang lebih terukur. Hasil prediksi ini juga memberikan gambaran besar kepada para pemerhati lingkungan untuk menerapkan strategi pencegahan pemanasan global.

## 2. Business Understanding

Hasil penelitian ini akan berdampak pada keputusan dari para pemerhati lingkungan dengan ditemani hasil penelitian lain untuk mengantisipasi pemanasan global dalam jangka waktu panjang karena perubahan suhu dunia adalah proses yang perlahan-lahan namun pasti.
Dengan adanya hasil penelitian ini maka penelitian ini dapat memberikan wawasan seberapa banyak sumber daya yang dibutuhkan untuk menyelesaikan dampak pemanasan global ke depannya baik dari sudut pandang pemerintah ataupun privat yang peduli dengan isu pemanasan global.
Keberhasilan prediksi ini akan ditentukan oleh seberapa tepat tindakan yang sudah dilakukan berdasarkan metode yang dibuat untuk mengatasi pemanasan global beberapa tahun ke depan.

## 3. Data Understanding

Dataset mengandung 9 fitur yaitu:
- dt: waktu pengamatan
- LandAverage Temperature: suhu rata-rata daratan
- LandAverageTemperatureUncertainty: nilai error suhu rata-rata daratan
- LandMaxTemperature: suhu maksimum daratan
- LandMaxTemperatureUncertainty: nilai error suhu maksimum daratan
- LandMinTemperature: suhu minimum daratan
- LandMinTemperatureUncertainty: nilai error suhu minimum daratan
- LandAndOceanAverageTemperature: suhu rata-rata gabungan daratan dan samudra (global)
- LandAndOceanAverageTemperature: nilai error suhu rata-rata gabungan daratan dan samudra

Dataset yang digunakan dalam proyek ini berisi catatan historis suhu global. Bagian dataset yang digunakan adalah dua kolom: `dt` yang berisi tanggal pengamatan, dan `LandAndOceanAverageTemperature` yang berisi suhu rata-rata global pada tanggal tersebut. Dataset ini memiliki kolom `LandAndOceanAverageTemperature` yang terisi mulai 01 Januari 1850 yaitu pada baris ke-1200 yang menjadi awal dari prediksi suhu global.[^2^][2]
Di dalam data tersebut terlihat bahwa suhu globa selalu meningkat dari waktu ke waktu mulai dari awal revolusi industri di tahun 1750 namun tidak lebih dari 20 derajat celcius.

## 4. Data Preparation

Data preparation melibatkan beberapa langkah, termasuk:

- Mengekstrak kolom dt sebagai tanggal dan LandAndOceanAverageTemperature sebagai suhu rata-rata global
- Mengekstrak baris ke-1200 karena mulai pada baris tersebut suhu rata-rata global tersedia
- Menormalisasi data agar lebih mudah diproses saat pelatihan model
- Splitting data dengan menggunakan train_test_split() dengan ukuran test_size sebesar 0.2 dan tidak dishuffle.
## 5. Modeling

Modeling dilakukan menggunakan LSTM (Long Short-Term Memory), sebuah jenis jaringan saraf berulang yang sangat efektif untuk pemodelan data deret waktu. Model ini memiliki layer pertama berjenis LSTM dengan 4 unit, layer kedua berjenis Dense dengan 8 unit, layer ketiga berjenis LSTM dengan 1 unit dan layer output Dense dengan 1 unit. Model ini dikompilasi dengan loss function 'mean_absolute_error', optimizer 'adam' dan metrics MeanAbsoluteError. Epoch dari training adalah sebanyak 100 kali.

## 6. Evaluation

Akurasi dari train set yang menggunakan metrik MeanAbsoluteError adalah 0.02 dan saat model diuji pada test set juga memiliki akurasi test score sebesar 0.02.
Model ini diterapkan untuk memprediksi pemanasan global 10 tahun ke depan dan hasilnya cukup memuaskan dapat memprediksi peningkatan suhu global. Namun terdapat penurunan suh mulai dari tahun 2031 hingga 2033.
Hal ini mungkin karena overfitting pada dataset. Model yang lebih bagus diharapkan dapat memperbaiki kecacatan prediksi ini. Atau mungkin model ini memerlukan dataset yang lebih besar yang mana merupakan kekurangan dataset sendiri.
Namun prediksi model ini cukup akurat untuk memprediksi peningkatan suhu global 6 tahun ke depan yang merupakan waktu yang cukup lama untuk melakukan berbagai tindakan preventif oleh para pemerhati lingkungan.

---

Referensi:
[^1^][1]IPCC, 2014: Climate Change 2014: Synthesis Report. Contribution of Working Groups I, II and III to the Fifth Assessment Report of the Intergovernmental Panel on Climate Change [Core Writing Team, R.K. Pachauri and L.A. Meyer (eds.)]. IPCC, Geneva, Switzerland, 151 pp.
[^2^][2][GlobalTemperatures.csv](https://www.kaggle.com/datasets/berkeleyearth/climate-change-earth-surface-temperature-data)