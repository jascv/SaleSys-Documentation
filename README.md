# Laravel Sales Management System 

This repository is a **ready-to-upload GitHub template** for a Sales Management System built with Laravel.
It is a project skeleton (no `vendor/`) that includes:

- Products, Sales, Customers, Suppliers, Categories tables
- Models with Eloquent relationships
- Controllers with CRUD for Products, Sales, Customers, Suppliers, Categories
- Tailwind-based Blade UI (simple dashboard + pages)
- Migrations and Seeders (sample data)
- Instructions to finish setup locally

## How to use

1. Clone this repo to your machine.
2. Ensure you have PHP, Composer, Node.js & npm installed.
3. From project root:
   ```bash
   composer install
   cp .env.example .env
   php artisan key:generate
   # set DB credentials in .env
   php artisan migrate --seed
   npm install
   npm run dev
   php artisan serve
   ```
4. Visit `http://127.0.0.1:8000`

> NOTE: This is a template skeleton. You still need to run `composer install` to install Laravel core and dependencies.

## Included features
- Products (CRUD)
- Sales (create sales with product selection; stock updates)
- Customers (CRUD)
- Suppliers (CRUD)
- Categories (CRUD; products belong to categories)
- Simple dashboard with total sales, top products, low stock list
- Tailwind CSS layout

## Folder Structure
app/Models           # Eloquent models (Category, Supplier, Customer, Product, Sale)
app/Http/Controllers # Controllers for CRUD operations and business logic
resources/views      # Blade templates for UI
routes/web.php       # Route definitions
database/migrations  # Database schema
database/seeders     # Sample data (categories, suppliers, customers, products, sales)

## Database Schema
categories: id, name, description
suppliers: id, name, contact_info, address
customers: id, name, contact_info, email
products: id, name, category_id, supplier_id, price, stock_quantity
sales: id, customer_id, product_id, quantity, total_price, date

## Contributors
Cervania, Jaslyn Joy N.
Developed for DMMMSU System Integration and Architecture 2 (AY 2025-26).
