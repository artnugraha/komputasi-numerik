# Catatan Kuliah: Aproksimasi dan Analisis Galat dalam Metode Numerik

Metode numerik pada dasarnya adalah metode mengaproksimasi (mendekati) solusi suatu permasalahan melalui algoritma tertentu dengan galat (*error*) yang diharapkan sekecil-kecilnya. Istilah komputasi numerik kemudian kerap digunakan mengingat metode numerik diterapkan dalam komputer melalui bahasa pemrograman tertentu. Dalam kuliah ini, kita menggunakan Python sebagai implementasi algoritma setiap metode numerik yang dibahas.

## 1. Urgensi Metode Numerik

Banyak permasalahan di bidang sains dan teknik tidak memiliki solusi analitik (solusi eksak) atau solusinya sangat sulit diperoleh. Metode numerik memberikan pendekatan praktis untuk memperoleh solusi pendekatan melalui algoritma iteratif. Dalam rangkaian kuliah mendatang, kita akan menjabarkan beberapa metode untuk
- pencarian akar-akar persamaan nonlinier
- penyelesaian permasalahan aljabar linier
- interpolasi dan regresi
- integrasi dan diferensiasi
- penyesaian persamaan diferensial
- (bila cukup waktu) transformasi Fourier dan pembelajaran mesin

Dasar-dasar metode numerik di atas dapat menjadi fondasi yang berguna untuk kebanyakan permasalahan sains dan teknik yang ada di masa kini maupun masa mendatang. Perlu ditekankan bahwa solusi numerik harus dieksekusi secara efisien dari sisi waktu dan sumber daya. Oleh karena itu, algoritma harus dirancang agar stabil, akurat, dan mampu mengendalikan galat yang muncul akibat keterbatasan representasi bilangan dalam komputer.

---

## 2. Representasi Bilangan dalam Komputer

Bilangan *real* dalam komputer direpresentasikan menggunakan format *floating-point*, yang pada dasarnya merupakan representasi bilangan dalam bentuk biner. 

Representasi ini melibatkan:

- **Bilangan Biner:**  
  Semua data dalam komputer disimpan dalam bentuk biner (0 dan 1). Bilangan desimal harus dikonversi ke format biner untuk diproses.

- **Komponen Floating-Point:**  
  Format floating-point (misalnya, sesuai standar IEEE 754) terdiri atas tiga bagian:
  - **Tanda (Sign):** Menunjukkan apakah bilangan positif atau negatif.
  - **Eksponen (Exponent):** Mengatur skala bilangan.
  - **Mantisa (Significand):** Menyimpan bagian presisi dari bilangan.

### Ukuran Variabel

Ukuran variabel yang digunakan untuk menyimpan bilangan memengaruhi:

- **Presisi Perhitungan:**  
  Variabel bertipe presisi tunggal (32-bit atau 4-bytes) menyediakan jumlah bit yang lebih sedikit dibandingkan presisi ganda (64-bit atau 8-bytes), sehingga semakin besar kemungkinan terjadinya galat pembulatan.
  
- **Rentang Nilai:**  
  Ukuran bit menentukan seberapa besar atau kecil bilangan yang dapat direpresentasikan. Variabel 64-bit dapat menampung rentang nilai yang jauh lebih luas daripada 32-bit.
  
- **Efisiensi Memori dan Kecepatan:**  
  Penggunaan tipe data yang lebih besar (misalnya, 64-bit) mungkin memerlukan lebih banyak memori dan waktu proses, sehingga pemilihan tipe data harus disesuaikan dengan kebutuhan aplikasi.

### Contoh Suatu Representasi Bilangan (Standar IEEE 754)

Misalkan kita ingin merepresentasikan bilangan 6.5 (enam koma lima dalam bahasa Indonesia) menggunakan format floating-point 32-bit (presisi tunggal). Berikut adalah langkah-langkah pembagian komponen:

1. **Konversi ke Bilangan Biner:**  
   Bilangan 6.5 dalam desimal dikonversi ke biner sebagai berikut:
   - 6 dalam biner adalah 110.
   - 0.5 dalam biner adalah 0.1.  
     
   Jadi, 6.5 dalam biner menjadi:  
   \[
   6.5_{10} = 110.1_2.
   \]

2. **Normalisasi:**  
   Untuk format floating-point, kita menormalkan bilangan sehingga berbentuk:
   \[
   1.m \times 2^E.
   \]
   Kita dapat menuliskan 110.1 sebagai:
   \[
   110.1_2 = 1.101_2 \times 2^2.
   \]
   Di sini, \( m \) (mantisa) adalah 101 (setelah titik biner) dan \( E = 2 \).

3. **Penentuan Komponen Floating-Point:**
   - **Sign (Tanda):**  
     Karena 6.5 adalah bilangan positif, bit tanda adalah 0.
   - **Exponent (Eksponen):**  
     Dalam format IEEE 754 32-bit, eksponen disimpan dengan bias 127.  
     Eksponen sebenarnya \( E = 2 \), sehingga nilai yang disimpan adalah:
     \[
     E_{\text{stored}} = E + 127 = 2 + 127 = 129.
     \]
     Dalam biner, 129 ditulis sebagai:  
     \[
     129_{10} = 10000001_2.
     \]
   - **Mantisa (Significand):**  
     Mantisa disimpan dalam 23 bit. Karena bilangan sudah dinormalisasi (dengan bentuk \(1.101\)), angka 1 di depan titik biner tidak disimpan (dikenal sebagai "hidden bit"). Sehingga, mantisa yang disimpan adalah bagian setelah titik, yaitu:  
     \[
     101\,0000\,0000\,0000\,0000\,000_2.
     \]
     (ditambah nol hingga mencapai 23 bit).

4. **Rangkuman Representasi:**  
   Format 32-bit untuk 6.5 adalah:
   - **Sign:** 0  
   - **Exponent:** 10000001  
   - **Mantissa:** 10100000000000000000000

Dengan demikian, bilangan 6.5 dalam representasi floating-point 32-bit (IEEE 754) disusun berdasarkan komponen-komponen di atas, yang memungkinkan komputer untuk menyimpan dan mengoperasikan bilangan tersebut dengan efisiensi dan presisi yang terbatas sesuai format yang telah ditentukan.

### Machine Epsilon (ε) dan Kegunaannya
- **Definisi:**  
  Machine epsilon adalah nilai terkecil yang, ketika ditambahkan ke 1, menghasilkan bilangan berbeda dari 1 dalam sistem floating-point:
  
  \[
  1 + \varepsilon > 1.
  \]
  
- **Implikasi dan Kegunaan:**  
  \( \varepsilon \) menentukan batas ketelitian perhitungan dan memiliki peran penting, di antaranya:
  - **Kontrol Galat Pembulatan:**  
    Menjadi tolok ukur batas kesalahan pada setiap operasi aritmetika.
  - **Kriteria Iterasi:**  
    Digunakan dalam algoritma iteratif (misalnya, Newton-Raphson) sebagai kriteria penghentian; jika perbedaan antara iterasi kurang dari \( \varepsilon \), iterasi dianggap telah konvergensi.
  - **Validasi Hasil:**  
    Memastikan bahwa nilai perhitungan masih dalam batas ketelitian yang dapat diterima.

### Deret Taylor dalam Representasi Bilangan
Deret Taylor tidak hanya digunakan untuk mendekati fungsi non-linear, tetapi juga sangat berguna dalam pustaka pemrograman untuk representasi nilai-nilai irasional seperti \( e \), \( \pi \), \(\sin(x)\), dan \(\cos(x)\).
- **Definisi Deret Taylor:**  
  Fungsi \( f(x) \) dapat direpresentasikan sebagai:
  
  \[
  f(x) = f(a) + f'(a)(x-a) + \frac{f''(a)}{2!}(x-a)^2 + \frac{f'''(a)}{3!}(x-a)^3 + \cdots.
  \]
  
- **Aplikasi di Pustaka Pemrograman:**  
  Banyak algoritma menghitung nilai fungsi irasional dengan memotong deret Taylor setelah sejumlah suku tertentu untuk mencapai ketelitian yang diinginkan sehingga komputasi dapat dilakukan dengan efisien.

---

## 3. Analisis Galat (*Error*)

Metode numerik tidak terlepas dari kesalahan/galat (*error*). Dengan memahami analisis galat, kita dapat mencoba meminimalkan kesalahan yang mungkin ada dalam setiap metode numerik.

### Jenis-Jenis Galat dan Formulanya

#### a. Galat Pembulatan (Round-Off Error)
- **Definisi:**  
  Terjadi karena keterbatasan representasi bilangan dalam komputer. Saat mengkonversi bilangan desimal ke biner atau melakukan operasi aritmetika, nilai harus dibulatkan ke representasi terdekat.
  
- **Formula Matematis:**  
  Jika \( fl(x) \) adalah representasi floating-point dari \( x \), maka galat relatifnya:
  
  \[
  \delta_x = \frac{fl(x) - x}{x} \quad \text{dengan} \quad |\delta_x| \leq \varepsilon.
  \]

#### b. Galat Pemotongan (Truncation Error)
- **Definisi:**  
  Muncul saat deret tak hingga, seperti deret Taylor, dipotong setelah sejumlah suku tertentu sehingga suku-suku berikutnya diabaikan.
  
- **Formula Matematis:**  
  Misalnya, fungsi \( f(x) \) didekati dengan deret Taylor di sekitar \( a \):
  
  \[
  f(x) = \sum_{k=0}^{\infty} \frac{f^{(k)}(a)}{k!}(x-a)^k.
  \]
  
  Jika dipotong hingga orde \( n \):
  
  \[
  T_n(x) = \sum_{k=0}^{n} \frac{f^{(k)}(a)}{k!}(x-a)^k,
  \]
  
  maka sisa (galat pemotongan) diberikan oleh bentuk Lagrange:
  
  \[
  R_{n+1}(x) = \frac{f^{(n+1)}(\xi)}{(n+1)!}(x-a)^{n+1} \quad \text{dengan} \quad \xi \in [a,x].
  \]
  
  Secara asimtotik, \( R_{n+1}(x) = O((x-a)^{n+1}) \).

#### c. Galat Total (Total Error)
- **Definisi:**  
  Merupakan akumulasi dari galat pembulatan dan galat pemotongan:
  
  \[
  \text{Galat Total} = \text{Galat Pemotongan} + \text{Galat Pembulatan}.
  \]

#### d. Perambatan Galat (Error Propagation)
- **Definisi:**  
  Menggambarkan bagaimana kesalahan pada input atau operasi awal menyebar melalui perhitungan selanjutnya.
  
- **Formula Umum:**  
  Untuk fungsi \( f(x_1, x_2, \dots, x_n) \) dengan galat \( \delta x_i \) pada masing-masing variabel:
  
  \[
  \delta f \approx \sqrt{\left(\frac{\partial f}{\partial x_1} \delta x_1\right)^2 + \left(\frac{\partial f}{\partial x_2} \delta x_2\right)^2 + \cdots + \left(\frac{\partial f}{\partial x_n} \delta x_n\right)^2}.
  \]

### Contoh Kasus Analisis Galat

#### Contoh 1: Aproksimasi Deret Taylor untuk \( e^x \)
Aproksimasi \( e^x \) di sekitar \( x = 0 \) dengan tiga suku pertama:

\[
e^x \approx 1 + x + \frac{x^2}{2}.
\]

Galat pemotongan (sisa deret) diestimasikan sebagai:

\[
R_3(x) = \frac{e^\xi}{3!}x^3 \quad \text{dengan} \quad 0 \leq \xi \leq x.
\]

Untuk \( x \) kecil, galat aproksimasi adalah \( O(x^3) \).

#### Contoh 2: Perambatan Galat dalam Operasi Aritmetika
Untuk fungsi \( f(x, y) = x \cdot y \) dengan galat relatif \( \delta_x \) dan \( \delta_y \), galat relatif fungsi tersebut dapat dihitung dengan:

\[
\frac{\delta f}{f} \approx \sqrt{\left(\frac{\delta x}{x}\right)^2 + \left(\frac{\delta y}{y}\right)^2}.
\]

Jika \( \delta x/x \) dan \( \delta y/y \) sama-sama kecil (misalnya, sebesar \( \varepsilon \)), maka:

\[
\frac{\delta f}{f} \approx \sqrt{2}\varepsilon.
\]

---

### Notasi Big-O dan Estimasi Galat
Notasi Big-O digunakan untuk menyatakan orde galat yang tersisa setelah aproksimasi. Untuk deret Taylor, jika kita potong deret setelah orde \( n \), sisa galat adalah:

\[
R_{n+1}(x) = O((x-a)^{n+1}).
\]

Sebagai contoh, kita potong deret Taylor untuk \(\sin(x)\):

\[
\sin(x) = x - \frac{x^3}{6} + O(x^5),
\]

yang menunjukkan bahwa sisa galat berorde \( x^5 \) saat \( x \) mendekati 0. Secara umum, semakin tinggi nilai pangkat dalam notasi Big-O ini maka semakin tinggi ketelitian hasil metode numerik tersebut.