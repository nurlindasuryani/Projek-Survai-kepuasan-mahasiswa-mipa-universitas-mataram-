# PROJEK-SURVEI-kEPUASAN-MAHASISWA-FMIPA-UNIVERSITAS-MATARAM

## LATAR BELAKANG

Kantin merupakan salah satu fasilitas penting di lingkungan kampus yang berfungsi untuk memenuhi kebutuhan konsumsi mahasiswa selama menjalani kegiatan perkuliahan. Keberadaan kantin yang menyediakan makanan dengan kualitas baik, harga terjangkau, dan pelayanan yang memuaskan sangat berpengaruh terhadap kenyamanan mahasiswa. Pelayanan kantin yang baik dapat membantu mahasiswa memenuhi kebutuhan makan dan minum dengan lebih mudah, sehingga dapat mendukung kelancaran aktivitas akademik di kampus. Universitas Mataram, khususnya Fakultas Matematika dan Ilmu Pengetahuan Alam Universitas Mataram, memiliki kantin yang dimanfaatkan oleh mahasiswa dari Jurusan Biologi, Kimia, Fisika, Statistika, dan Matematika. Kantin tersebut menjadi salah satu fasilitas yang sering digunakan mahasiswa untuk membeli makanan dan minuman di sela-sela kegiatan perkuliahan. Oleh karena itu, kualitas pelayanan kantin perlu dievaluasi secara berkala agar dapat terus memenuhi harapan mahasiswa. Kepuasan mahasiswa terhadap pelayanan kantin dapat diukur melalui beberapa aspek, yaitu variasi menu makanan, kebersihan makanan, kebersihan tempat makan, harga makanan, porsi makanan, keramahan penjual, kecepatan pelayanan, kenyamanan tempat duduk, kebersihan peralatan makan, dan kualitas makanan secara keseluruhan. Penilaian terhadap aspek-aspek tersebut dapat memberikan gambaran mengenai kualitas pelayanan kantin yang dirasakan oleh mahasiswa. Penelitian ini dilakukan untuk mengetahui tingkat kepuasan mahasiswa terhadap pelayanan kantin FMIPA Universitas Mataram.

## TUJUAN PENELITIAN
1. Mengetahui tingkat kepuasan mahasiswa terhadap pelayanan kantin FMIPA Universitas Mataram.
2. Menentukan jumlah sampel penelitian menggunakan rumus Slovin.
3. Mengetahui validitas instrumen kuesioner yang digunakan dalam penelitian.
4. Mengetahui reliabilitas instrumen kuesioner menggunakan metode Cronbach Alpha.
5. Menganalisis data hasil survei menggunakan aplikasi R Studio.

## Metode Penelitian
Penelitian ini menggunakan metode kuantitatif dengan pendekatan survei. Pengumpulan data dilakukan dengan menyebarkan kuesioner kepada mahasiswa FMIPA Universitas Mataram. Populasi penelitian terdiri dari mahasiswa Program Studi Matematika, Statistika, Biologi, Kimia, dan Fisika.
Penentuan jumlah sampel dilakukan menggunakan rumus Slovin dengan tingkat kesalahan sebesar 10%.
n=N/(1+N(e^2)).
Keterangan:
n= jumlah sampel 
N= jumlah populasi 
e= tingkat kesalahan 
Instrumen penelitian menggunakan kuesioner dengan skala Likert yang terdiri dari lima pilihan jawaban, yaitu:
1. Sangat Tidak Setuju,
2. Tidak Setuju,
3. Netral,
4. Setuju, dan
5. Sangat Setuju.
Pengolahan data dilakukan menggunakan aplikasi R Studio.
Pengambilan Sampel
## PROSES ANALISIS DATA
1. Menentukan Jumlah Sampel Menggunakan Rumus Slovin

Pengambilan sampel dilakukan menggunakan rumus Slovin. Populasi penelitian merupakan mahasiswa dari lima program studi di FMIPA Universitas Mataram, yaitu Matematika, Statistika, Biologi, Kimia, dan Fisika dengan jumlah populasi sebanyak 897 mahasiswa.
Rumus Slovin yang digunakan yaitu:
n=1+N(e2)N
Keterangan:
n = jumlah sampel
N = jumlah populasi
e = tingkat kesalahan
Dengan jumlah populasi sebanyak 897 mahasiswa dan tingkat kesalahan tertentu, diperoleh jumlah sampel penelitian sebanyak 30 responden. Sampel dipilih dari lima program studi di FMIPA Universitas Mataram.

2. Menginfor Data
Data penelitian diperoleh melalui penyebaran kuesioner kepada mahasiswa. Data hasil kuesioner kemudian disimpan dalam file Excel dan diimpor ke dalam R Studio menggunakan package readxl.
library(readxl)
data_kuesioner_teksam <- read_excel("D:/data kuesioner teksam.xlsx")

3. Uji Data
   Uji Validitas

Uji validitas digunakan untuk mengetahui apakah item pertanyaan pada kuesioner valid atau mampu mengukur variabel penelitian. Pengujian dilakukan menggunakan korelasi Pearson antara skor item dan skor total.
#uji validitas
item <- data_kuesioner_teksam[, c("P1","P2","P3","P4","P5","P6","P7","P8","P9","P10")]
#menghitung skor total responden
total <- rowSums(item)
#korelasi item dengan skor total (validitas item)
cor_validitas <- cor(item, total)
cor_validitas
#korelasi item-total lengkap (opsional)
corr.test(item)
Kriteria pengujian:

p-value < 0,05 → valid
p-value > 0,05 → tidak valid

4. Uji Rehabilitas
Uji reliabilitas digunakan untuk mengetahui konsistensi instrumen penelitian menggunakan metode Cronbach Alpha.
#UJI RELIABILITAS
#menghitung Cronbach Alpha (uji reliabilitas instrumen)
reliabilitas <- alpha(item)
#nilai Cronbach Alpha saja
reliabilitas$total$raw_alpha
#seluruh output reliabilitas
reliabilitas$total
Kriteria pengujian:

Cronbach Alpha > 0,60 → reliabel
Cronbach Alpha < 0,60 → tidak reliabel
