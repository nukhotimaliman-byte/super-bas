# 🔧 Fix: Website Jadi BLANK di cPanel

## ❌ Masalah yang Ditemukan

Website jadi blank ketika diupload ke cPanel karena **path untuk asset tidak benar**.

### Penyebab:
```html
<!-- SALAH (Absolute Path) -->
<script src="/assets/index-Dsqa7O20.js"></script>
<link href="/assets/index-DC0SG-Zv.css">
```

**Path absolute `/assets/`** hanya bekerja jika:
- Website di root domain (domain.com/)
- Tidak bekerja jika di subfolder (domain.com/nama-folder/)
- Tidak bekerja jika ada base path berbeda

---

## ✅ SOLUSI YANG DITERAPKAN

Mengubah ke **Relative Path** yang lebih flexible:

```html
<!-- BENAR (Relative Path) -->
<script src="./assets/index-Dsqa7O20.js"></script>
<link href="./assets/index-DC0SG-Zv.css">
```

### Keuntungan Relative Path:
✅ Bekerja di root domain: `domain.com/` → `domain.com/assets/`  
✅ Bekerja di subfolder: `domain.com/app/` → `domain.com/app/assets/`  
✅ Tidak tergantung path config  
✅ Universal untuk semua hosting  

---

## 📋 Apa yang Sudah Diubah

| File | Perubahan | Status |
|------|-----------|--------|
| `website-untuk-cpanel/index.html` | `/assets/` → `./assets/` | ✅ Fixed |
| `website-cpanel-ready.zip` | Rebuilt dengan file fixed | ✅ Updated |

---

## 🎯 Langkah Berikutnya

### Untuk cPanel Rumahweb:

#### Jika di Root Domain (domain.com):
```
1. Download: website-cpanel-ready.zip (UPDATED)
2. Extract ke folder baru
3. Upload semua file ke public_html/
4. Akses: domain.com/
5. ✅ Website seharusnya TIDAK BLANK lagi
```

#### Jika di Subfolder (domain.com/app):
```
1. Download: website-cpanel-ready.zip (UPDATED)
2. Extract ke folder baru
3. Buat folder "app" di public_html/
4. Upload semua file ke public_html/app/
5. Akses: domain.com/app/
6. ✅ Website seharusnya TIDAK BLANK lagi
```

---

## 🧪 Testing

Untuk verify sebelum upload ke cPanel:

```bash
# Local test (root):
python3 -m http.server 8080 --directory website-untuk-cpanel
# Akses: http://localhost:8080/

# Local test (subfolder):
# Buat subfolder dan test dari sana
```

---

## 📊 Verification Checklist

Sebelum upload ke cPanel, pastikan:

- [x] Path di index.html sudah `./assets/` (relative)
- [x] Folder `assets/` ada dengan file di dalamnya
- [x] File `.htaccess` ada untuk SPA routing
- [x] ZIP file sudah updated (2/7/2026 14:03)

---

## 🚀 Update File Ready

**File yang sudah di-update:**
- ✅ `website-cpanel-ready.zip` (137 KB)
  - HTML dengan relative path fixed
  - Semua assets lengkap
  - .htaccess included

**Gunakan file terbaru ini untuk upload!**

---

## 💡 Teknis Penjelasan

### Absolute Path Problem:
```
Ketika browser load:
1. Browser parsing index.html
2. Menemukan: <script src="/assets/...">
3. Browser cari di: https://domain.com/assets/
4. Jika website di subfolder → URL salah!
5. JS/CSS tidak load → Halaman blank
```

### Relative Path Solution:
```
Ketika browser load:
1. Browser parsing index.html di: https://domain.com/app/
2. Menemukan: <script src="./assets/...">
3. Browser cari di: https://domain.com/app/assets/
4. Path relative terhadap current file location
5. JS/CSS load dengan benar ✅
```

---

## ⚠️ Penting Diingat

1. **Gunakan file ZIP terbaru** yang sudah fixed
2. **Jangan download file lama** - pastikan updated 2026-02-07 14:03
3. **Path relative ini universal** - bekerja di manapun

---

## 📞 Jika Masih Blank

Jika setelah upload masih blank:

1. **Clear browser cache** (Ctrl+F5)
2. **Check DevTools (F12)** → Console → ada error apa?
3. **Verify file upload**:
   - Buka File Manager cPanel
   - Pastikan `assets/` folder dan file di dalamnya ada
   - Pastikan `index.html` ada
4. **Check .htaccess**:
   - Pastikan ada di public_html (file tersembunyi)
   - Content seharusnya ada RewriteRule untuk SPA

Jika semua sudah ada tapi masih blank:
- **Kontak Rumahweb Support** - minta cek mod_rewrite enabled

---

Generated: 2026-02-07 14:03  
Status: ✅ FIXED & VERIFIED  
Version: website-cpanel-ready-v2
