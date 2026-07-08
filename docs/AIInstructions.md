# AI Development Instructions

FixiT Management System (FFixiT-MS)

---

## Document Information

| Item        | Value                 |
| ----------- | --------------------- |
| Version     | 0.1                   |
| Author      | Muhammad Irfan Syafiq |
| Project     | FFixiT-MS             |
| Last Update | 2026-07-09            |
| Status      | Active                |

---

# Purpose

Dokumen ini berisi aturan yang wajib diikuti oleh AI Assistant selama membantu proses pengembangan FFixiT-MS.

AI bertindak sebagai Developer yang membantu implementasi, bukan sebagai System Analyst yang mengubah proses bisnis.

---

# Technology Stack

Framework

- Laravel 12

Programming Language

- PHP 8.5

Database

- MySQL 8.4

Frontend

- HTML5
- Bootstrap 5
- JavaScript (Vanilla)

Development Tools

- Visual Studio Code
- Git
- Composer

---

# Required Reading Order

Sebelum membuat kode, AI WAJIB membaca dokumen berikut.

1. README.md
2. BusinessFlow.md
3. Roles.md
4. Modules.md
5. Roadmap.md
6. ERD.md
7. CodingStandards.md
8. UIGuidelines.md

---

# Development Rules

AI harus:

- Mengikuti Business Flow.
- Mengikuti Role Based Access Control (RBAC).
- Mengikuti struktur database pada ERD.
- Menggunakan Laravel Convention.
- Menggunakan Bootstrap 5.
- Menghasilkan kode yang bersih dan mudah dibaca.

AI tidak boleh:

- Mengubah Business Flow tanpa persetujuan.
- Menambah role baru.
- Mengubah nama tabel.
- Mengubah nama kolom tanpa persetujuan.
- Mengubah relasi database.
- Menambahkan library pihak ketiga tanpa alasan yang jelas.

---

# UI Rules

Saat diminta membuat UI:

- Bootstrap 5 Only
- Responsive Layout
- Consistent Design
- Sidebar Layout
- Clean Dashboard
- Professional Appearance

---

# Backend Rules

Saat membuat Backend:

- Gunakan MVC Laravel.
- Gunakan Eloquent ORM.
- Gunakan Form Request Validation jika diperlukan.
- Hindari Query Builder apabila Eloquent sudah mencukupi.

---

# Database Rules

AI harus mengikuti ERD.

Tidak boleh membuat:

- tabel baru
- foreign key baru
- relasi baru

tanpa persetujuan terlebih dahulu.

---

# Business Rules

AI wajib mengikuti aturan berikut.

- CS membuat Ticket.
- Teknisi hanya mengerjakan Ticket.
- IT melakukan Approval Cancel Ticket.
- Inventory berkurang setelah transaksi.
- Tanda Terima dicetak saat Ticket dibuat.
- Invoice dibuat setelah Service selesai.

AI should never guess business rules.

If documentation is unclear,
ask for clarification before implementation.

---

# If Something Is Missing

Apabila AI menemukan kebutuhan baru:

JANGAN langsung mengimplementasikan.

Sebaliknya:

1. Jelaskan alasannya.
2. Berikan usulan.
3. Tunggu persetujuan.

---

# Goal

Seluruh implementasi harus konsisten dengan dokumentasi FFixiT-MS dan mudah dipelihara pada pengembangan berikutnya.
