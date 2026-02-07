# Panduan Deploy ke cPanel Rumahweb

## 📋 Isi Folder
Folder ini berisi semua file yang siap untuk diupload ke server hosting cPanel Anda.

**File-file penting:**
- `index.html` - File utama aplikasi web
- `assets/` - Folder berisi CSS dan JavaScript yang sudah di-compile
- `.htaccess` - Konfigurasi untuk SPA routing (PENTING - jangan dihapus!)

## 🚀 Cara Upload ke cPanel Rumahweb

### Metode 1: Menggunakan File Manager cPanel (Mudah)
1. Login ke cPanel Rumahweb Anda
2. Buka **File Manager**
3. Navigasi ke folder `public_html` (ini adalah root website Anda)
4. Jika sudah ada file lama, hapus semuanya
5. **Upload** semua file dari folder ini ke `public_html`
   - Tekan **Upload** 
   - Pilih semua file: `index.html`, folder `assets/`, dan `.htaccess`
6. Tunggu upload selesai
7. Akses website Anda di browser

### Metode 2: Menggunakan FTP (Lebih Cepat untuk File Banyak)
1. Dapatkan akun FTP dari cPanel Anda
2. Gunakan FTP Client seperti FileZilla:
   - Host: nama domain atau IP yang diberikan Rumahweb
   - Username: akun FTP Anda
   - Password: password FTP Anda
   - Port: 21
3. Navigate ke folder `public_html`
4. Drag & drop semua file dari folder ini ke FTP
5. Upload selesai

### Metode 3: Menggunakan Addon Domain (Jika ingin subfolder)
Jika ingin website di subfolder (misal: domain.com/nama-folder/):
1. Buat folder di `public_html`
2. Upload semua file ke folder tersebut
3. Akses di `domain.com/nama-folder/`

## ⚠️ PENTING - Tips Sukses Upload
- ✅ Pastikan **`.htaccess` HARUS** ada di root folder public_html
- ✅ Jika tidak ada `.htaccess`, routing mungkin tidak bekerja
- ✅ Pastikan mod_rewrite diaktifkan (biasanya aktif default di Rumahweb)
- ✅ Tunggu 5-10 menit setelah upload, cache bisa mempengaruhi
- ✅ Jika masih error, clear cache browser Anda (Ctrl+F5 atau Cmd+Shift+R)

## 🔍 Troubleshooting

### Website Menunjukkan Error 404
- Pastikan `.htaccess` sudah ter-upload dengan benar
- Cek di File Manager apakah `.htaccess` ada di `public_html`
- Jika masih error, kontak support Rumahweb untuk memastikan mod_rewrite aktif

### File Tidak Ter-upload
- Coba upload satu file dulu untuk test
- Pastikan ukuran file tidak melebihi limit (biasanya 100MB per file)
- Gunakan FTP jika File Manager terlalu lambat

### Website Blank atau Error
- Clear cache browser (Ctrl+F5)
- Cek console browser (F12) untuk error message
- Upload ulang semua file

## 📞 Kontak Support Rumahweb
Jika ada masalah dengan hosting, hubungi:
- Rumahweb Support: https://www.rumahweb.com/kontak
- Status cPanel: Cek di dashboard Rumahweb Anda

## ✨ Selamat!
Website Anda sekarang live di cPanel! 🎉

---
**Generated:** 2026-02-07
**Aplikasi:** Pasukan Alim Kosombi 2 DC
