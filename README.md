# Praktikum Pertemuan 6 — Katalog Oleh-Oleh Medan

**Micael Zecsen Saragih · 4243250056 · PSIK24D · Ilmu Komputer UNIMED**

Praktikum berdasarkan Modul Pemrograman Mobile Pertemuan 6: layout responsif dan navigasi multi-screen. **Proyek ini akan dipakai lagi pada Pertemuan 7 untuk keranjang belanja; jangan dihapus.** Nama package disesuaikan agar tidak bertabrakan dengan proyek lain.

## Fitur
- Enam produk dari modul, data `Produk`, extension `rupiah`.
- Grid 2 kolom (<600 dp), 3 kolom (<900 dp), dan 4 kolom (≥900 dp).
- `MediaQuery` menampilkan `NavigationBar` (<840 dp) dan `NavigationRail` (≥840 dp).
- Halaman katalog, detail `/produk/:id`, Tentang, dan halaman ID tidak ditemukan.
- `StatefulShellRoute.indexedStack` mempertahankan posisi cabang navigasi.
- Tantangan B.4: `FilterChip` kategori, `/kategori/:nama`, serta `Hero` animasi produk.
- Layout detail vertikal di layar sempit, dua kolom di layar lebar.

## Persiapan project
ZIP berisi source Flutter; apabila folder platform Flutter belum ada, dari folder proyek ini jalankan **satu kali**:

```powershell
flutter create --org id.ac.unimed --project-name pm_pertemuan_06_4243250056 .
flutter pub get
flutter run -d chrome
```

Periksa sebelum menjalankan `flutter create .` supaya file source yang sudah ada tidak tertimpa. Jika project sudah memiliki platform, tidak perlu `flutter create`.

## Pengujian
```powershell
dart format .
flutter analyze
flutter test
```

Status: **belum dieksekusi di lingkungan ini** (Flutter SDK tidak tersedia). Jalankan perintah pada laptop mahasiswa, perbaiki masalah yang benar-benar muncul, lalu dokumentasikan hasilnya.

## Checklist lembar kerja
- [ ] Coba berbagai `mainAxisAlignment` pada `Row` (contoh A.2).
- [ ] Buat overflow teks panjang di `Row`, lalu perbaiki dengan `Expanded` + `TextOverflow.ellipsis`.
- [ ] Jalankan katalog pada layar sempit: 2 kolom dan navigasi bawah.
- [ ] Jalankan pada layar lebar: 3–4 kolom dan NavigationRail.
- [ ] Verifikasi detail produk, berpindah Tentang dan kembali, serta state cabang.
- [ ] Verifikasi URL `/#/produk/2` dan `/#/produk/99` pada Chrome.
- [ ] Verifikasi tantangan FilterChip, kategori, dan Hero.
- [ ] Rekam screenshot pada folder `docs/` dan push GitHub.

## Jawaban refleksi
1. `MediaQuery.sizeOf(context)` membaca ukuran jendela untuk memutuskan komponen navigasi global, sedangkan `LayoutBuilder` membaca constraint lokal untuk jumlah kolom dan tata letak detail.
2. `pathParameters['id']` bertipe `String?`, sehingga `int.tryParse` mencegah exception pada ID bukan angka, dan `cariProduk` boleh `null` untuk menampilkan halaman tidak ditemukan.
3. `context.go` memindahkan lokasi sesuai hierarki URL (cocok untuk rute katalog/detail), sementara `context.push` menumpuk halaman sementara untuk dikembalikan dengan `pop`.

## Pernyataan penggunaan AI
AI membantu penyusunan kode awal dan dokumentasi. Pengujian runtime, pemahaman kode, serta screenshot dari aplikasi yang benar-benar dijalankan tetap menjadi tanggung jawab mahasiswa.
