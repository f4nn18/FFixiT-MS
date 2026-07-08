\# Entity Relationship Diagram (ERD)

FixiT Management System (FFixiT-MS)

\---

## Document Information

| Item        | Value                 |
| ----------- | --------------------- |
| Version     | 0.1                   |
| Author      | Muhammad Irfan Syafiq |
| Project     | FFixiT-MS             |
| Last Update | 2026-07-09            |
| Status      | Active                |

\---

# Overview

Dokumen ini menjelaskan rancangan database FFixiT-MS yang akan digunakan sebagai dasar pengembangan sistem.

Desain database mengikuti prinsip normalisasi untuk meminimalkan duplikasi data, menjaga integritas data, serta mempermudah pengembangan di masa mendatang.

\---

# Database Design Principles

Database dirancang dengan prinsip berikut.

\- Menggunakan Primary Key `id` pada setiap tabel.

\- Menggunakan Foreign Key untuk seluruh relasi.

\- Menggunakan `created\_at` dan `updated\_at`.

\- Soft Delete diterapkan pada tabel tertentu apabila diperlukan.

\- Menggunakan Audit Log untuk mencatat aktivitas penting.

\- Seluruh penamaan tabel menggunakan bentuk jamak (plural) dengan format snake_case.

Contoh:

```

users

customers

tickets

ticket\_photos

stock\_movements

```

---

\# Entity List

## Authentication

\### users

Menyimpan akun pengguna sistem.

\### roles

Daftar role pengguna.

\---

## Customer

\### customers

Menyimpan informasi customer.

\---

## Employee

\### employees

Data karyawan.

\---

## Service

\### tickets

Data utama service.

\### ticket_progresses

Riwayat progress pengerjaan.

\### ticket_photos

Evidence Before & After.

\### ticket_parts

Sparepart yang digunakan.

\### ticket_cancellations

Riwayat pembatalan tiket.

\### ticket_warranties

Riwayat garansi.

\---

## Inventory

\### suppliers

Data supplier.

\### categories

Kategori barang.

\### products

Master barang.

\### stock_movements

Riwayat keluar masuk stock.

\### purchase_transactions

Pembelian stock.

\### purchase_transaction_items

Detail pembelian.

\---

\## Sales

\### sales

Invoice penjualan.

\### sale_items

Detail barang yang dijual.

\---

## Operational

\### operational_expenses

Pengeluaran operasional.

\### expense_categories

Kategori pengeluaran.

\---

\## Audit

\### audit_logs

Riwayat aktivitas pengguna.

\---

# Entity Relationships

## User

```
Role
1
│
└────────────∞ Users
```

---

\## Customer

```
Customer
1
│
└────────────∞ Tickets
```

---

\## Employee

```
Employee
1
│
└────────────∞ Tickets (Technician)
```

---

\## Ticket

```
Ticket
1
├────────━∞ Ticket Progresses
├────────━∞ Ticket Photos
├────────━∞ Ticket Parts
├───────── 1 Ticket Warranty
└─────────0..1 Ticket Cancellation
```

---

\## Product

```
Category
1
│
└────────────∞ Products
```

---

```
Supplier
1
│
└────────────∞ Purchase Transactions
```

---

```
Purchase Transaction
1
│
└────────────∞ Purchase Transaction Items
```

---

```
Product
1
├────────━∞ Stock Movements
├────────━∞ Ticket Parts
└────────━∞ Sale Items
```

---

\## Sales

```
Sale
1
│
└────────────∞ Sale Items
```

---

# High Level Database Flow

```
   Customer
      │
      ▼
    Ticket
      │
      ├──────── Progress
      ├──────── Photos
      ├──────── Parts
      ├──────── Warranty
      └──────── Cancellation

    Parts
      │
      ▼
  Inventory
      │
      ▼
Stock Movement

   Ticket
      │
      ▼
Invoice (Sales)

   Invoice
      │
      ▼
   Payment

```

---

\# Naming Convention

\## Table

Menggunakan bentuk jamak.

Contoh:

```

customers

products

tickets

```

---

\## Primary Key

```

id

```

---

\## Foreign Key

```
customer_id
ticket_id
product_id
supplier_id
user_id
```

---

\## Timestamp

Menggunakan standar Laravel.

```
created_at
updated_at
```

---

# Notes

ERD ini menjadi acuan utama selama pengembangan FFixiT-MS.

Penambahan, penghapusan, atau perubahan entity hanya dapat dilakukan apabila terdapat perubahan pada Business Flow, Modules, atau kebutuhan bisnis yang telah disetujui.

Contoh kemungkinan entity pada versi berikutnya:

- notifications
- device_brands
- device_models
- service_checklists
- payment_methods
- warranty_claims

Seluruh perubahan wajib memperhatikan konsistensi terhadap:

- BusinessFlow.md
- Modules.md
- Roles.md
- AIInstructions.md

Penambahan entity harus tetap mengikuti Business Flow dan Module yang telah ditetapkan sebelumnya.

\---

\# Summary

Database FFixiT-MS dirancang menggunakan pendekatan modular sehingga setiap modul memiliki entity yang terpisah namun saling terhubung melalui relasi.

# Summary

Database FFixiT-MS dirancang menggunakan pendekatan modular sehingga setiap modul memiliki entity yang terpisah namun saling terhubung melalui relasi.

Dokumen ini menjadi acuan utama dalam pembuatan:

- Laravel Migration
- Eloquent Model
- Database Seeder
- Factory
- Foreign Key Relationship
- Business Logic yang berkaitan dengan database

Seluruh implementasi database harus tetap konsisten dengan BusinessFlow.md, Modules.md, dan AIInstructions.md.
