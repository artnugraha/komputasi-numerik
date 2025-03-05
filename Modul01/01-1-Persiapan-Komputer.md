Dalam pelajaran ini, kita akan menginstalasi lingkungan pemrograman Python dengan *virtual environment* yang menyertakan pustaka NumPy, SciPy, SymPy, dan Matplotlib. Editor yang akan digunakan adalah VS Code dengan *extension* yang menunjang penyuntingan dalam *Jupyter Notebook* (format berkas `.ipynb`) serta *Markdown* (format berkas `*.md`). Petunjuk instalasi lengkap di bawah ini diberikan untuk sistem operasi Windows. 

Selain instalasi perangkat lunak, kita akan belajar secara ringkas prosedur pengiriman berkas-berkas (*files*) yang kita edit di komputer lokal kita ke server repositori seperti [GitHub](https://github.com) dengan menggunakan perintah `git`.

---

### Langkah 1: Instalasi Python via Microsoft Store
1. **Buka Microsoft Store**:
   - Tekan tombol **Start**, cari **Microsoft Store**, dan buka aplikasinya.

2. **Cari Python di Microsoft Store**:
   - Di dalam Microsoft Store, ketik "Python" pada panel pencarian.
   - Pilih **Python 3.x** (saran: Python 3.11) dari hasil pencarian.

3. **Instalasi Python**:
   - Klik **Get** atau **Install** untuk mengunduh dan menginstal Python dari Microsoft Store.
   - Setelah instalasi selesai, Python akan tersedia di sistem kita.

4. **Verifikasi Instalasi Python**:
   - Buka **Command Prompt** dan ketik perintah berikut untuk memeriksa apakah Python telah terinstalasi dengan benar:
     ```bash
     python --version
     ```
   - Jika berhasil, kita akan melihat versi Python yang baru saja dipasang. Jika perintah tersebut tidak berhasil dieksekusi, bisa mencoba langkah alternatif instalasi Python dengan mengunduh penginstalasi dari situs pengembang Python.

### Langkah 1 Alternatif: Instalasi Python dari Situs Web Pengembang
1. **Unduh Penginstalasi Python**
   - Kunjungi [situs resmi pengembang Python](https://www.python.org/downloads/windows/) dan unduh Python (saran: Python 3.13.2 versi stabil termutakhir atau Python 3.11.11) untuk Windows.

2. **Instalasi Python**
   - Buka *installer* Python dan pilih opsi-opsi *default*-nya, terutama terkait pilihan menambahkan Python ke dalam PATH harus dipastikan disertakan.

3. **Verifikasi Instalasi Python**:
   - Buka **Command Prompt** dan ketik
     ```bash
     python --version
     ```
   - Jika berhasil, kita akan melihat versi Python yang baru saja dipasang.


---

### Langkah 2: Instalasi Visual Studio Code (VS Code)
1. **Unduh VS Code**: 
   - Kunjungi [situs resmi VS Code](https://code.visualstudio.com/Download) dan unduh versi Windows.

2. **Instalasi VS Code**:
   - Jalankan file unduhan dan ikuti langkah-langkah instalasi.
   - Dalam proses instalasi, pastikan untuk memilih opsi berikut:
     - **Add to PATH** (menambahkan VS Code ke PATH).
     - **Register Code as an editor for supported file types**.
     - **Install 'code' command in PATH** (untuk membuka VS Code dari terminal).

3. **Verifikasi Instalasi VS Code**: 
   Setelah instalasi, verifikasi VS Code dengan membukanya melalui Start Menu. Jika sudah bisa dibuka, boleh ditutup lagi.

---

### Langkah 3: Instalasi Git Bash
1. **Unduh Git untuk Windows**: 
   - Kunjungi [situs Git](https://git-scm.com/download/win) dan unduh versi Windows.

2. **Instalasi Git**:
   - Jalankan installer dan ikuti langkah-langkah instalasi.
   - Pilih opsi untuk menginstalasi Git Bash.
   - Pilih opsi *default* selama proses instalasi jika kita tidak ingin pusing.

3. **Verifikasi Git Bash**: 
   Setelah Git terinstal, verifikasi Git Bash sudah terinstalasi dengan membuka Git Bash melalui Start Menu. Jika sudah bisa dibuka, boleh ditutup lagi.

---

### Langkah 4: Instalasi Python dan Jupyter Extensions di VS Code
1. **Instalasi Python Extension**:
   - Buka kembali VS Code dan di dalamnya cek menu **Extensions** yang secara *default* ada di panel sebelah kiri vertikal (coba cek satu per satu), atau bisa juga dengan langsung menekan `Ctrl + Shift + X`.
   - Cari **Python Extension Pack** (*from Don Jayamanne*) dan klik **Install**.   
   - Setelah Python Extension terinstalasi, cari **Jupyter** (*from Microsoft*) dan pilih **Install**. Dengan ekstensi ini, kita nanti dapat menjalankan berbagai Jupyter notebook yang dibuat dalam perkuliahan, secara langsung di dalam VS Code.

---

### Langkah 5: Memilih Git Bash sebagai terminal *default*

1. **Buka Ulang VS Code**: 
   - Setelah instalasi Extensions, ada baiknya kita *refresh* atau *reload* VS Code dengan cara keluar (tutup) dulu kemudian masuk (buka) lagi VS Code.

2. **Pilih Terminal Git Bash di VS Code**:
   - Di VS Code, buka terminal dengan menekan `Ctrl + ~` (atau pilih **Terminal > New Terminal** dari menu).
   - Di bagian panel terminal, klik pada *dropdown* (arah panah bawah) yang menunjukkan terminal *default* (misalnya, PowerShell atau Command Prompt), kemudian pilih **Git Bash**. 
   ![Pilihan Terminal](../img/vscode-terminal-selection.png)
   - Ilustrasi di bawah ini untuk komputer yang menggunakan Linux yang sudah *default*-nya Bash (label 1).
   ![Default Terminal](../img/vscode-terminal-profile.png)
   Jika Bash belum menjadi *default*, perlu klik **Select Default Profile** (label 2), dan pilih **Git Bash** dari daftar. 
---

### Langkah 6: Instalasi *Virtual Environment* (venv)

1. **Pilih Folder Kerja Aktif**
   - Di VS Code, dari menu `File`, pilih `Open Folder` dan buat Folder baru untuk pelajaran ini, misalnya diberi nama `kelas-teko`. 

2. **Buat Virtual Environment (venv)**:
   - Klik ikon berupa ular di panel sebelah kiri yang merupakan Python Environment Manager. Dari sana, di bawah bagian `Global Environments` semestinya kita dapat melihat opsi `Venv`. 
   ![Venv](../img/vscode-venv.png)
   - Klik tanda + dengan kursor mouse untuk `Create Environment`. Kita akan diminta memilih `workspace` untuk `environment` ini dan Python *interpreter*  yang sesuai. Bisa pilih versi Python yang berasal dari instalasi Python sebelumnya. 
   ![Venv Creation](../img/vscode-venv-create.png)
   - Tunggu beberapa saat sampai inisialisasi Python Environment selesai.

3. **Konfigurasi Virtual Environment**:
   - Setelah *virtual environment* dibuat, kita dapat melihatnya sebagai salah satu opsi di bawah panah Global Environments dan `Venv`. Aktifkan `Venv` ini dengan klik dua gambar ikon yang tiba-tiba muncul, yakni (1) `Open in Terminal` (ikon terminal) dan (2) `Set as active workspace interpreter` (ikon bintang).
   ![Venv Terminal](../img/vscode-venv-term.png)
   - Jika berhasil, terminal Git Bash kita akan menunjukkan bahwa venv aktif dengan melihat `(venv)` di awal prompt.

---

### Langkah 7: Instalasi Paket yang Dibutuhkan dalam Virtual Environment

1. **Instalasi Paket dengan `pip`**:
   - Sekarang, dengan venv aktif di Git Bash Terminal di dalam VS Code kita, lakukan instalasi pustaka yang akan kita butuhkan, meliputi **NumPy**, **SciPy**, **SymPy**, **Matplotlib**, dan **Jupyter**, menggunakan perintah `pip`. Baris perintah di bawah ini dapat disalin ke Terminal Bash.
     ```bash
     pip install numpy scipy sympy matplotlib jupyter
     ```

2. **Verifikasi Instalasi**:
   - Kita dapat memverifikasi bahwa pustaka telah diinstalasi dengan menjalankan:
     ```bash
     pip list
     ```
   - Ini akan menampilkan semua pustaka yang telah diinstalasi di dalam *virtual environment* kita.

---

### Langkah 8: Menggunakan Virtual Environment di VS Code

1. **Pilih Interpreter Python di VS Code**:
   - Setelah *virtual environment* (venv) aktif, tekan `Ctrl + Shift + P` di VS Code untuk membuka **Command Palette**.
   - Ketik dan pilih **Python: Select Interpreter**.
   - Pilih interpreter Python yang ada di dalam folder `venv`. kita akan melihat sesuatu seperti `./venv/Scripts/python` pada daftar pilihan.

2. **Verifikasi di VS Code**:
   - Pastikan bahwa interpreter Python yang aktif di VS Code adalah interpreter dari *virtual environment* (venv) yang baru saja kita buat.
   - Coba buat atau buka file Python `.py` maupun Jupyter Notebook `.ipynb` untuk memastikan semuanya berjalan dengan baik.

---

### Langkah 9: Menjalankan Jupyter Notebook di VS Code

1. **Buat atau Buka Notebook**:
   - Di dalam VS Code, kita bisa membuat file baru dengan ekstensi `.ipynb` untuk membuat Jupyter Notebook baru, atau buka notebook yang sudah ada.
   
2. **Pilih Kernel Jupyter**:
   - Setelah membuka file `.ipynb`, pilih kernel Jupyter yang terhubung dengan *virtual environment* (venv). Pilih **Python Kernel** yang sesuai dari pilihan kernel yang muncul di bagian atas notebook.
   
3. **Mulai Menulis dan Menjalankan Kode**:
   - Sekarang kita dapat menulis dan menjalankan kode Python di Jupyter Notebook di dalam VS Code dengan menggunakan pustaka yang telah diinstalasi (NumPy, SciPy, SymPy, Matplotlib, Jupyter).

---

## Berinteraksi dengan Git dan GitHub

GitHub merupakan salah satu situs web yang menyediakan repositori (tempat penyimpanan) gratis bagi penggunanya untuk berbagi berkas, terutama kode dan data secara terbuka kepada publik maupun secara tertutup kepada kolaborator dalam komunitas tertutup. Proses berbagi berkas ini dapat dilakukan melalui perintah-perintah `git`. 

Untuk keperluan pelajaran kita, ada beberapa konfigurasi yang mesti dilakukan. Ini dimulai dari membuat repositori di situs web GitHub,  mengatur akses pengguna dan "token" interaksi antara komputer lokal (laptop kita misalnya) dengan server GitHub, hingga sinkronisasi repositori di komputer lokal kita dengan server GitHub.  

---

### Langkah 1: Pastikan sudah punya akun GitHub dan membuat repositori

1. **Akses situs web GitHub**:
   - Buka situs web https://github.com
   - Login dengan akun masing-masing. Jika belum punya akun GitHub, buat dulu dengan mengikuti petunjuk yang ada di situsnya.

2. **Buat repositori pelajaran jika belum punya**:
   - Pilih tab `Repositories` atau menu `Your Repositories` dari profil pengguna kita, biasanya bisa diakses di **pojok kanan atas** jika membuka di versi *desktop*.
   - Klik tombol `New`, biasanya berlatar belakang warna hijau untuk membuat repositori baru. 
   - Pada bagian `Repository name` bisa tulis nama repositori yang kita inginkan, misalnya `kelas-teko`.
   - Berikan `Description` ringkas seperti: "Tempat menaruh tugas pelajaran komputasi numerik" (ditulis tanpa tanda petik).
   - Sifat repositori dapat dipilih sebagai repositori `Private` untuk keperluan pelajaran ini.
   - Opsi lainnya boleh dikerjakan maupun tidak. Misalnya, jika kita ingin ada berkas `README` sebagai awalan pengisi repositori, kita dapat centang opsi **Add a Readme file**.
   - Kalau sudah puas, klik `Create repository`

3. **Menambah kolaborator**
   - Pada langkah berikutnya, kolaborator kita dapat ditambahkan sebagai pengakses repositori dengan memilih `Invite collaborators` ketika ada tampilan `Add collaborators to this repository` 
   - Tergantung dari konfigurasi akun GitHub kita, kadang akan diminta untuk login kembali. Setelah itu, kita bisa `Add people` sebagai kolaborator dan mengetik nama akun yang perlu ditambah. Untuk pelajaran ini kita dapat mengundang anggota kelompok masing-masing dan akun `artnugraha` (atau email art.nugraha@gmail.com) sebagai kolaborator.

---

### Langkah 2: Buat `token` untuk interaksi komputer lokal dan GitHub

1. **Cari Developer Settings**:
   - Dimulai dari klik gambar profil GitHub kita di pojok kanan atas situs GitHub, ada pilihan `Settings`.
   - Setelah itu, akan ada beberapa menu yang berpindah ke panel sebelah kiri, *scroll* ke bawah sebelah kiri akan tampak `Developer settings`.

2. **Pembuatan token**:
   - Pilih `Personal access tokens` &rarr; `Tokens (classic)`.
   - Agak geser ke sebelah kanan, ada pilihan `Generate new token` yang bisa diklik. Kemudian, pilih `Generate new token (classic)`.
   - `Note` atau catatan dapat diisi bebas, misalnya "Token untuk kelas teko" (tanpa tanda kutip). 
   - `Expiration` atau masa berlaku disarankan untuk diatur `Custom` 1 tahun dengan menulis tanggal setahun setelah hari ini dalam format mm/dd/yyyy (misal: 03/05/2026 artinya 5 Maret 2026)
   - `Select scopes` maksudnya adalah memilih cakupan `token` ini, kita bisa centang semuanya saja untuk kemudahan (walau tidak terlalu aman, kita bukan *programmer* terkenal yang diincar *hacker* yang jahat)
   - Setelah memilih semua `scopes` yang sesuai, di bagian bawah kita bisa klik tombol `Generate token` (biasanya berlatar belakang hijau).

3. **Token harus langsung disimpan**:
   - Begitu `token` muncul dari langkah sebelumnya, kita harus segera menyalinnya ke tempat yang aman. Contoh `token` semacam ini:
      ```
      ghp_92OcO9FyFzYmfmW5LZYzGO6S3N6Voq1UjyGr
      ```
      
---

### Langkah 3: Buat berkas konfigurasi Git

1. **Akses folder `home` atau `user` masing-masing**:
   - Dari VS Code, kita dapat membuka folder akun pengguna kita masing-masing melalui menu `File` &rarr; `Open Folder`.
   - Standar di Windows biasanya folder pengguna beralamat di `C:\Users\nama-pengguna`. Cari folder semacam itu dan kalau sudah ketemu bisa klik `Select` serta `Open`.
   
2. **Buat dua berkas (*files*) baru untuk konfigurasi Git**:
   - Dari panel Explorer di VS Code, kita dapat memilih `New file ` untuk membuat berkas baru yang berada dalam folder `C:\Users\nama-pengguna`. 
   - Dua berkas baru yang perlu dibuat harus memiliki nama yang tidak boleh keliru sedikitpun huruf demi hurufnya, yakni
     - `.gitconfig`
     - `.git-credentials`
     
     Perhatikan bahwa kedua berkas tersebut diawali tanda titik (`.`) yang bukan merupakan suatu kekeliruan, memang begitu penamaannya. 

3. **Isian `.gitconfig`**:
   - Pada Explorer VS Code, kita klik `.gitconfig` yang sudah dibuat untuk kita edit langsung dengan isian seperti di bawah.

      ```yaml
      [user]
         name = Nama Lengkap Masing Masing
         email = alamat@penyediaemail.com
      [credential]
         helper = store
      [core]
         autocrlf = input
      ```
   - Bagian `name` dan `email` sesuaikan dengan punya masing-masing. Kemudian, simpan (*save*) `.gitconfig`.

4. **Isian `.git-credentials`**:
   - Pada Explorer VS Code, klik `.gitconfig` yang sudah dibuat untuk kita edit langsung dengan format seperti di bawah.

      ```yaml
      https://usernamegithub:token@github.com
      ```
   - Misal `usernamegithub` adalah `artnugraha` dengan token `ghp_92OcO9FyFzYmfmW5LZYzGO6S3N6Voq1UjyGr`, isian `.gitconfig` ini menjadi:

      ```yaml
      https://artnugraha:ghp_92OcO9FyFzYmfmW5LZYzGO6S3N6Voq1UjyGr@github.com
      ```
   - Jangan lupa simpan (*save*) berkas tersebut.

---

### Langkah 4: Klon dan Sinkronisasi Repositori

1. **Buka ulang folder `kelas-teko`**:
   - Asumsikan kita sudah membuat folder `kelas-teko` di `C:\Users\nama-pengguna\kelas-teko`, kita bisa buka ulang dengan mengakses menu `File` &rarr; `Open Folder` di VS Code dan mengarahkan ke alamat folder tersebut.
   - Di dalam folder ini kita akan melakukan klon repositori dari situs GitHub.

2. **Buka Terminal dengan `venv` yang sesuai**:
   - Klik ikon berupa ular di panel sebelah kiri yang merupakan Python Environment Manager. Dari sana, di bawah bagian `Global Environments` semestinya kita dapat melihat opsi `Venv`.
   - Aktifkan `Venv` ini dengan klik dua gambar ikon yang tiba-tiba muncul, yakni (1) `Open in Terminal` (ikon terminal) dan (2) `Set as active workspace interpreter` (ikon bintang).

3. **Operasi `git` dalam terminal**
   - Di dalam terminal, kita dapat mengetik beberapa perintah penting `git` untuk klon dan sinkronisasi repositori.
   - Untuk klon repositori kita yang sudah dibuat di GitHub, misal beralamat di https://github.com/usernamegithub/kelas-teko, kita tulis satu baris perintah   
      ```bash
      git clone https://github.com/usernamegithub/kelas-teko
      ```
   - Setelah eksekusi perintah di atas, kita akan mendapati ada folder baru muncul di Explorer VS Code dengan nama `kelas-teko`. Untuk membedakan dari folder utama yang mungkin namanya terlanjur sama `kelas-teko`, kita bisa ganti nama (`Rename`) folder yang baru muncul ini dengan cara klik kanan dan pilih `Rename` untuk foldernya menjadi `GitHub-Tugas`. Ini dengan asumsi bahwa proses sinkronisasi berkas pelajaran hanya akan dilakukan di dalam folder tersebut.
   - Setelah penggantian nama folder, kita bisa membuat contoh berkas baru di dalamnya, misalnya `nguliq.ipynb`. Ini adalah berkas Jupyter Notebook yang akan kita sinkronisasi ke repositori GitHub.
   - Di dalam `nguliq.ipynb`, kita bisa tulis beberapa baris kode Python. Misalnya:
      ```python
      import numpy as np
      y = np.sin(np.pi/2)
      print(y)
      ```
   - Simpan (`Save`) berkas tersebut dan sekarang kita beralih ke terminal.
   - Dalam Terminal, kita perlu masuk dulu ke folder `GitHub-Tugas` dengan perintah
      ```bash
      cd GitHub-Tugas
      ```
      atau nama folder lain yang tadi kita lakukan perubahan namanya saat mengakses folder tersebut. Hati-hati dengan ukuran huruf besar-kecilnya.

   - Setelah itu, tambahkan berkas `nguliq.ipynb` ke dalam rangkaian sinkronisasi via perintah-perintah `git` berikut ini.
      
      ```bash
      git add nguliq.ipynb
      ```
      ```bash
      git commit -m 'tugas ke-0'
      ```

      ```bash
      git push
      ```
   - Tiga baris perintah di atas akan 'mengirimkan' berkas `nguliq.ipynb` versi lokal untuk sinkronisasi ke situs web github.com yang beralamat pada repositori yang telah kita buat sebelumnya (misal: https://github.com/usernamegithub/kelas-teko).
   - Ketika kita diminta untuk berbagi kode ke repositori oleh kolaborator, kita dapat melakukan 3 rangkaian perintah yang sama seperti di atas, tinggal mengganti berkas yang sesuai dan pesan `commit` yang menunjukkan catatan revisi.
   - Selain tiga rangkaian perintah di atas, satu lagi perintah `git` paling populer yang penting diketahui adalah
   
      ```bash
      git pull
      ```
   - Perintah `git pull` ini bahkan biasanya dilakukan paling duluan (sebelum 3 rangkaian perintah sinkronisasi tadi) jika kita baru "bangun tidur" dan baru membuka komputer di waktu kerja berikutnya. Siapa tahu kolaborator kita sudah mengerjakan sesuatu di repositori, kita perlu 'menarik' hasil editan kolaborator kita itu dan menggabungkannya ke versi lokal kita.
   - Untuk belajar lebih lengkap seputar Git, kita dapat mengakses tutorial yang komprehensif seputar Git bagi pemula di situs [Software Carpentry](https://swcarpentry.github.io/git-novice/instructor/index.html)

   