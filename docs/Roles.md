\# Roles \& Responsibilities



FFixiT Management System (FFixiT-MS)



\---



\## Document Information



| Item | Value |

|------|-------|

| Version | 0.1 |

| Author | Muhammad Irfan Syafiq |

| Project | FFixiT-MS |

| Last Update | 2026-07-08 |

| Status | Draft |



\---



\# Overview



Dokumen ini menjelaskan role pengguna beserta tanggung jawab, hak akses, dan batasan pada sistem FFixiT-MS.



Sistem menggunakan \*\*Role Based Access Control (RBAC)\*\* sehingga setiap pengguna hanya dapat mengakses menu dan fitur sesuai dengan tugasnya.



\---



\# User Roles



\## 1. IT (Super Administrator)



\### Description



IT merupakan Super Administrator yang memiliki akses penuh terhadap sistem.



\### Responsibilities



\- Mengelola User

\- Mengelola Role

\- Mengelola Permission

\- Mengelola Data Master

\- Melakukan Reassign Teknisi

\- Approval Pembatalan Tiket

\- Monitoring Audit Log

\- Konfigurasi Sistem



\### Accessible Modules



\- Dashboard

\- User Management

\- Employee Management

\- Role \& Permission

\- Audit Log

\- Master Data

\- Monitoring

\- System Configuration



\### Restrictions



Tidak memiliki batasan akses.



\---



\## 2. Kepala Toko



\### Description



Kepala Toko bertugas melakukan monitoring operasional toko serta mengelola pengeluaran operasional.



\### Responsibilities



\- Monitoring Ticket

\- Monitoring Omzet

\- Monitoring Inventory

\- Monitoring KPI

\- Menginput Pengeluaran Operasional



\### Accessible Modules



\- Dashboard

\- Monitoring

\- Operational Expense

\- Reports



\### Restrictions



\- Tidak dapat mengubah data transaksi.

\- Tidak dapat menghapus data.

\- Tidak dapat mengubah inventory.



\---



\## 3. Admin Gudang



\### Description



Admin Gudang bertanggung jawab terhadap seluruh aktivitas inventory.



\### Responsibilities



\- Mengelola Supplier

\- Mengelola Master Barang

\- Barang Masuk

\- Stock Opname

\- Request Sparepart

\- Monitoring Stock



\### Accessible Modules



\- Dashboard

\- Supplier

\- Master Barang

\- Inventory

\- Riwayat Inventory



\### Restrictions



\- Tidak dapat membuat Ticket.

\- Tidak dapat membuat Invoice.

\- Tidak dapat mengubah data Customer.



\---



\## 4. Customer Service (CS)



\### Description



Customer Service menjadi penghubung antara customer dan teknisi.



\### Responsibilities



\- Membuat Ticket

\- Menginput Customer

\- Follow Up Approval

\- Membuat Invoice Service

\- Membuat Invoice Penjualan

\- Mencetak Tanda Terima

\- Mengajukan Pembatalan Ticket



\### Accessible Modules



\- Dashboard

\- Ticket

\- Customer

\- Invoice

\- Direct Sales



\### Restrictions



\- Tidak dapat mengubah hasil diagnosis teknisi.

\- Tidak dapat membatalkan ticket secara langsung.

\- Tidak dapat mengubah inventory.



\---



\## 5. Teknisi



\### Description



Teknisi bertanggung jawab terhadap proses diagnosis dan pengerjaan service.



\### Responsibilities



\- Mengambil Ticket

\- Diagnosis

\- Upload Evidence Before

\- Upload Evidence After

\- Menginput Progress

\- Menginput Biaya Jasa

\- Menginput Sparepart

\- Menyelesaikan Ticket

\- Request Sparepart



\### Accessible Modules



\- Dashboard

\- My Ticket

\- Diagnosis

\- Progress Service



\### Restrictions



\- Tidak dapat membuat Invoice.

\- Tidak dapat mengubah data Customer.

\- Tidak dapat membatalkan Ticket.

\- Tidak dapat mengubah Inventory.



\---



\# Role Hierarchy



```

IT

│

├── Kepala Toko

├── Admin Gudang

├── Customer Service

└── Teknisi

```



IT memiliki akses penuh terhadap seluruh modul.



Role lainnya hanya memiliki akses sesuai tugas masing-masing.



\---



\# Business Rules



\## Ticket



\- Ticket dibuat oleh CS.

\- Ticket hanya dapat diambil oleh satu Teknisi.

\- Ticket tidak dapat dikerjakan sebelum customer memberikan approval.

\- Ticket tidak dapat dibatalkan oleh Teknisi.

\- Pembatalan Ticket harus melalui approval IT.



\---



\## Inventory



\- Inventory dikelola oleh Admin Gudang.

\- Pengurangan stock dilakukan otomatis ketika terjadi penjualan atau service.

\- Seluruh perubahan stock tercatat sebagai Stock Movement.



\---



\## Invoice



\- Invoice hanya dibuat oleh CS.

\- Invoice Service hanya dapat dibuat setelah Teknisi menyelesaikan Ticket.



\---



\## Audit Log



\- Seluruh aktivitas pengguna dicatat.

\- Audit Log tidak dapat diedit maupun dihapus.

\- Audit Log hanya dapat diakses oleh IT.



\---



\# Summary



| Role | Main Responsibility |

|------|----------------------|

| IT | Mengelola seluruh sistem |

| Kepala Toko | Monitoring operasional dan pengeluaran |

| Admin Gudang | Inventory dan Supplier |

| Customer Service | Ticket, Customer, Invoice |

| Teknisi | Diagnosis dan Service |

