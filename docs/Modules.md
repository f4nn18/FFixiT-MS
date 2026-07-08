\# System Modules



FFixiT Management System (FFixiT-MS)



\---



\## Document Information



|-------------|-----------------------|

| Version     | 0.1                   |

| Author      | Muhammad Irfan Syafiq |

| Project     | FFixiT-MS             |

| Last Update | 2026-07-08            |

| Status      | Draft                 |

|-------------|-----------------------|

\---



\# Overview



Dokumen ini menjelaskan seluruh modul utama yang akan dikembangkan pada FFixiT-MS beserta tujuan, pengguna yang memiliki akses, dan fungsi utama setiap modul.



Modul dirancang secara modular agar mudah dikembangkan, dipelihara, dan diperluas pada versi berikutnya.



\---



\# Module List



\## 1. Authentication



\### Purpose



Mengelola proses autentikasi pengguna sebelum mengakses sistem.



\### Main Features



\- Login

\- Logout

\- Session Management

\- Remember Login



\### Accessible By



\- Semua User



\---



\## 2. Dashboard



\### Purpose



Menampilkan informasi sesuai dengan role pengguna.



\### Main Features



\- Ringkasan aktivitas

\- Statistik

\- Shortcut Menu

\- Informasi real-time



\### Accessible By



\- IT

\- Kepala Toko

\- Admin Gudang

\- CS

\- Teknisi



\---



\## 3. Customer Management



\### Purpose



Mengelola data customer.



\### Main Features



\- Tambah Customer

\- Edit Customer

\- Detail Customer

\- Riwayat Service

\- Riwayat Pembelian



\### Accessible By



\- CS

\- IT



\---



\## 4. Service Ticket



\### Purpose



Mengelola seluruh proses service mulai dari penerimaan perangkat hingga selesai.



\### Main Features



\- Create Ticket

\- Assign Technician

\- Diagnosis

\- Customer Approval

\- Progress Service

\- Finish Service

\- Warranty History

\- Ticket Cancellation Request



\### Accessible By



\- CS

\- Teknisi

\- IT



\---



\## 5. Inventory Management



\### Purpose



Mengelola persediaan barang.



\### Main Features



\- Stock Saat Ini

\- Barang Masuk

\- Barang Keluar

\- Stock Opname

\- Stock Adjustment

\- Stock Movement

\- Request Sparepart



\### Accessible By



\- Admin Gudang

\- IT



\---



\## 6. Supplier Management



\### Purpose



Mengelola data supplier.



\### Main Features



\- Tambah Supplier

\- Edit Supplier

\- Purchase History



\### Accessible By



\- Admin Gudang

\- IT



\---



\## 7. Direct Sales (POS)



\### Purpose



Melayani penjualan sparepart tanpa proses service.



\### Main Features



\- Create Invoice

\- Payment

\- Print Invoice

\- Sales History



\### Accessible By



\- CS

\- IT



\---



\## 8. Operational Expense



\### Purpose



Mencatat seluruh pengeluaran operasional toko.



\### Main Features



\- Tambah Pengeluaran

\- Edit Pengeluaran

\- Kategori Pengeluaran

\- Riwayat Pengeluaran



\### Accessible By



\- Kepala Toko

\- IT



\---



\## 9. Monitoring \& Reports



\### Purpose



Menampilkan kondisi operasional toko secara real-time.



\### Main Features



\- Ticket Monitoring

\- Revenue Monitoring

\- Inventory Monitoring

\- KPI Monitoring

\- Operational Expense Summary



\### Accessible By



\- Kepala Toko

\- IT



\---



\## 10. User Management



\### Purpose



Mengelola seluruh akun pengguna sistem.



\### Main Features



\- Employee Management

\- User Management

\- Role Assignment

\- Reset Password

\- Activate / Deactivate User



\### Accessible By



\- IT



\---



\## 11. Audit Log



\### Purpose



Mencatat seluruh aktivitas penting pengguna sebagai riwayat sistem.



\### Main Features



\- Login History

\- Data Changes

\- Ticket Activity

\- Inventory Activity

\- User Activity

\- Search Log



\### Accessible By



\- IT



\---



\# Module Dependency



```

Authentication

&#x20;       │

&#x20;       ▼

Dashboard

&#x20;       │

&#x20;       ├──────── Customer Management

&#x20;       ├──────── Service Ticket

&#x20;       ├──────── Inventory Management

&#x20;       ├──────── Supplier Management

&#x20;       ├──────── Direct Sales (POS)

&#x20;       ├──────── Operational Expense

&#x20;       ├──────── Monitoring \& Reports

&#x20;       ├──────── User Management

&#x20;       └──────── Audit Log

```



\---



\# Module Access Matrix



|        Module        | IT | Kepala Toko | Admin Gudang | CS | Teknisi  |

|----------------------|:--:|:-----------:|:------------:|:--:|:--------:|

| Authentication       | ✅ |     ✅     |      ✅     | ✅ |   ✅    |

| Dashboard            | ✅ |     ✅     |      ✅     | ✅ |   ✅    |

| Customer Management  | ✅ |     ❌     |      ❌     | ✅ |   ❌    |

| Service Ticket       | ✅ |     👁️     |      ❌     | ✅ |   ✅    |

| Inventory Management | ✅ |     👁️     |      ✅     | ❌ |   👁️    |

| Supplier Management  | ✅ |     ❌     |      ✅     | ❌ |   ❌    |

| Direct Sales (POS)   | ✅ |     👁️     |      ❌     | ✅ |   ❌    |

| Operational Expense  | ✅ |     ✅     |      ❌     | ❌ |   ❌    |

| Monitoring \& Reports | ✅ |     ✅     |      👁️     | ❌ |   ❌    |

| User Management      | ✅ |     ❌     |      ❌     | ❌ |   ❌    |

| Audit Log            | ✅ |     ❌     |      ❌     | ❌ |   ❌    |



\*\*Keterangan\*\*



\- ✅ Full Access

\- 👁️ View Only

\- ❌ No Access



\---



\# Development Priority



Modul akan dikembangkan dengan urutan berikut:



1\. Authentication

2\. User Management

3\. Dashboard

4\. Customer Management

5\. Service Ticket

6\. Inventory Management

7\. Supplier Management

8\. Direct Sales (POS)

9\. Operational Expense

10\. Monitoring \& Reports

11\. Audit Log



\---



\# Summary



FFixiT-MS terdiri dari sebelas modul utama yang saling terintegrasi. Seluruh modul dirancang menggunakan konsep Role Based Access Control (RBAC) sehingga setiap pengguna hanya dapat mengakses fitur sesuai tanggung jawabnya.



Pengembangan dilakukan secara bertahap dengan prioritas pada modul inti yang mendukung operasional toko, yaitu autentikasi, manajemen pengguna, ticket service, inventory, dan point of sale.

