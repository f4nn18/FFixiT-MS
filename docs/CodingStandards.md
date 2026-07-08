# Coding Standards

FixiT Management System (FFixiT-MS)

---

## Document Information

|-------------|-----------------------|
| Version | 0.1 |
| Author | Muhammad Irfan Syafiq |
| Project | FFixiT-MS |
| Last Update | 2026-07-08 |
| Status | Draft |
|-------------|-----------------------|

---

# Purpose

Dokumen ini menjadi standar penulisan kode selama pengembangan FFixiT-MS.

---

# PHP Standard

Mengikuti:

- PSR-12

---

# Naming Convention

## Controller

Gunakan:

CustomerController

TicketController

InventoryController

SupplierController

UserController

---

## Model

Gunakan Singular.

Contoh:

Customer

Ticket

Product

Supplier

User

---

## Migration

Gunakan Laravel Standard.

Contoh:

create_customers_table

create_products_table

create_tickets_table

---

## Table

Gunakan:

snake_case

plural

Contoh:

customers

products

ticket_parts

stock_movements

---

## Column

Gunakan:

snake_case

Contoh:

customer_name

ticket_status

estimated_cost

created_at

updated_at

---

## Variable

Gunakan:

camelCase

Contoh:

customerData

ticketStatus

totalPrice

---

## Function

Gunakan:

camelCase

Contoh:

storeTicket()

finishService()

calculateStock()

---

# Route Naming

Gunakan Resource Route.

Contoh:

customers.index

customers.create

customers.store

customers.edit

customers.update

customers.destroy

---

# Folder Structure

Ikuti struktur standar Laravel.

Jangan mengubah struktur folder framework.

---

# Comments

Gunakan komentar hanya jika diperlukan.

Kode harus mudah dipahami tanpa komentar berlebihan.

---

# Validation

Selalu lakukan validasi terhadap input pengguna.

---

# Security

Gunakan:

- CSRF Protection
- Validation
- Authorization
- Authentication

Jangan mempercayai input dari client.

---

# Git Commit Convention

Gunakan format berikut.

feat:

fix:

docs:

style:

refactor:

test:

chore:

Contoh:

feat: add customer management

fix: resolve ticket approval issue

docs: update erd documentation

---

# Code Quality

Kode harus:

- Mudah dibaca
- Konsisten
- Tidak duplikasi
- Mudah dipelihara

---

# Goal

Kode FFixiT-MS harus mudah dipahami bahkan oleh developer baru yang bergabung di kemudian hari.
