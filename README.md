# TKA PPLG — Media Pembelajaran Interaktif

Website statis untuk latihan TKA Pengembangan Perangkat Lunak dan Gim (PPLG) SMK.

## Fitur
- **Level 1:** soal 1–30 berdasarkan teks yang diberikan pengguna.
- **Level 2:** soal tambahan 31–60.
- Bentuk soal: pilihan ganda tunggal, pilihan ganda kompleks (semua pilihan benar), dan Benar/Salah (tiga pernyataan).
- Perpindahan nomor bebas, autosave `localStorage`, progres per level, penilaian, pembahasan lengkap, ulangi level.
- Responsif untuk HP dan desktop. Tidak perlu akun, framework, maupun database.

## Cara upload ke GitHub Pages
1. Buat repository GitHub (misalnya `tka-pplg`).
2. Upload `index.html`, `style.css`, `app.js`, dan `questions.json` **ke root repository**.
3. Buka **Settings → Pages**.
4. Pada **Build and deployment**, pilih **Deploy from a branch**; branch `main` dan folder `/ (root)`, lalu **Save**.
5. Setelah publikasi, website biasanya tersedia di `https://USERNAME.github.io/tka-pplg/`.

## Menjalankan di komputer
Jalankan server lokal dari folder proyek:

```bash
python -m http.server 8000
```

Lalu buka `http://localhost:8000` di browser. Jangan hanya double-click `index.html` karena browser bisa memblokir pengambilan JSON lewat `file://`.

## Mengedit soal
Buka `questions.json`. Masing-masing objek memiliki `id`, `level`, `type`, `question`, `explanation`, dan:
- `type: "single"`: `options` array dan `answer` huruf, misalnya `"B"`.
- `type: "multi"`: `options` array dan `answer` array huruf, misalnya `["A","C"]`.
- `type: "tf"`: `statements` berisi tiga teks dan `answer` berisi tiga boolean `[true,false,true]`.

## Penilaian
Setiap soal bernilai 1. Pada pilihan ganda kompleks, **semua** opsi harus tepat; pada Benar/Salah, **ketiga** pernyataan harus tepat. Nilai level = jumlah benar ÷ 30 × 100, dibulatkan ke bilangan bulat terdekat. Jawaban tidak lengkap bernilai 0.

## Catatan sumber
Soal Level 1 diekstraksi dari teks yang disediakan pengguna. **Jawaban dan pembahasan Level 1 adalah hasil analisis, bukan kunci resmi dari situs.** Level 2 disusun sebagai soal latihan tambahan. Tinjau konten dan hak penggunaan ulang materi sumber sebelum memublikasikannya secara terbuka.

## Privasi
Progres hanya tersimpan di browser perangkat melalui `localStorage`, bukan tersinkron antarperangkat.
