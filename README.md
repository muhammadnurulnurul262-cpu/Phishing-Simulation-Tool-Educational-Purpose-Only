# Phishing-Simulation-Tool-Educational-Purpose-Only
📸 phish_cam - Edukasi phishing berbasis kamera. Minta izin kamera → capture foto + login credentials → simpan ke file lokal. Hanya untuk pembelajaran keamanan siber. 🛡️

phish_cam/
├── index.html          (halaman phishing)
├── post.php            (backend capture)
├── captured/           (folder kosong, tempat foto)
├── creds.txt           (akan muncul setelah ada korban)
├── README.md           (dokumentasi utama)
└── screenshot/
    └── demo.jpg        (screenshot hasil capture - opsional)

    # 📸 phish_cam

**Phishing Simulation Tool — Educational Purpose Only**

Sebuah tools sederhana untuk memahami bagaimana teknik **phishing berbasis kamera** bekerja.  
Dibuat sebagai bahan pembelajaran keamanan siber, **bukan untuk disalahgunakan**.

> ⚠️ **Disclaimer:** Tools ini hanya untuk edukasi dan testing dengan izin.  
> Penulis tidak bertanggung jawab atas penyalahgunaan di luar tujuan edukasi.

---

## 🎯 Fitur

| Fitur | Deskripsi |
| :--- | :--- |
| 📷 **Camera Capture** | Meminta akses kamera korban via browser |
| 🔐 **Credential Harvesting** | Menangkap username & password yang diinput |
| 🎭 **Real-time Preview** | Korban melihat dirinya sendiri sebelum submit |
| 🔄 **Auto Redirect** | Setelah submit, korban diarahkan ke website asli |
| 💾 **Local Storage** | Hasil capture disimpan di folder `captured/` & `creds.txt` |

---

## 🧠 Cara Kerja (Teknis)

1. Korban membuka link yang dikirim attacker.
2. Halaman meminta izin akses kamera (menggunakan `navigator.mediaDevices.getUserMedia`).
3. Jika diizinkan, korban dapat melihat dirinya sendiri di preview video.
4. Korban mengisi form username & password.
5. Saat submit, JavaScript mengambil satu frame dari video.
6. Frame dikirim ke `post.php` bersama data formulir.
7. `post.php` menyimpan:
   - Foto ke folder `captured/`
   - Kredensial ke `creds.txt`
8. Korban diarahkan ke website asli (misal: google.com / facebook.com).
9. Attacker dapat melihat hasil capture kapan saja.

---

## 🔧 Instalasi & Penggunaan

### Prasyarat
- Termux (Android) atau PHP environment (Linux/Windows)
- Koneksi internet (untuk tunnel)

### Langkah-langkah

```bash
# 1. Clone repository
git clone https://github.com/username-lo/phish_cam.git
cd phish_cam

# 2. Jalankan server PHP
php -S localhost:8080

# 3. Buka terminal baru, buat tunnel (opsional, untuk akses publik)
cloudflared tunnel --url localhost:8080

# 4. Akses halaman via browser
#    - Lokal: http://localhost:8080
#    - Publik: https://xxxx.trycloudflare.com
