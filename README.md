## Project Overview
The **Sales Management System** is a web-based application built with **Laravel 10** and **PHP 8.1**, designed to streamline sales operations for businesses.  
It provides functionalities for managing **customers, suppliers, products, categories, and sales transactions**, along with real-time dashboards for monitoring sales performance.  
The system uses **MySQL** for database management and **Vite + npm** for frontend assets.  

---

## Objectives
- Provide an intuitive interface for managing sales data efficiently.
- Track inventory and sales performance for better decision-making.
- Simplify management of customers, suppliers, and product categories.
- Generate useful insights and reports.

---

## Features / Functionality
- **Dashboard**: View total sales, sales count, top products, and low stock items.
- **Customer Management**: Add, edit, view, delete customers.
- **Supplier Management**: Add, edit, view, delete suppliers.
- **Product Management**: Add, edit, view, delete products.
- **Category Management**: Add, edit, view, delete categories.
- **Sales Transactions**: Record and manage sales with totals and reports.
- **Responsive Design**: Accessible on desktop and mobile devices.

---

## Installation Instructions

1. **Clone the repository**
   ```bash
   git clone https://github.com/jascv/laravel-sales-project.git
   cd laravel-sales-project
Install PHP dependencies

bash
Copy code
composer install
Install Node.js dependencies

bash
Copy code
npm install
npm run dev
Configure environment

bash
Copy code
cp .env.example .env
Update .env with your database credentials:

env
Copy code
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=mysales
DB_USERNAME=root
DB_PASSWORD=
Generate application key

bash
Copy code
php artisan key:generate
Run migrations and seed the database

bash
Copy code
php artisan migrate --seed
Serve the application

bash
Copy code
php artisan serve
Access your app at: http://127.0.0.1:8000

Usage
Navigate to the dashboard to view sales statistics.

Manage customers, suppliers, products, and categories via the sidebar menu.

Record sales transactions and manage existing entries.

Use edit and delete actions to update or remove records.

## Code Snippets
DashboardController

php
Copy code
namespace App\Http\Controllers;

use App\Models\Sale;
use App\Models\Product;

class DashboardController extends Controller
{
    public function index()
    {
        $totalSales = Sale::sum('total_price');
        $salesCount = Sale::count();
        $topProducts = Product::orderByDesc('stock')->take(5)->get();
        $lowStock = Product::where('stock', '<', 5)->get();

        return view('dashboard.index', compact('totalSales','salesCount','topProducts','lowStock'));
    }
}
Customers Blade Template

blade
Copy code
@foreach($customers as $customer)
<tr>
    <td>{{ $customer->name }}</td>
    <td>{{ $customer->contact ?? '-' }}</td>
    <td>{{ $customer->email ?? '-' }}</td>
    <td>
        <a href="{{ route('customers.edit', $customer->id) }}">Edit</a>
        <form action="{{ route('customers.destroy', $customer->id) }}" method="POST" style="display:inline">
            @csrf
            @method('DELETE')
            <button type="submit">Delete</button>
        </form>
    </td>
</tr>
@endforeach

## Contributor
Cervania, Jaslyn Joy N.

License
Developed for DMMMSU System Integration and Architecture 2 (AY 2025-26).
