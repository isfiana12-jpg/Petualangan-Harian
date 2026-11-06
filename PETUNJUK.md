# Pasang Petualangan Harianku di Firebase

Hasilnya: aplikasi punya alamat sendiri (https://NAMA-PROJECT.web.app), bisa dibuka di HP mana pun, dan datamu tersimpan di Firestore setelah masuk dengan Google.

## 1. Buat project
1. Buka https://console.firebase.google.com lalu **Add project** (Google Analytics boleh dimatikan).

## 2. Aktifkan login Google
2. **Build > Authentication > Get started > Sign-in method > Google > Enable**, pilih email dukungan, **Save**.

## 3. Buat database
3. **Build > Firestore Database > Create database**. Pilih lokasi (misal `asia-southeast2` Jakarta) dan mode **production**.

## 4. Ambil konfigurasi web
4. Klik ikon gerigi > **Project settings > Your apps > ikon Web (</>)**. Daftarkan aplikasi (centang Hosting tidak wajib).
5. Salin isi `firebaseConfig`, lalu buka `public/index.html` dan ganti baris `const cfg={...}` (cari tulisan "ISI DENGAN firebaseConfig") dengan nilaimu: `apiKey`, `authDomain`, `projectId`, `appId`.
   (apiKey di sini bukan rahasia. Keamanan data dijaga oleh aturan di `firestore.rules`.)

## 5. Deploy
Pasang Node.js (https://nodejs.org), lalu di terminal, di dalam folder ini:

    npm install -g firebase-tools
    firebase login
    firebase use --add        # pilih project-mu
    firebase deploy

Selesai. Buka alamat `https://NAMA-PROJECT.web.app` di HP, tekan **Masuk dengan Google**.
Di Chrome HP: menu titik tiga > **Tambahkan ke layar utama** supaya terasa seperti aplikasi.

## Memindahkan data lama
Di versi lama: tab Riwayat > **Salin cadangan**. Di versi baru (setelah masuk): tab Riwayat > tempel di kotak > **Pulihkan**. Data langsung ikut ke cloud.

## Catatan
- Semua data disimpan dalam satu dokumen (batas Firestore 1 MB). Itu cukup untuk waktu lama, tapi kalau jurnalmu sangat panjang, kabari untuk dipecah per bulan.
- Kalau dibuka di dua perangkat sekaligus, versi yang terakhir diubah yang dipakai.
- Paket gratis (Spark) cukup untuk pemakaian pribadi.
