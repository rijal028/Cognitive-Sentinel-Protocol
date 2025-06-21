# Riset V3: Menjinakkan "The Sleeper Agent"
### Sebuah Peningkatan untuk Protokol Kognitif dengan Validasi Baseline

Dokumen ini merinci kerangka kerja konseptual untuk mengatasi ancaman tingkat lanjut "Sleeper Agent" dan masalah "Peracunan Data Dasar" (*Baseline Poisoning*).

---

### **(English Version) V3 Research: Neutralizing the "Sleeper Agent"**
*An Enhancement for the Cognitive Protocol with Baseline Validation*

#### **1. The Threat Definition: The "Poisoned Baseline" Problem**

The standard Cognitive Protocol is effective at detecting behavioral anomalies against an established, trusted baseline. However, its most sophisticated threat vector is the **"Sleeper Agent"**: a malicious actor (either a compromised new hire's account or a malicious insider) who passes all initial checks.

This actor then patiently operates with seemingly normal behavior for the first 30-90 days. Their goal is to **poison the learning process** of the system, teaching it that a malicious or overly-permissive set of behaviors is "normal." Once this poisoned baseline is established, their future malicious actions will not trigger significant Trust Score penalties, allowing them to fly under the radar.

#### **2. The Solution: The "Zero-Trust Onboarding" Protocol**

To counter this, we introduce an enhanced module: The Zero-Trust Onboarding Protocol. Its goal is not just to learn a new user's behavior, but to **actively validate the authenticity of that behavior** during the initial learning phase. This is achieved through three new pillars of analysis.

**Pillar 1: Cohort Analysis (Group Comparison)**
The system no longer just compares a user to their own past behavior. It compares them to their **peer group (cohort)**.
* **Process:** A new user, "Charlie (Junior Developer, Mobile Team, Joined June 2025)," is automatically benchmarked against the aggregated and anonymized behavioral data of all other junior developers in similar teams.
* **Insight:** This allows us to distinguish between a "genius" and a "spy."
    * A **true genius** will be a positive anomaly (e.g., completes tasks 5x faster than the cohort average).
    * A **spy pretending to be a novice** will be a negative anomaly (e.g., has a near-zero rate of consulting documentation, unlike 99% of new developers in their cohort).

**Pillar 2: Qualitative Parameter Monitoring**
Beyond simple actions, the system analyzes the *quality* and *nature* of the behavior to differentiate between a genuine novice and an expert in disguise.
* **Key Parameters:**
    * **Error Rate:** A real novice makes honest mistakes (typos, failed code builds). A spy might be too perfect.
    * **Navigational Efficiency:** A novice "wanders" and searches for things. A spy might move with unnatural precision.
    * **Documentation Consumption:** A novice consumes vast amounts of internal documentation. A spy might avoid this to prevent leaving a trail.

**Pillar 3: Managerial Review & Random Audits**
This provides the human oversight layer.
* **The Trust Dashboard:** The dashboard we designed will visually represent the Cohort Analysis and Qualitative Parameters, allowing a manager to quickly see if a new hire's learning curve is genuine or suspicious.
* **Random Audits:** The system will periodically flag a small percentage of "Normal" users for a quick managerial review, creating an unpredictable check that makes it risky for a sleeper agent to remain complacent.

#### **3. Conclusion: From a Reactive to a Predictive Immune System**

With these enhancements, the Cognitive Protocol evolves. It no longer just reacts to deviations from a baseline; it **predictively assesses the trustworthiness of the baseline itself.** It makes the price of infiltration—requiring an actor to perfectly mimic the inefficient and mistake-prone learning process of a true novice for months—prohibitively expensive for even the most patient attackers.

---
---

### **(Versi Bahasa Indonesia) Riset V3: Menjinakkan "The Sleeper Agent"**
*Sebuah Peningkatan untuk Protokol Kognitif dengan Validasi Baseline*

#### **1. Definisi Ancaman: Masalah "Peracunan Data Dasar"**

Protokol Kognitif standar efektif dalam mendeteksi anomali perilaku terhadap baseline yang sudah ada dan tepercaya. Namun, vektor serangan paling canggihnya adalah **"Sleeper Agent"**: seorang aktor jahat (baik akun karyawan baru yang dibajak atau orang dalam) yang berhasil lolos semua pemeriksaan awal.

Aktor ini kemudian dengan sabar beroperasi dengan perilaku yang tampak normal selama 30-90 hari pertama. Tujuannya adalah untuk **meracuni proses pembelajaran** sistem, mengajari sistem bahwa serangkaian perilaku yang berbahaya atau terlalu permisif adalah "normal". Setelah baseline yang beracun ini terbentuk, tindakan jahatnya di masa depan tidak akan memicu penalti Skor Kepercayaan yang signifikan, memungkinkannya untuk terbang di bawah radar.

#### **2. Solusinya: "Protokol Onboarding Zero-Trust"**

Untuk melawannya, kita memperkenalkan modul tambahan: Protokol Onboarding Zero-Trust. Tujuannya bukan hanya untuk mempelajari perilaku pengguna baru, tetapi untuk **secara aktif memvalidasi keaslian perilaku tersebut** selama fase pembelajaran awal. Ini dicapai melalui tiga pilar analisis baru.

**Pilar 1: Analisis Kelompok (Cohort Analysis)**
Sistem tidak lagi hanya membandingkan pengguna dengan perilaku masa lalunya sendiri. Ia membandingkannya dengan **kelompok sebayanya (cohort)**.
* **Proses:** Pengguna baru, "Charlie (Junior Developer, Tim Mobile, Bergabung Juni 2025)," secara otomatis diukur kinerjanya terhadap data perilaku gabungan dan anonim dari semua junior developer lain di tim serupa.
* **Wawasan:** Ini memungkinkan kita membedakan antara "jenius" dan "mata-mata".
    * Seorang **jenius sejati** akan menjadi anomali positif (misal, menyelesaikan tugas 5x lebih cepat dari rata-rata kelompoknya).
    * Seorang **mata-mata yang berpura-pura menjadi pemula** akan menjadi anomali kecurigaan (misal, tingkat konsultasi dokumentasinya mendekati nol, tidak seperti 99% developer baru di kelompoknya).

**Pilar 2: Pemantauan Parameter Kualitatif**
Selain tindakan sederhana, sistem menganalisis *kualitas* dan *sifat* dari perilaku untuk membedakan antara pemula asli dan ahli yang menyamar.
* **Parameter Kunci:**
    * **Tingkat Kesalahan:** Pemula asli membuat kesalahan jujur (salah ketik, build gagal). Seorang mata-mata mungkin terlalu sempurna.
    * **Efisiensi Navigasi:** Pemula "berkeliling" dan mencari-cari. Seorang mata-mata mungkin bergerak dengan presisi yang tidak wajar.
    * **Konsumsi Dokumentasi:** Pemula mengonsumsi banyak sekali dokumentasi internal. Seorang mata-mata mungkin menghindarinya agar tidak meninggalkan jejak.

**Pilar 3: Tinjauan Manajerial & Audit Acak**
Ini menyediakan lapisan pengawasan manusia.
* **Dasbor Kepercayaan:** Dasbor yang kita rancang akan memvisualisasikan Analisis Kelompok dan Parameter Kualitatif, memungkinkan manajer untuk dengan cepat melihat apakah kurva belajar karyawan baru itu asli atau mencurigakan.
* **Audit Acak:** Sistem akan secara berkala menandai sebagian kecil pengguna "Normal" untuk tinjauan manajerial singkat, menciptakan pemeriksaan tak terduga yang membuat mata-mata berisiko untuk tetap berpuas diri.

#### **3. Kesimpulan: Dari Sistem Imun Reaktif menjadi Prediktif**

Dengan penyempurnaan ini, Protokol Kognitif berevolusi. Ia tidak lagi hanya bereaksi terhadap penyimpangan dari baseline; ia **secara prediktif menilai tingkat kepercayaan dari baseline itu sendiri.** Ini membuat harga penyusupan—mengharuskan seorang aktor untuk meniru dengan sempurna proses belajar seorang pemula yang tidak efisien dan penuh kesalahan selama berbulan-bulan—menjadi sangat mahal bahkan untuk penyerang yang paling sabar sekalipun.
