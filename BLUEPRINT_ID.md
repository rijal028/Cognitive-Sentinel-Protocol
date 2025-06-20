# Blueprint: Protokol Penjaga Kognitif (Cognitive Sentinel Protocol)
### Sebuah Kerangka Kerja Keamanan Identitas Dinamis

**Oleh: Rijal Saepuloh**

---

### Daftar Isi
1.  [Filosofi Inti: Mengasumsikan Kebobolan (Assume Breach)](#1-filosofi-inti-mengasumsikan-kebobolan-assume-breach)
2.  [Arsitektur Tiga Lapis Pertahanan Internal](#2-arsitektur-tiga-lapis-pertahanan-internal)
    * [2.1. Lapisan Profil: Menciptakan "DNA Perilaku Digital"](#21-lapisan-profil-menciptakan-dna-perilaku-digital)
    * [2.2. Lapisan Deteksi: Mesin Skor Kepercayaan Dinamis](#22-lapisan-deteksi-mesin-skor-kepercayaan-dinamis)
    * [2.3. Lapisan Respon: Tindakan Imun Otomatis](#23-lapisan-respon-tindakan-imun-otomatis)
3.  [Sinergi dengan Arsitektur Benteng](#3-sinergi-dengan-arsitektur-benteng)
4.  [Studi Kasus: Menetralisir Vektor Serangan Spesifik](#4-studi-kasus-menetralisir-vektor-serangan-spesifik)
5.  [Kesimpulan: Menuju Keamanan Berbasis Identitas](#5-kesimpulan-menuju-keamanan-berbasis-identitas)

---

### 1. Filosofi Inti: Mengasumsikan Kebobolan (Assume Breach)

Arsitektur keamanan tradisional berfokus pada pertahanan perbatasan (perimeter)—membangun tembok yang lebih tinggi untuk mencegah penyerang masuk. "Protokol Kognitif" beroperasi pada filosofi yang lebih modern dan realistis: **Assume Breach**.

Kita harus berasumsi bahwa cepat atau lambat, pertahanan perbatasan akan gagal. Kredensial pengguna—baik karena *phishing*, rekayasa sosial, atau kebocoran data—akan jatuh ke tangan yang salah.

> Pertanyaan yang ingin dijawab oleh protokol ini bukan lagi "Bagaimana cara mencegah penyusup masuk?", melainkan "Bagaimana cara kita mendeteksi dan melumpuhkan penyusup yang sudah berada di dalam dan menyamar sebagai salah satu dari kita?"

Untuk itu, kita membangun sebuah **Sistem Imunitas Digital** yang secara konstan berpatroli di dalam jaringan untuk membedakan antara perilaku "diri sendiri" yang sah dan perilaku "asing" yang berbahaya, bahkan jika keduanya menggunakan identitas yang sama.

### 2. Arsitektur Tiga Lapis Pertahanan Internal

Protokol ini bekerja melalui tiga lapisan yang saling berhubungan untuk memvalidasi identitas secara berkelanjutan.

#### 2.1. Lapisan Profil: Menciptakan "DNA Perilaku Digital"
Lapisan pertama adalah tentang pembelajaran. Sistem secara pasif dan terus-menerus membangun sebuah profil atau "DNA" yang unik untuk setiap pengguna. Profil ini terdiri dari puluhan sinyal lemah, termasuk:
* **Biometrik Perilaku:** Irama mengetik (*keystroke dynamics*), pola gerakan dan klik mouse.
* **Pola Kebiasaan:** Jam kerja tipikal, lokasi geografis (IP) yang biasa digunakan, perangkat keras (*device fingerprint*) yang terdaftar.
* **Pola Navigasi:** Aplikasi yang sering dibuka, urutan alur kerja, jenis file yang biasa diakses.
* **Pola Jaringan:** Pola penggunaan *bandwidth*, server internal yang biasa dihubungi.

#### 2.2. Lapisan Deteksi: Mesin Skor Kepercayaan Dinamis
Lapisan ini adalah otak dari sistem. Ia berfungsi sebagai tim detektif yang secara *real-time* membandingkan aktivitas saat ini dengan "DNA Perilaku" yang sudah ada.
* **Skor Kepercayaan (Trust Score):** Setiap sesi pengguna dimulai dengan skor 100.
* **Penalti Anomali:** Setiap tindakan yang menyimpang dari profil DNA akan dikenakan "penalti" yang mengurangi skor. Bobot penalti ditentukan oleh tingkat keparahan anomali (misalnya, login dari negara baru memiliki penalti lebih besar daripada gerakan mouse yang sedikit berbeda).
* **Fusi Sinyal:** Kekuatan lapisan ini adalah kemampuannya untuk menggabungkan banyak anomali kecil menjadi satu kesimpulan besar yang mencurigakan.

#### 2.3. Lapisan Respon: Tindakan Imun Otomatis
Lapisan ini adalah "otot" dari sistem. Ketika Skor Kepercayaan seorang pengguna turun melewati ambang batas tertentu, sistem secara otomatis menjalankan respons yang sepadan.
* **Tingkat 1 (Skor Agak Rendah, misal < 80):** **Verifikasi Ulang.** Sistem memaksa otentikasi multi-faktor (MFA). Contoh: Budi login dari cafe (lokasi baru), skor turun, sistem meminta persetujuan dari ponsel Budi.
* **Tingkat 2 (Skor Cukup Rendah, misal < 50):** **Pembatasan Sesi.** Sesi pengguna mungkin dibatasi (misalnya, tidak bisa mengakses data super sensitif) dan sebuah peringatan (*alert*) dikirim ke tim keamanan untuk dianalisis lebih lanjut.
* **Tingkat 3 (Skor Kritis, misal < 25):** **Blokir Total.** Sesi langsung dimatikan, akun dikunci, dan peringatan darurat dikirim.

### 3. Sinergi dengan Arsitektur Benteng

Kedua konsep ini dirancang untuk bekerja bersama sebagai strategi pertahanan berlapis (*defense-in-depth*).
* **Arsitektur Benteng:** Berfungsi sebagai "sistem pertahanan udara dan perbatasan". Ia mencegah misil (file berbahaya) dari luar masuk dan merusak kota.
* **Protokol Kognitif:** Berfungsi sebagai "polisi rahasia dan sistem imun" di dalam kota. Ia mencari mata-mata dan pengkhianat yang sudah berhasil menyusup dan menyamar sebagai warga biasa.

### 4. Studi Kasus: Menetralisir Vektor Serangan Spesifik

* **vs. Kredensial Curian:** Penyerang mungkin punya password Budi, tapi kombinasi anomali lokasi, waktu, dan perilaku biometriknya akan segera menurunkan Skor Kepercayaan.
* **vs. Pembajakan Sesi:** Meskipun penyerang mencuri *session cookie* yang aktif, perubahan mendadak pada sinyal jaringan (IP, lokasi geografis, dll.) akan langsung terdeteksi sebagai anomali besar.
* **vs. Serangan Lambat:** Analisis pola jangka panjang akan mendeteksi aktivitas anomali yang konsisten (misal: unduhan data kecil setiap malam) dan menurunkannya menjadi sebuah laporan untuk diinvestigasi.
* **vs. Serangan "Sleeper Agent" (v3):** Ini adalah tantangan terberat. Protokol ini bisa diperkuat lebih lanjut dengan kebijakan "Zero-Trust Onboarding", di mana profil DNA karyawan baru dibangun dalam lingkungan "sandbox" dengan akses terbatas selama 30 hari pertama untuk memastikan baseline yang dipelajari benar-benar bersih.

### 5. Kesimpulan: Menuju Keamanan Berbasis Identitas

"Protokol Kognitif" mewakili pergeseran dari keamanan berbasis kredensial statis (siapa yang Anda *katakan*) ke keamanan berbasis identitas dinamis (siapa yang Anda *buktikan* melalui perilaku Anda). Dengan terus-menerus memvalidasi identitas melalui lensa perilaku, kita dapat secara efektif mendeteksi dan melumpuhkan ancaman paling berbahaya—ancaman yang datang dari dalam.
