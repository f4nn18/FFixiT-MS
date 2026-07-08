\# Development Roadmap

FixiT Management System (FFixiT-MS)

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

Roadmap ini menjadi panduan pengembangan FFixiT-MS dari tahap dokumentasi hingga versi stabil (v1.0).

Setiap milestone disusun berdasarkan prioritas pengembangan sehingga modul yang memiliki dependensi tinggi akan dikerjakan lebih dahulu.

\---

\# Development Strategy

Pengembangan dilakukan secara bertahap dengan prinsip:

\- Foundation First

\- Modular Development

\- One Module at a Time

\- Continuous Documentation

\- Git Version Control

Setiap modul harus memenuhi tahapan berikut:

```

Planning

&#x20;   ↓

Documentation

&#x20;   ↓

Database Design

&#x20;   ↓

Implementation

&#x20;   ↓

Testing

&#x20;   ↓

Git Commit

&#x20;   ↓

Git Push

```

\---

\# Milestones

\## v0.1 — Project Foundation ✅

\### Objectives

Membangun pondasi proyek.

\### Scope

\- Git Repository

\- Project Structure

\- Development Environment

\- Business Flow Documentation

\- Roles Documentation

\- Modules Documentation

\- Roadmap Documentation

\- ERD Documentation

Status

```

In Progress

```

\---

\## v0.15

UI Prototype

Wireframe

Bootstrap Prototype

Navigation Review

\---

\## v0.2 — Authentication \& User Management

\### Objectives

Membangun sistem autentikasi dan manajemen pengguna.

\### Features

\- Login

\- Logout

\- Session Management

\- Role Based Access Control (RBAC)

\- User Management

\- Employee Management

\- Reset Password

\- Activate / Deactivate User

\---

\## v0.3 — Dashboard

\### Objectives

Membangun dashboard untuk setiap role.

\### Features

\- Dashboard IT

\- Dashboard Kepala Toko

\- Dashboard Admin Gudang

\- Dashboard CS

\- Dashboard Teknisi

\---

\## v0.4 — Customer Management

\### Objectives

Mengelola data customer.

\### Features

\- Customer List

\- Add Customer

\- Edit Customer

\- Customer Detail

\- Service History

\- Sales History

\---

\## v0.5 — Service Ticket

\### Objectives

Mengelola seluruh proses service.

\### Features

\- Create Ticket

\- Print Service Receipt

\- Assign Technician

\- Diagnosis

\- Customer Approval

\- Progress Service

\- Request Sparepart

\- Finish Service

\- Generate Service Invoice

\- Warranty History

\- Ticket Cancellation Request

\---

\## v0.6 — Inventory Management

\### Objectives

Mengelola inventory toko.

\### Features

\- Supplier

\- Master Barang

\- Stock Saat Ini

\- Barang Masuk

\- Barang Keluar

\- Stock Opname

\- Stock Adjustment

\- Stock Movement

\---

\## v0.7 — Direct Sales (POS)

\### Objectives

Mengelola penjualan sparepart.

\### Features

\- Sales Invoice

\- Payment

\- Print Invoice

\- Sales History

\---

\## v0.8 — Operational Expense

\### Objectives

Mengelola pengeluaran operasional toko.

\### Features

\- Expense Category

\- Add Expense

\- Edit Expense

\- Expense History

\---

\## v0.9 — Monitoring \& Reports

\### Objectives

Menyediakan informasi operasional toko secara real-time.

\### Features

\- Revenue Dashboard

\- Ticket Monitoring

\- Inventory Monitoring

\- KPI Monitoring

\- Operational Expense Summary

\---

\## v1.0 — Stable Release

\### Objectives

Menyelesaikan seluruh modul utama.

\### Features

\- Audit Log

\- Bug Fix

\- UI Improvement

\- Performance Optimization

\- Documentation Update

\- Production Ready

\---

\# Development Workflow

Setiap fitur mengikuti alur berikut:

```

Requirement



↓



Analysis



↓



Design



↓



Database



↓



Backend



↓



Frontend



↓



Testing



↓



Documentation



↓



Commit



↓



Push

```

\---

\# Git Commit Convention

Jenis commit yang digunakan selama pengembangan.

| Prefix | Description |

|----------|-------------|

| feat | Menambahkan fitur baru |

| fix | Memperbaiki bug |

| docs | Perubahan dokumentasi |

| style | Perubahan tampilan atau formatting |

| refactor | Perbaikan struktur kode tanpa mengubah fungsi |

| chore | Pekerjaan pendukung (setup, dependency, dll.) |

| test | Penambahan atau perubahan testing |

Contoh:

```

feat: add customer management



fix: resolve inventory stock calculation



docs: update business flow



refactor: simplify ticket service



chore: configure laravel project

```

\---

\# Long-Term Vision

Setelah versi 1.0 selesai, FFixiT-MS dapat dikembangkan dengan fitur tambahan seperti:

\- Barcode / QR Code

\- WhatsApp Notification

\- Email Notification

\- Purchase Order

\- Multi Branch Support

\- Finance Module

\- HR Module

\- Mobile Technician App

\- Customer Portal

\- API Integration

\---

\# Summary

FFixiT-MS dikembangkan menggunakan pendekatan modular sehingga setiap milestone dapat diselesaikan secara mandiri tanpa mengganggu modul lain.

Roadmap ini menjadi acuan utama selama proses pengembangan dan dapat diperbarui sesuai kebutuhan proyek.
