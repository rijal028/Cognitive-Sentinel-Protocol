# Blueprint: Protokol Komunikasi Aman Internal (PKAI)
*Sebuah Kerangka Kerja Fondasi untuk Komunikasi Terverifikasi*

---

### **(English Version) Blueprint: The Internal Secure Communication Protocol (ISCP/PKAI)**
*A Foundational Framework for Verified Communication*

#### **1. The Core Problem: The Need for Internal Trust**
In any complex system composed of multiple services or processes, a critical vulnerability exists in the communication channels between them. How does Service A know that the message it received truly came from Service B, and not an impostor? This protocol is designed to solve this problem of internal trust for processes running on the same local network or machine.

#### **2. The Guiding Philosophy: Ephemeral, Scoped, and Context-Aware Tokens**
This protocol rejects the idea of a single, static "master key" for internal communication. Instead, it operates on a dynamic trust model based on three principles:
* **Ephemeral:** Trust is temporary. Access is granted via short-lived session tokens.
* **Scoped:** Trust is specific. A token for one function (e.g., "read status") cannot be used for another (e.g., "change configuration").
* **Context-Aware:** Trust is intelligent. The central service validates not just the token, but whether the request itself is logical for the requesting entity.

#### **3. The Three-Stage Protocol**

**Stage 1: Initial Trust Establishment (The Handshake)**
* **Method:** This protocol uses **Parent Process Inheritance** for the initial handshake. A master process creates a one-time, secret key in its memory and passes it directly to its "child" processes (e.g., the main service and the command-line tool) upon launch.
* **Reasoning:** This is the most secure method as the initial secret never touches the disk, making it extremely difficult to intercept. This establishes the initial **"Master Identity Token."**

**Stage 2: Per-Feature Session Token Exchange**
* **Method:** For any subsequent action, the client process uses its "Master Identity Token" to request a specific **"Session Token"** from the main service.
* **Example:** The CLI (client) asks, "This is me, I have the Master Token. I need a token to check the system status." The Service replies, "Here is a 'status-check' token, it is valid for 3 minutes."
* **Reasoning:** This implements the Principle of Least Privilege. If an attacker compromises the client and steals a "status-check" token, they cannot use it to perform a more dangerous action like changing a security policy.

**Stage 3: Contextual Validation**
* **Method:** The main service (the "gatekeeper" of functions) does not blindly grant Session Tokens. It performs a contextual check.
* **Example:** An IoT lightbulb process (client) requests a token to "access the smart lock's data." The service checks its policy matrix. It sees that a lightbulb has no logical reason to access the lock.
* **Action:** The request for the token is **denied**, and a high-priority security alert is generated, even though the lightbulb's "Master Identity Token" was valid.
* **Reasoning:** This protects against a compromised but "authenticated" internal component. It asks not just "Are you who you say you are?", but also "Does your request make sense?".

#### **4. Conclusion**
The PKAI/ISCP provides a robust, layered, and Zero-Trust approach to internal process communication. By combining secure initial trust, ephemeral session tokens, and intelligent contextual validation, it creates a resilient foundation upon which larger, more complex architectures like the `Fortress`, `Cognitive Protocol`, and `Cerebrum` can be safely built.

---
---

### **(Versi Bahasa Indonesia) Blueprint: Protokol Komunikasi Aman Internal (PKAI)**
*Sebuah Kerangka Kerja Fondasi untuk Komunikasi Terverifikasi*

#### **1. Masalah Inti: Kebutuhan akan Kepercayaan Internal**
Dalam sistem kompleks manapun yang terdiri dari banyak layanan atau proses, ada satu celah keamanan kritis di jalur komunikasi di antara mereka. Bagaimana Layanan A tahu bahwa pesan yang ia terima benar-benar datang dari Layanan B, dan bukan dari seorang peniru? Protokol ini dirancang untuk memecahkan masalah kepercayaan internal ini untuk proses-proses yang berjalan di jaringan lokal atau mesin yang sama.

#### **2. Filosofi Panduan: Token yang Sementara, Spesifik, dan Sadar Konteks**
Protokol ini menolak ide tentang satu "kunci master" yang statis untuk komunikasi internal. Sebaliknya, ia beroperasi pada model kepercayaan dinamis yang didasarkan pada tiga prinsip:
* **Sementara (Ephemeral):** Kepercayaan itu temporer. Akses diberikan melalui token sesi yang berumur pendek.
* **Spesifik (Scoped):** Kepercayaan itu spesifik. Sebuah token untuk satu fungsi (misal: "baca status") tidak bisa digunakan untuk fungsi lain (misal: "ubah konfigurasi").
* **Sadar Konteks (Context-Aware):** Kepercayaan itu cerdas. Layanan pusat tidak hanya memvalidasi token, tetapi juga apakah permintaan itu sendiri logis untuk entitas yang memintanya.

#### **3. Protokol Tiga Tahap**

**Tahap 1: Pembentukan Kepercayaan Awal (Jabat Tangan)**
* **Metode:** Protokol ini menggunakan **"Warisan dari Proses Induk" (Parent Process Inheritance)** untuk jabat tangan awal. Sebuah proses master menciptakan kunci rahasia sekali pakai di dalam memorinya dan mewariskannya secara langsung ke proses-proses "anak"-nya (misal: layanan utama dan alat baris perintah) saat diluncurkan.
* **Alasan:** Ini adalah metode paling aman karena rahasia awal tidak pernah menyentuh hard drive, membuatnya sangat sulit untuk dicegat. Ini menetapkan **"Token Identitas Utama"** awal.

**Tahap 2: Pertukaran Token Sesi per Fitur**
* **Metode:** Untuk setiap tindakan selanjutnya, proses klien menggunakan "Token Identitas Utama"-nya untuk meminta **"Token Sesi"** yang spesifik dari layanan utama.
* **Contoh:** CLI (klien) bertanya, "Ini saya, saya punya Token Utama. Saya butuh token untuk memeriksa status sistem." Layanan menjawab, "Ini 'token-cek-status', berlaku selama 3 menit."
* **Alasan:** Ini menerapkan Prinsip Hak Akses Minimal. Jika penyerang membajak klien dan mencuri "token-cek-status", dia tidak bisa menggunakannya untuk melakukan tindakan yang lebih berbahaya seperti mengubah kebijakan keamanan.

**Tahap 3: Validasi Kontekstual**
* **Metode:** Layanan utama ("penjaga gerbang" fungsi) tidak secara buta memberikan Token Sesi. Ia melakukan pemeriksaan kontekstual.
* **Contoh:** Sebuah proses lampu bohlam IoT (klien) meminta token untuk "mengakses data kunci pintu pintar". Layanan akan memeriksa matriks kebijakannya. Ia melihat bahwa lampu bohlam tidak punya alasan logis untuk mengakses kunci.
* **Tindakan:** Permintaan token **DITOLAK**, dan peringatan keamanan prioritas tinggi dihasilkan, meskipun "Token Identitas Utama" lampu itu valid.
* **Alasan:** Ini melindungi dari komponen internal yang sudah terotentikasi tetapi dibajak. Ia tidak hanya bertanya "Apakah kamu benar dirimu?", tetapi juga "Apakah permintaanmu masuk akal?".

#### **4. Kesimpulan**
PKAI menyediakan pendekatan berlapis dan Zero-Trust untuk komunikasi proses internal. Dengan menggabungkan kepercayaan awal yang aman, token sesi sementara, dan validasi kontekstual yang cerdas, ia menciptakan sebuah fondasi tangguh di mana arsitektur yang lebih besar dan kompleks seperti `Benteng`, `Protokol Kognitif`, dan `Cerebrum` dapat dibangun dengan aman.
