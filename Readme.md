
# 🤖 gcommit on Ubuntu with Virtual Environment

Panduan ini menjelaskan cara menginstal dan menggunakan **gcommit**, alat bantu Git commit berbasis AI, di Ubuntu Linux menggunakan **Python virtual environment (venv)** dan alias di terminal untuk kemudahan akses.

---

## 📦 Prasyarat

Pastikan sistem Anda telah memiliki:

- **Python 3.x**
- **Git**

Jika belum, instal dengan:

```bash
sudo apt update
sudo apt install python3 python3-pip python3-venv git
```

---

## 🧪 1. Siapkan Virtual Environment (venv)

> Jika Anda **belum memiliki virtual environment**, ikuti langkah ini.  
> Jika sudah punya, **lewati ke langkah 2** dan sesuaikan dengan lokasi `venv` Anda.

```bash
# Buat folder khusus untuk menyimpan semua virtual environment (opsional)
mkdir -p ~/venvs

# Buat virtual environment baru bernama 'myenv'
python3 -m venv ~/venvs/myenv
```

---

## 🗂️ 2. Clone Folder Proyek dan Simpan gcommit

```bash
# Clone repository di directory yang anda mau
cd ~/project/gcommit-ubuntu
```

---

## 📥 3. Aktifkan venv dan Instal Dependensi

```bash
source ~/venvs/myenv/bin/activate
pip install GitPython google-generativeai
```

---

## 🔐 4. Tambahkan Google Gemini API Key

Untuk memungkinkan gcommit menggunakan AI Gemini, Anda harus memiliki API Key.

### Cara mendapatkan API Key:
1. Kunjungi [Google AI Studio](https://ai.google.com/studio)
2. Login dengan akun Google Anda.
3. Klik **"Get API key"** → **"Create API key in new project"**
4. Salin API Key yang diberikan (misalnya diawali dengan `AIza...`)

### Tambahkan API Key ke file aktivasi venv:

```bash
nano ~/venvs/myenv/bin/activate
```

Tambahkan baris berikut di akhir file:

```bash
export GOOGLE_API_KEY="ISI_DENGAN_API_KEY_ANDA"
```

Simpan dan keluar (`Ctrl+X`, lalu `Y`, lalu `Enter`)

---

## ⚙️ 5. Buat Alias `gcommit` di `.bashrc`

Agar Anda bisa menjalankan `gcommit` dari terminal di mana saja, tambahkan alias ke `.bashrc`.

```bash
nano ~/.bashrc
```

Tambahkan baris ini di akhir file:

```bash
alias gcommit='source ~/venvs/myenv/bin/activate && python3 ~/project/gcommit-ubuntu/gcommit.py'
```

> **Catatan**: Sesuaikan path jika Anda menggunakan lokasi `venv` atau proyek yang berbeda.

Kemudian aktifkan perubahan:

```bash
source ~/.bashrc
```

---

## 🚀 Cara Menggunakan gcommit

1. Buka terminal dan pindah ke folder proyek Git Anda:
   ```bash
   cd ~/Documents/nama-proyek-anda
   ```

2. Stage perubahan:
   ```bash
   git add .
   ```

3. Jalankan gcommit:
   ```bash
   gcommit
   ```

4. Ikuti instruksi di terminal:
   - Tekan `y` untuk menggunakan pesan commit yang disarankan
   - Tekan `n` untuk membatalkan

---

## 🧠 Tips

- Jika Anda ingin menggunakan `.env` untuk menyimpan API key daripada menulisnya di `activate`, Anda bisa memodifikasi `gcommit.py` untuk membaca dari `.env` menggunakan `python-dotenv`.
- Untuk multiple environment, buat alias lain seperti `gcommit-dev`, `gcommit-prod`, dsb.

---

## ✅ Struktur Folder yang Disarankan

```
.
├── project/
│   └── gcommit-ubuntu/
│       └── gcommit.py
└── venvs/
    └── myenv/
```

---

Happy committing! 🚀