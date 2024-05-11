# PCD_UTS_202231007_2024_ITPLN

Nama : Fajar Budi Alamsyah

NIM : 202231007

## Tahapan Pengolahan Citra

1. Membaca Citra:

Citra dengan nama file 'nama_fajar.jpg' dibaca menggunakan OpenCV dan disimpan dalam variabel image.

2. Prapemrosesan Awal:

Citra diubah ke mode warna RGB menggunakan fungsi cv2.cvtColor. Hal ini dilakukan untuk memastikan bahwa citra bekerja dalam mode warna yang sesuai.

3. Ekstraksi Warna:

Citra dipisahkan menjadi saluran warna merah, hijau, dan biru menggunakan slicing array. Setiap saluran warna kemudian dihistogram menggunakan plt.hist untuk melihat distribusi intensitas piksel.

4. Penyesuaian Kontras

Dilakukan peningkatan kontras pada citra dengan mengalikan setiap nilai piksel dengan faktor alpha. Hal ini dilakukan dalam loop for dengan mengalikan setiap nilai piksel pada setiap saluran warna dengan alpha. Hasilnya disimpan dalam variabel citra_kontras.

6. Konversi ke Grayscale:

Citra diubah menjadi citra grayscale menggunakan fungsi cv2.cvtColor dengan parameter cv2.COLOR_BGR2GRAY. Ini menghasilkan citra grayscale yang hanya memiliki satu saluran warna.

8. Binerisasi untuk mencari nilai batas ambang

Dilakukan binerisasi citra grayscale menggunakan metode Otsu. Ambang batas untuk binerisasi dihitung otomatis menggunakan cv2.threshold dengan mode cv2.THRESH_OTSU. Hasilnya disimpan dalam variabel binary_blue, binary_green, binary_red, binary_rgb, binary_none, dan binary_red_blue.

10. Inversi:

Citra biner yang telah dihasilkan kemudian di-inversi menggunakan operasi bitwise NOT (cv2.bitwise_not). Ini dilakukan untuk menghasilkan citra yang objeknya menjadi putih dan latar belakangnya menjadi hitam, yang mempermudah untuk analisis lebih lanjut.
<br><br>

## Analasis Histogram

Image 1: Warna Biru
Pada gambar pertama, kita melihat dua subplot histogram yang menggambarkan distribusi intensitas nilai piksel pada citra berwarna biru. Histogram pertama di bagian atas menunjukkan distribusi yang cenderung seragam dengan nilai piksel yang tersebar di rentang nilai yang cukup lebar, meskipun ada sedikit puncak di sekitar nilai 50-100. Histogram kedua di bagian bawah memperlihatkan distribusi yang lebih meruncing dengan puncak yang tinggi di sekitar nilai 150. Ini mengindikasikan bahwa sebagian besar piksel pada citra memiliki intensitas biru yang cukup tinggi di area tersebut.

Image 2: Citra Kontras
Pada gambar kedua, kita melihat citra asli dan dua subplot histogram yang menggambarkan distribusi intensitas nilai piksel setelah penerapan operasi peningkatan kontras. Histogram pertama di bagian atas menunjukkan distribusi yang cenderung seragam dengan nilai piksel yang tersebar di rentang nilai yang cukup lebar, mirip dengan histogram biru pada gambar pertama. Namun, histogram kedua di bagian bawah memperlihatkan distribusi yang sangat berbeda, dengan puncak-puncak yang tajam dan terkonsentrasi pada nilai-nilai intensitas tertentu. Ini disebabkan oleh operasi peningkatan kontras yang mempertajam perbedaan intensitas antar piksel, sehingga menciptakan distribusi yang lebih bergradasi dan tidak merata.

Image 3: Warna Merah
Pada gambar ketiga, kita melihat dua subplot histogram yang menggambarkan distribusi intensitas nilai piksel pada citra berwarna merah. Kedua histogram memperlihatkan distribusi yang sangat berbeda dari warna biru pada gambar pertama. Distribusinya cenderung berpusat pada nilai-nilai rendah, dengan puncak yang tinggi di sekitar nilai 0-5. Ini mengindikasikan bahwa sebagian besar piksel pada citra memiliki intensitas merah yang rendah atau gelap. Namun, terdapat pula beberapa puncak kecil di nilai-nilai yang lebih tinggi, menunjukkan adanya area-area dengan intensitas merah yang lebih cerah.

Secara keseluruhan, analisis histogram memberikan informasi penting tentang karakteristik distribusi intensitas pada citra, yang dapat digunakan untuk berbagai tujuan pengolahan citra seperti peningkatan kontras, segmentasi, dan lain-lain.

## Nilai Batas Ambang

1. *None (Citra Tanpa Warna)*: Nilai ambang batas = 0.0
2. *Red-Blue (Citra Merah-Biru)*: Nilai ambang batas = 143.0
3. *RGB (Citra Warna RGB)*: Nilai ambang batas = 144.0
4. *Biru (Saluran Warna Biru)*: Nilai ambang batas = 141.0
5. *Hijau (Saluran Warna Hijau)*: Nilai ambang batas = 145.0
6. *Merah (Saluran Warna Merah)*: Nilai ambang batas = 145.0

Penjelasan :

1. None (Citra Tanpa Warna): Citra yang diproses tanpa warna (grayscale) memiliki variasi intensitas piksel yang rendah. Sehingga, nilai ambang batas yang dihitung menggunakan metode Otsu cenderung mendekati 0, karena tidak ada variasi warna yang signifikan untuk dipisahkan.

2. Red-Blue (Citra Merah-Biru): Citra yang hanya terdiri dari saluran warna merah dan biru memiliki variasi warna yang lebih sedikit dibandingkan citra RGB. Namun, ada cukup variasi warna antara merah dan biru sehingga nilai ambang batasnya sedikit lebih tinggi dari citra tanpa warna.

3. RGB (Citra Warna RGB): Citra berwarna RGB memiliki variasi warna yang lebih kompleks karena terdiri dari tiga saluran warna. Oleh karena itu, nilai ambang batasnya sedikit lebih tinggi dari citra yang hanya terdiri dari dua saluran warna (merah-biru).

4. Biru (Saluran Warna Biru): Saluran warna biru memiliki intensitas piksel yang rendah dibandingkan dengan saluran warna lainnya dalam citra RGB. Oleh karena itu, nilai ambang batasnya sedikit lebih rendah dari saluran warna hijau dan merah.

5. Hijau (Saluran Warna Hijau): Saluran warna hijau seringkali memiliki intensitas piksel yang cukup tinggi dalam citra alam. Oleh karena itu, nilai ambang batasnya sedikit lebih tinggi dari saluran warna biru.

6. Merah (Saluran Warna Merah): Saluran warna merah seringkali memiliki intensitas piksel yang cukup tinggi dalam citra manusia. Oleh karena itu, nilai ambang batasnya tinggi dan sama dengan saluran warna hijau.

## Teori Pendukung

Berikut adalah beberapa teori yang mendukung :

1. *Model Warna RGB*: Codingan mengambil citra dan memprosesnya dalam model warna RGB, yang merupakan model dasar untuk merepresentasikan warna dalam citra digital. Model ini berdasarkan kombinasi tiga saluran warna: merah (Red), hijau (Green), dan biru (Blue).

2. *Prapemrosesan Citra*: Prapemrosesan awal dilakukan untuk meningkatkan kualitas citra sebelum memulai pengolahan. Prapemrosesan mencakup konversi warna, penyesuaian kontras, dan peningkatan kecerahan.

3. *Histogram*: Histogram digunakan untuk menganalisis distribusi intensitas piksel dalam citra. Hal ini berguna untuk memahami karakteristik citra sebelum dan sesudah pengolahan.

4. *Segmentasi*: Segmentasi digunakan untuk memisahkan area atau objek yang menarik dalam citra. Pada kode tersebut, segmentasi dilakukan dengan cara membagi citra menjadi saluran warna merah, hijau, dan biru.

5. *Ekstraksi Fitur*: Fitur-fitur penting dari citra diekstraksi untuk analisis lebih lanjut. Pada kode tersebut, fitur-fitur seperti intensitas piksel dan warna diekstraksi untuk setiap saluran warna.

6. *Binerisasi*: Binerisasi digunakan untuk mengubah citra menjadi citra biner (hitam putih) dengan menghitung ambang batas. Ini dilakukan untuk memisahkan objek dari latar belakang dalam citra.

7. *Inversi*: Inversi digunakan untuk membalik citra biner, membuat objek menjadi putih dan latar belakang menjadi hitam. Ini berguna untuk analisis lebih lanjut, seperti deteksi tepi atau penghitungan luas objek.

8. *Otsu's Thresholding*: Otsu's Thresholding adalah metode untuk menghitung ambang batas secara otomatis dalam binerisasi citra. Metode ini memilih ambang batas yang menghasilkan varian dalam kelas terendah, sehingga memungkinkan pemisahan yang optimal antara objek dan latar belakang.

Dengan menggabungkan prinsip-prinsip ini, codingan tersebut dapat melakukan berbagai operasi pengolahan citra, termasuk prapemrosesan, segmentasi, ekstraksi fitur, binerisasi, dan inversi, yang dapat digunakan untuk berbagai aplikasi seperti analisis citra medis, pengenalan pola, dan pengolahan gambar.
