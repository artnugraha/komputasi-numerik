Dalam mata kuliah ini, peserta perlu menginstalasi lingkungan pemrograman Python dengan *virtual environment* yang menyertakan pustaka NumPy, SciPy, SymPy, dan Matplotlib. Editor yang akan digunakan adalah VS Code dengan *extension* yang menunjang penyuntingan dalam *Jupyter Notebook* (format berkas `.ipynb`) serta *Markdown* (format berkas `*.md`). Petunjuk instalasi lengkap di bawah ini diberikan untuk sistem operasi Windows. 

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
   - Jika berhasil, kita akan melihat versi Python yang baru saja dipasang.

---

### Langkah 2: Instal Visual Studio Code (VS Code)
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
   - Di VS Code, dari menu `File`, pilih `Open Folder` dan buat Folder baru untuk bekerja sepanjang mata kuliah ini, misalnya diberi nama `kelas-teko`. 

2. **Buat Virtual Environment (venv)**:
   - Klik ikon berupa ular di panel sebelah kiri yang merupakan Python Environment Manager. Dari sana, di bawah bagian `Global Environments` semestinya kita dapat melihat opsi `Venv`. 
   ![Venv](../img/vscode-venv.png)
   - Klik tanda + dengan kursor mouse untuk `Create Environment`. Kita akan diminta memilih `workspace` untuk `environment` ini dan Python *interpreter*  yang sesuai. Bisa pilih versi Python yang berasal dari instalasi Python sebelumnya. 
   ![Venv Creation](../img/vscode-venv-create.png)
   - Tunggu beberapa saat sampai inisialisasi Python Environment selesai.

3. **Konfigurasi Virtual Environment**:
   - Setelah virtual environment dibuat, kita dapat melihatnya sebagai salah satu opsi di bawah panah Global Environments dan `Venv`. Aktifkan `Venv` ini dengan klik dua gambar ikon yang tiba-tiba muncul, yakni (1) `Open in Terminal` (ikon terminal) dan (2) `Set as active workspace interpreter` (ikon bintang).
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
   - Kita dapat memverifikasi bahwa pustaka telah diinstal dengan menjalankan:
     ```bash
     pip list
     ```
   - Ini akan menampilkan semua pustaka yang telah diinstal di dalam virtual environment kita.

---

### Langkah 8: Menggunakan Virtual Environment di VS Code

1. **Pilih Interpreter Python di VS Code**:
   - Setelah virtual environment (venv) aktif, tekan `Ctrl + Shift + P` di VS Code untuk membuka **Command Palette**.
   - Ketik dan pilih **Python: Select Interpreter**.
   - Pilih interpreter Python yang ada di dalam folder `venv`. kita akan melihat sesuatu seperti `./venv/Scripts/python` pada daftar pilihan.

2. **Verifikasi di VS Code**:
   - Pastikan bahwa interpreter Python yang aktif di VS Code adalah interpreter dari virtual environment (venv) yang baru saja kita buat.
   - Coba buat atau buka file Python `.py` maupun Jupyter Notebook `.ipynb` untuk memastikan semuanya berjalan dengan baik.

---

### Langkah 9: Menjalankan Jupyter Notebook di VS Code

1. **Buat atau Buka Notebook**:
   - Di dalam VS Code, kita bisa membuat file baru dengan ekstensi `.ipynb` untuk membuat Jupyter Notebook baru, atau buka notebook yang sudah ada.
   
2. **Pilih Kernel Jupyter**:
   - Setelah membuka file `.ipynb`, pilih kernel Jupyter yang terhubung dengan virtual environment (venv). Pilih **Python Kernel** yang sesuai dari pilihan kernel yang muncul di bagian atas notebook.
   
3. **Mulai Menulis dan Menjalankan Kode**:
   - Sekarang kita dapat menulis dan menjalankan kode Python di Jupyter Notebook di dalam VS Code, dengan menggunakan pustaka yang telah diinstal (NumPy, SciPy, SymPy, Matplotlib, Jupyter).
