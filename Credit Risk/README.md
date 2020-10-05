# Credit Risk
Credit risk adalah resiko yang harus ditanggung oleh seorang individu atau lembaga ketika memberikan pinjaman - biasanya dalam bentuk uang - ke individu atau pihak lain.

Resiko ini berupa tidak bisa dibayarkannya pokok dan bunga pinjaman, sehingga mengakibatkan kerugian berikut:

gangguan aliran kas (cash flow) sehingga modal kerja terganggu.
meningkatkan biaya operasional untuk mengejar pembayaran tersebut (collection).
Untuk memperkecil resiko kredit ini, biasanya dilakukan proses yang disebut dengan credit scoring dan credit rating terhadap pihak peminjam. Output proses ini akan menjadi basis untuk menentukan apakah aplikasi pengajuan pinjaman baru diterima atau ditolak.

## Credit Score
Credit score adalah nilai resiko yang diberikan kepada seorang individu atau organisasi yang mengajukan pinjaman berdasarkan rekam jejak pinjaman dan pembayaran yang dilakukan. Proses pemberian credit score ini biasanya disebut sebagai credit scoring.

Perhitungan credit score biasanya dibuat berdasarkan data historis lamanya keterlambatan pembayaran dan yang tidak bayar sama sekali (bad debt). Bad debt biasanya mengakibatkan lembaga pemberian kredit harus menyita aset atau melakukan write off .
Nilai credit score biasanya bervariasi antar lembaga. Namun banyak yang kemudian mengadopsi model FICO Score yang memiliki rentang nilai 300 - 850. Semakin tinggi nilai yang didapatkan, maka semakin baik tingkat kemampuan seseorang atau sebuah lembaga untuk membayar pinjaman.

## Risk Rating
Kadang banyak lembaga yang menggunakan risk rating atau tingkat resiko. Terbalik dengan credit score, semakin tinggi rating ini menunjukkan resiko yang semakin meningkat.

Selain itu kodifikasi juga dibuat lebih simpel  dibandingkan rentang nilai sehingga keputusan yang bisa diambil lebih cepat. Contoh, misalkan penggunaan kombinasi seperti huruf AAA,  AA+, P-1, dan seterusnya. Atau  untuk banyak internal lembaga peminjam, kategorisasi hanya menggunakan rentang angka yang kecil misalkan 1 sampai dengan 5.

Mari kita lihat contoh data risk rating dengan pendekatan terakhir ini pada subbab berikutnya.

## Analisa dan Model Pengambilan Keputusan
Seorang analis akan melakukan penelusuran terhadap data kita untuk mencari pola. Berikut adalah temuannya: 
- Jika jumlah tanggungan berjumlah lebih dari 4, kecenderungan resikonya sangat tinggi (rating 4 dan 5).
- Jika durasi pinjaman semakin lama yaitu lebih dari 24 bulan, maka kecenderungan resiko juga meningkat (rating 4 dan 5).

Dari kedua temuan ini, analis akan membentuk aturan-aturan untuk menuntun pengambilan keputusan (decision making model) terhadap pengajuan pinjaman baru untuk sebagai berikut:

1. Jika jumlah tanggungan berjumlah kurang dari 5 orang , dan durasi pinjaman kurang dari 24 bulan maka rating diberikan nilai 2 dan pengajuan pinjaman diterima. 
2. Jika jumlah tanggungan berjumlah lebih dari 4 orang dan durasi pinjaman lebih dari 24 bulan maka maka rating diberikan nilai 5 dan pengajuan pinjaman ditolak.
3. Jika jumlah tanggungan berjumlah kurang dari 5, dan durasi pinjaman kurang dari 36 bulan maka maka rating diberikan nilai 3 dan diberikan pinjaman. 

Nah, tiga aturan itu kita sebut sebagai model untuk memprediksi nilai risk rating dan menjadi basis pengambilan keputusan terhadap aplikasi pinjaman baru.

Dengan model ini, lembaga pinjaman akan semakin cepat mengambil keputusan dan dengan tingkat kesalahan pengambilan keputusan yang lebih minim.

## Kesimpulan
Credit risk adalah resiko yang harus ditanggung oleh seorang individu atau lembaga ketika memberikan pinjaman - biasanya dalam bentuk uang - ke individu atau pihak lain.

Resiko ini berupa tidak bisa dibayarkannya pokok dan bunga pinjaman, sehingga mengakibatkan kerugian berikut:
- gangguan aliran kas (cash flow) sehingga modal kerja terganggu.
- meningkatkan biaya operasional untuk mengejar pembayaran tersebut (collection).

Credit score dan risk rating adalah dua penilaian yang dilakukan meminimalkan resiko dari pihak pemberi kredit. Karena berdasarkan kedua model penilaian tersebut, akan diputuskan apakah aplikasi peminjaman seseorang disetujui atau ditolak.

# SOURCE
[1] https://academy.dqlab.id/