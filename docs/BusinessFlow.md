\# Business Flow

FFixiT Management System (FFixiT-MS)

\---

\## Document Information

| Item        | Value                 |
| ----------- | --------------------- |
| Version     | 0.1                   |
| Author      | Muhammad Irfan Syafiq |
| Project     | FFixiT-MS             |
| Last Update | 2026-07-09            |
| Status      | Active                |

\---

\# Overview

FFixiT-MS merupakan sistem manajemen operasional untuk toko komputer yang menyediakan layanan penjualan produk, jasa perbaikan, dan jasa perakitan komputer. Sistem ini dirancang untuk membantu pengelolaan transaksi, inventory, service ticket, monitoring operasional, serta pengendalian akses pengguna berdasarkan Role Based Access Control (RBAC).Role yang tersedia pada sistem:

\- IT (Super Administrator)

\- Kepala Toko

\- Admin Gudang

\- Customer Service (CS)

\- Teknisi

\---

\# Scope

Business Flow ini mencakup proses utama yang akan diimplementasikan pada versi awal FFixiT-MS, meliputi:

- Service Management

\- Direct Sales (POS)

\- Inventory Management

\- Operational Expense

\- Monitoring Dashboard

\- Audit Log

\---

\# Business Flow

\## A. Service Flow

\### 1. Customer Datang

Customer datang ke toko membawa perangkat untuk diperbaiki atau meminta konsultasi.

↓

\### 2. CS Membuat Tiket \& Tanda Terima Barang

CS menginput:

\- Data Customer

\- Data Device

\- Keluhan

\- Kelengkapan Barang

\- Kondisi Fisik Awal

\- Estimasi selesai (opsional)

Status Ticket:

```

Waiting Technician

```

↓

\### 3. Teknisi Mengambil Tiket

Teknisi memilih tiket yang masih tersedia.

Sistem mencatat:

\- Teknisi

\- Tanggal

\- Jam

Status:

```

Diagnosis

```

↓

\### 4. Diagnosis

Teknisi melakukan:

\- Pemeriksaan perangkat

\- Foto Evidence Before

\- Analisa kerusakan

\- Estimasi biaya

\- Estimasi pengerjaan

\- Sparepart yang dibutuhkan

\*\*Business Rule\*\*

Teknisi \*\*belum diperbolehkan memulai pengerjaan\*\* sebelum customer memberikan persetujuan.

Status:

```

Waiting Customer Approval

```

↓

\### 5. CS Menghubungi Customer

CS melakukan konfirmasi kepada customer mengenai:

\- Hasil diagnosis

\- Estimasi biaya

\- Estimasi pengerjaan

Customer memiliki dua kemungkinan keputusan.

\---

\### 5.1 Customer Approved

Customer menyetujui hasil diagnosis.

↓

Teknisi dapat menekan tombol:

```

Start Service

```

Status berubah menjadi:

```

In Progress

```

\---

\### 5.2 Customer Rejected

Customer tidak menyetujui hasil diagnosis.

CS membuat:

```

Request Ticket Cancellation

```

Disertai evidence berupa:

\- Chat

\- Rekaman

\- Bukti lainnya

↓

IT melakukan review.

↓

Jika disetujui.

Status:

```

Cancelled

```

\*\*Business Rule\*\*

Teknisi tidak memiliki hak untuk membatalkan tiket.

\---

\### 6. Proses Service

Teknisi melakukan pengerjaan.

Selama proses berlangsung teknisi dapat menginput:

\- Progress pekerjaan

\- Catatan teknisi

\- Sparepart yang digunakan

\- Jasa yang dilakukan

Apabila sparepart tidak tersedia.

↓

Teknisi membuat:

```

Request Sparepart

```

↓

Admin Gudang melakukan pengadaan.

↓

Setelah sparepart tersedia.

↓

Service dilanjutkan.

\---

\### 7. Service Selesai

Teknisi menginput:

\- Foto Evidence After

\- Hasil pengerjaan

\- Biaya jasa

\- Sparepart yang digunakan

Kemudian menekan tombol:

```

Finish Service

```

Status:

```

Waiting Invoice

```

\---

\### 8. Invoice \& Payment

Button Invoice hanya aktif apabila status tiket:

```

Finished

```

CS membuat:

\- Invoice

\*\*Business Rule\*\*

Customer yang akan mengambil barang wajib membawa bukti tanda terima barang yang diberikan sebelum service

↓

Customer melakukan pembayaran.

↓

Status:

```

Paid

```

↓

Status akhir:

```

Closed

```

\---

\# B. Direct Sales Flow

Customer membeli sparepart tanpa melakukan service.

↓

CS membuat Invoice.

↓

Inventory otomatis berkurang.

↓

Transaksi selesai.

\---

\# C. Inventory Flow

Admin Gudang bertanggung jawab terhadap:

\- Supplier

\- Master Barang

\- Barang Masuk

\- Barang Keluar

\- Stock Saat Ini

\- Stock Opname

\- Request Sparepart

Setiap perubahan stock menghasilkan \*\*Stock Movement\*\*.

Jenis Stock Movement:

\- Purchase

\- Sales

\- Service

\- Adjustment

\- Stock Opname

\---

\# D. Operational Expense Flow

Kepala Toko menginput pengeluaran operasional.

Contoh:

\- Listrik

\- Air

\- Air Galon

\- Internet

\- Sewa Ruko

\- Peralatan Operasional

Seluruh transaksi pengeluaran menjadi bagian dari laporan keuangan toko.

\---

\# E. Monitoring Flow

Kepala Toko dapat memonitor:

\- Omzet

\- Pengeluaran Operasional

\- Ticket Real Time

\- Stock Barang

\- Service Performance

\- KPI Karyawan

Contoh Service Performance:

\- Open Ticket

\- Closed Ticket

\- Cancelled Ticket

\- Average Repair Time

Kepala Toko hanya memiliki hak monitoring dan tidak dapat mengubah data transaksi.

\---

\# F. Audit Flow

Seluruh aktivitas penting pengguna dicatat oleh sistem.

Contoh:

\- Login

\- Logout

\- Create Data

\- Update Data

\- Delete Data

\- Cancel Ticket

\- Change Technician

\- Stock Adjustment

\- Edit Invoice

Audit Log hanya dapat diakses oleh IT.

\*\*Business Rule\*\*

Audit Log bersifat \*\*immutable\*\*, sehingga tidak dapat diedit maupun dihapus oleh pengguna mana pun.

\---

\# Exceptional Cases

\## Teknisi Tidak Hadir

IT dapat melakukan:

```

Re-assign Technician

```

Riwayat teknisi sebelumnya tetap disimpan sebagai histori.

\---

\## Customer Membatalkan Setelah Approval

CS mengajukan pembatalan tiket.

↓

IT melakukan review.

↓

Jika disetujui.

↓

Status berubah menjadi:

```

Cancelled

```

\---

\## Sparepart Tidak Tersedia

Teknisi membuat Request Sparepart.

↓

Admin Gudang melakukan pembelian.

↓

Barang diterima.

↓

Inventory bertambah.

↓

Service dilanjutkan.

\---

\## Garansi

Ticket yang telah selesai dapat memiliki masa garansi sesuai kebijakan toko.

Apabila customer melakukan klaim garansi:

\- Ticket lama tetap tersimpan.

\- Sistem membuat riwayat klaim yang terhubung dengan ticket sebelumnya.

\- Seluruh histori service tetap dapat ditelusuri.

\---

\# Ticket Status

```````````````````````````````````````````````````

Waiting Technician

↓

Diagnosis

↓

Waiting Customer Approval

↓

In Progress

↓

Finished

↓

Waiting Payment

↓

Paid

↓

Closed

``````````````````````````````````````````````````

```````````````````````````````````````````````````
