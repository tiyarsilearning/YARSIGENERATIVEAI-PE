# MODUL PRAKTIKUM PERTEMUAN 7
**Mata Kuliah:** Pemanfaatan AI Generative untuk Pengembangan Aplikasi 

---

## A. Nama Praktikum
Menyusun Prompt Elements, XML Tags, dan Prompt Template pada Foundation Model (Qwen) 

---

## B. Target Kompetensi
- Mahasiswa mampu membuat akun, mengelola Access Token, dan mengambil ID Foundation Model dari platform Hugging Face.
- Mahasiswa mampu mengonfigurasi lingkungan komputasi Google Colab berbasis GPU (T4) serta menjalankan Foundation Model Qwen untuk menghasilkan respons teks (inference). 
- Mahasiswa mampu Menyusun Prompt Elements menggunakan Model lain yaitu Gamma (Google Gemma) secara mandiri di Google Colab dengan mengadaptasi alur kerja pemanggilan model dari praktikum. 

---

## C. Alat/Tools yang Digunakan
- **Google Colaboratory** (https://colab.research.google.com) dengan akselerator Hardware T4 GPU. 
- **Akun Hugging Face** (https://huggingface.co) sebagai repositori penyedia Foundation Model. 
- **Framework/Library Python:** `torch`, `transformers`, `accelerate`, dan `huggingface_hub`. 
- **Foundation Model:**
  - **Praktikum Kelas:** `Qwen/Qwen2.5-1.5B-Instruct` (https://huggingface.co/Qwen/Qwen2.5-1.5B-Instruct) 
  - **Tugas Mandiri:** `google/gemma-2-2b-it` (https://huggingface.co/google/gemma-2-2b-it) atau repositori mirror `unsloth/gemma-2-2b-it` (https://huggingface.co/unsloth/gemma-2-2b-it) 

---

## D. Langkah-Langkah Praktikum (Tutorial Hugging Face & Google Colab)

### Tahap 1: Membuat Akun dan Mengambil Access Token di Hugging Face
Untuk mengunduh model dari Hugging Face ke Google Colab, kita tidak mengunduh file berukuran gigabyte ke laptop, melainkan memanggil ID Model secara langsung melalui kode Python di Google Colab menggunakan Access Token. 

#### Daftar / Login Akun:
1. Buka https://huggingface.co. 
2. Klik Sign Up di pojok kanan atas untuk membuat akun baru (lakukan verifikasi email), atau klik Login jika sudah memiliki akun.

#### Membuat Access Token (hf_...):
1. Setelah login, buka halaman pengaturan token di tautan: https://huggingface.co/settings/tokens. 
2. Klik tombol **+ Create new token**. 
3. Pilih tipe token **Read** (tab di bagian atas). 
4. Pada kolom **Token name**, ketik nama bebas (contoh: `praktikum-colab`). 
5. Gulir ke paling bawah dan klik **Create token**. 
6. Akan muncul kode token yang diawali dengan huruf `hf_`.  
   Contoh bentuk kode token: `hf_aBcDeFgHiJkLmNoPqRsTuVwXyZ12345678`  
7. Klik tombol **Copy** dan simpan kode tersebut di Notepad/Catatan pribadi Anda (kode ini hanya ditampilkan satu kali). 

---

### Tahap 2: Cara Mencari dan Menyalin ID Model di Hugging Face
1. Buka menu **Models** di bagian atas situs Hugging Face (https://huggingface.co/models).
2. Ketik nama model pada kolom pencarian, misalnya: `Qwen2.5-1.5B-Instruct`.
3. Klik nama model `Qwen/Qwen2.5-1.5B-Instruct` dari daftar hasil pencarian. 
4. Di bagian kiri atas halaman model, klik ikon **Copy** di sebelah teks `Qwen/Qwen2.5-1.5B-Instruct`. Teks dengan format `Pembuat/Nama-Model` inilah yang disebut **ID Model** dan nantinya dimasukkan ke dalam variabel Python di Google Colab. 

#### Khusus untuk Tugas Model Gamma (google/gemma-2-2b-it):
1. Buka tautan https://huggingface.co/google/gemma-2-2b-it. 
2. Jika muncul kotak **Acknowledge license**, klik tombol tersebut dan setujui syarat penggunaannya agar token Anda diizinkan mengakses model tersebut. 
3. Apabila akun Anda belum mendapatkan izin lisensi, Anda dapat menggunakan ID model alternatif yang terbuka langsung tanpa lisensi tambahan, yaitu: `unsloth/gemma-2-2b-it` (https://huggingface.co/unsloth/gemma-2-2b-it). 

---

### Tahap 3: Menjalankan Praktikum Model Qwen di Google Colab
1. Unduh file `Praktikum5_Prompt_Elements.ipynb` lalu buka di Google Colab. 
2. Aktifkan GPU terlebih dahulu melalui menu **Runtime** -> **Change runtime type** -> pilih **T4 GPU** -> **Save**. 
3. Jalankan sel pemeriksaan GPU dan instalasi library (`transformers`, `accelerate`, `huggingface_hub`). 
4. Jalankan sel `login()`. Saat muncul kotak input Token, tempelkan (*paste*) kode token `hf_...` milik Anda lalu tekan Enter / klik tombol Login. 
5. Jalankan sel pengunduhan Tokenizer dan Model `Qwen/Qwen2.5-1.5B-Instruct`, lalu amati waktu muat dan kapasitas VRAM yang digunakan. 
6. Jalankan fungsi inference `jalankan_qwen()` pada 3 variasi struktur elemen dan catat hasilnya. 

---

## E. Tugas Praktikum
Setelah mengikuti praktikum menggunakan model Qwen di kelas, mahasiswa ditugaskan untuk menjalankan Foundation Model lain yaitu Gamma (Google Gemma) dengan ketentuan: 
1. Unduh file template tugas bernama `Tugas_5_Prompt_Elements.ipynb`.
2. Lengkapi seluruh sel kode yang kosong pada template tersebut dengan mengacu pada struktur kode di modul praktikum Qwen. 
3. Gunakan model `google/gemma-2-2b-it` atau `unsloth/gemma-2-2b-it` dari Hugging Face. 
4. Uji Model dengan 3 Variasi Struktur Elemen Prompt menggunakan Model Gemma
5. Isi tabel pengamatan perbandingan performa (pemakaian memori VRAM, waktu eksekusi, dan hasil jawaban) antara model Qwen dan model Gamma. 

---

## F. Format Laporan dan Pengumpulan

### File yang Dikumpulkan di LMS Layar:
- **File Notebook Tugas (.ipynb):** Pastikan seluruh sel kode telah dijalankan (Run) hingga seluruh output teks tampil lengkap di bawah setiap sel. Unduh file melalui menu **File** -> **Download** -> **Download .ipynb**.  
  *Format penamaan:* `Tugas_5_[NPM]_[NamaLengkap].ipynb`
- **File Laporan Praktikum (.pdf):** Berisi identitas mahasiswa (Nama dan NPM), screenshot hasil eksekusi kode praktikum (Qwen) dan tugas (Gamma), serta tabel pengamatan dan kesimpulan.  
  *Format penamaan:* `Laporan_P5_[NPM]_[NamaLengkap].pdf`

---

## Rubrik Penilaian

| No | Komponen Penilaian | Bobot Maksimal | 100 (Selesai & Tepat) | 50 (Kurang Lengkap / Error Sebagian) | 0 Poin (Tidak Dikerjakan / Gagal) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | Load Tokenizer & Model Gamma | 30 Poin | 30 Poin: Berhasil memuat tokenizer dan bobot model Gamma ke GPU T4 tanpa error serta menampilkan waktu muat dan pemakaian VRAM. | 15 Poin: Kode pemanggilan model sudah ditulis tetapi masih menghasilkan error saat dijalankan atau tidak menggunakan GPU. | 0 Poin: Sel kode dibiarkan kosong. |
| 2 | Pembuatan Fungsi Inference (jalankan_gamma) | 25 Poin | 25 Poin: Fungsi inference ditulis dengan tepat (menggunakan apply_chat_template, menghitung durasi waktu dan puncak VRAM) serta berjalan lancar. | 12 Poin: Fungsi dibuat namun pencatatan waktu/VRAM tidak disertakan atau terdapat kesalahan parameter. | 0 Poin: Fungsi tidak dibuat / kosong. |
| 3 | Penyusunan Prompt XML Tags & Prompt Template | 25 Poin | 25 Poin: Berhasil Menyusun Prompt menggunakan XML tags lengkap [\<tone\>, \<context\>, \<instructions\>, \<co3xnstraints\>, \<response_format\>, \<input_data\>, \<task\>] serta membuat Reusable Prompt Template berformat variable yang diuji pada sampel berita. | 13 Poin: Hanya Menyusun 1 atau 2 dari ketiga variasi struktur elemen prompt | 0 Poin: Tidak ada prompt yang berhasil dijalankan. |
| 4 | Tabel Pengamatan, Laporan PDF & Format File | 20 Poin | 20 Poin: Tabel perbandingan Qwen vs Gamma dan kesimpulan terisi lengkap, serta mengumpulkan kedua file (.ipynb dan .pdf) sesuai format nama. | 10 Poin: Tabel pengamatan/kesimpulan kurang lengkap atau hanya mengumpulkan salah satu dari dua file yang diwajibkan. | 0 Poin: Tidak melampirkan analisis dan format pengumpulan tidak sesuai. |
