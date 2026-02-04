# Panduan Pemakaian

Dokumen ini menjelaskan langkah-langkah menjalankan proyek **SESIA4** menggunakan _virtual environment_ Python dan Jupyter Notebook/Lab.

---

## 1. Membuat Virtual Environment

Jalankan perintah berikut di **direktori root proyek (SESIA4/)**:

```bash
# macOS / Linux
python -m venv .venv

# Windows (PowerShell atau CMD)
python -m venv .venv
```

💡 Perintah ini akan membuat folder **.venv/** di dalam direktori **SESIA4/**. **Jangan menghapus folder ini**, karena berisi environment Python proyek.

---

## 2. Mengaktifkan Virtual Environment

### macOS / Linux

```bash
source .venv/bin/activate
```

### Windows (PowerShell)

```powershell
.\.venv\Scripts\Activate.ps1
```

### Windows (Command Prompt / CMD)

```cmd
.\.venv\Scripts\activate.bat
```

🔍 Setelah aktif, _prompt_ terminal akan berubah (misalnya menjadi **(.venv) $**), menandakan Anda sudah berada di dalam virtual environment.

---

## 3. Instal Dependensi

Pastikan file **requirements.txt** berada di root proyek (**SESIA4/**), lalu jalankan:

```bash
pip install -r requirements.txt
```

⚠️ Jika **requirements.txt** belum tersedia, Anda dapat membuatnya setelah semua library yang dibutuhkan terinstal di environment:

```bash
pip freeze > requirements.txt
```

---

## 4. Install `ipykernel` agar Jupyter Menggunakan Environment Ini

Agar Jupyter Notebook/Lab dapat menggunakan kernel dari virtual environment:

```bash
pip install ipykernel
python -m ipykernel install --user --name=.venv --display-name "Python (.venv)"
```

hasilnya di MacOS

```bash
Installed kernelspec .venv in /Users/fauzannurrachman/Library/Jupyter/kernels/.venv
```

Setelah perintah ini dijalankan, kernel akan terdaftar dan bisa dipilih di Jupyter.

### Tips penting (biar nggak nyasar kernel 👀)

- Selalu aktifkan .venv dulu sebelum install library

- Cek kernel aktif di notebook:
  - Kernel → Change Kernel

- Kalau mau hapus kernel lama:
  - jupyter kernelspec list
  - jupyter kernelspec uninstall nama_kernel

## 5. Membuka Jupyter Notebook (.ipynb) di Visual Studio Code

Jika Anda membuka file **.ipynb** langsung menggunakan **Visual Studio Code**, ikuti langkah berikut:

### A. Pastikan Ekstensi Terpasang

Pastikan ekstensi berikut sudah terinstal di VS Code:

- **Python**
- **Jupyter**

### B. Pilih Python Interpreter dari Virtual Environment

1. Buka folder proyek ) di VS Code
2. Tekan **Ctrl + Shift + P** (Windows/Linux) atau **Cmd + Shift + P** (macOS)
3. Pilih menu **Python: Select Interpreter**
4. Pilih interpreter dari virtual environment:
   - macOS / Linux: `./venv/bin/python`
   - Windows: `./venv/Scripts/python.exe`

### C. Pilih Kernel di Notebook

1. Buka file `*.ipynb`
2. Di pojok kanan atas notebook, klik **Select Kernel**
3. Pilih **Python Environments** → pilih interpreter **env / venv**

✅ Jika kernel sudah benar, nama environment (**env**) akan muncul di pojok kanan atas notebook.

💡 **Catatan Penting:**

- Jika kernel tidak muncul, pastikan environment sudah aktif dan `ipykernel` sudah terinstal (lihat langkah 4)
- VS Code **tidak selalu membutuhkan** perintah `python -m ipykernel install`, selama interpreter virtual environment dipilih dengan benar

---

---

## 📁 Struktur Folder (Referensi)

```bash
TASK4/
├── assets
│   ├── data_point_pluvial_flood_dataset.geojson
│   └── data_point_pluvial_flood_dataset.qmd
├── docs
│   ├── Data Task Sesi 4.md
│   └── Task Sesi 4_Introduction Python for Spatial Data.pdf
├── labs
│   ├── peta_flood_interaktif.html
│   └── Task Sesi 4_Introduction Python for Spatial Data.ipynb
├── README.md
└── requirements.txt
```
