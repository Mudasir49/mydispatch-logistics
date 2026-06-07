# 🚛 MyDispatch — Freight Dispatch & Logistics Management Platform

A full-stack **freight dispatch and logistics management web application** built with PHP, Laravel, and MySQL.
The platform connects **dispatchers, drivers, customers, and admins** in a unified system to manage freight loads, shipments, carriers, and payments.



---

## 🎯 What This Project Does

MyDispatch simulates a real-world freight dispatching business platform — similar to how companies like Uber Freight or LoadBoard operate. It manages the full lifecycle of a freight load from creation to delivery.

```
Customer creates load → Dispatcher assigns driver → Driver picks up → Delivery confirmed → Payment processed
```

---

## ✨ Features

### 👥 Multi-Role System
- **Admin** — Full system control, analytics, user management
- **Dispatcher** — Creates and assigns loads to drivers
- **Driver** — Views available loads, self-assigns, updates status
- **Customer** — Creates shipment requests, tracks deliveries

### 📦 Load Management
- Create freight loads with pickup/delivery locations, dates, weight, miles, rate
- Role-based load visibility (drivers see available + their assigned loads only)
- Full CRUD REST API for loads (`GET`, `POST`, `PUT`, `DELETE`)
- Load status workflow: `available → assigned → in_transit → delivered`
- Auto-generated load numbers

### 🚚 Carrier Management
- Carrier registration with MC number, DOT number, equipment type
- Carrier profile setup and verification

### 📊 Role-Based Dashboards
- **Admin:** Total users, loads, revenue, load status distribution, user role distribution
- **Driver:** Active loads, monthly earnings, total miles driven
- **Customer:** Active shipments, total spent, on-time delivery rate

### 🔔 Notifications System
- Unread notification count in header
- Per-user notification tracking

### 📄 Additional Pages
- Real-time shipment tracking page
- Services and pricing pages
- Contact form
- Blog (placeholder)
- Custom 404 and 500 error pages

### 🛡️ Security
- Session-based authentication
- Role-based access control on every API endpoint
- PDO prepared statements (SQL injection prevention)
- Unauthorized access blocked with 403 responses

---

## 🛠️ Tech Stack

**Backend (PHP Version)**

![PHP](https://img.shields.io/badge/PHP-777BB4?style=flat-square&logo=php&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)

**Backend (Laravel Version)**

![Laravel](https://img.shields.io/badge/Laravel-FF2D20?style=flat-square&logo=laravel&logoColor=white)
![PHP](https://img.shields.io/badge/PHP-777BB4?style=flat-square&logo=php&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)

**Frontend**

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)

---

## 📁 Project Structure

```
mydispatch-logistics/
│
├── index.php                      # Entry point — PHP router
├── config/
│   └── database.php               # PDO database connection
│
├── backend/
│   └── api/
│       ├── loads.php              # REST API — Load CRUD (GET/POST/PUT/DELETE)
│       └── users.php              # REST API — User management
│
├── functions/
│   ├── auth.php                   # Authentication helpers
│   ├── helpers.php                # General helper functions
│   └── logout.php                 # Logout handler
│
├── includes/
│   ├── header.php                 # Shared header + navigation
│   ├── navigation.php             # Nav component
│   └── footer.php                 # Shared footer
│
├── assets/
│   ├── css/
│   │   ├── style.css              # Main stylesheet
│   │   └── responsive.css        # Mobile responsive styles
│   └── js/
│       ├── auth.js                # Frontend auth logic
│       └── main.js                # Main JS
│
├── database/
│   └── install.php                # Database installer script
│
├── laravel_app/                   # Laravel version of the backend
│   └── app/Http/Controllers/
│       ├── AdminController.php
│       ├── AuthController.php
│       ├── DashboardController.php
│       ├── CarrierController.php
│       ├── LoadController.php
│       ├── DocumentsController.php
│       ├── BlogController.php
│       └── ContactController.php
│
├── deploy.sh                      # Linux deployment script
├── deploy.bat                     # Windows deployment script
└── DATABASE_SETUP_GUIDE.md        # Database setup instructions
```

---

## 🔌 REST API Endpoints

### Loads API — `backend/api/loads.php`

| Method | Action | Permission |
|--------|--------|------------|
| `GET /api/loads` | List all loads (role-filtered) | All roles |
| `GET /api/loads?id=X` | Get single load | All roles |
| `POST /api/loads` | Create new load | Admin, Customer |
| `PUT /api/loads` | Update load | Admin, Customer, Driver (limited) |
| `DELETE /api/loads?id=X` | Delete load | Admin only |

**Role-based filtering:**
- Drivers see only available loads + their assigned loads
- Customers see only their own loads
- Admin sees all loads

---

## 🚀 Setup & Installation

### Requirements
- XAMPP (PHP 8.0+, MySQL 5.7+)
- OR Laravel environment (PHP 8.1+, Composer)

### PHP Version Setup

**1. Clone the repo:**
```bash
git clone https://github.com/Mudasir49/mydispatch-logistics.git
```

**2. Move to XAMPP htdocs:**
```
C:\xampp\htdocs\mydispatch-logistics\
```

**3. Create database:**
- Open phpMyAdmin → Create database: `mydispatch_db`
- Run `database/install.php` in browser to auto-create tables

**4. Configure database:**

Edit `config/database.php`:
```php
$host = 'localhost';
$db   = 'mydispatch_db';
$user = 'root';
$pass = '';
```

**5. Open in browser:**
```
http://localhost/mydispatch-logistics/
```

### Laravel Version Setup

```bash
cd laravel_app
composer install
cp .env.example .env
php artisan key:generate
php artisan migrate
php artisan serve
```

---

## 👤 Test Accounts

After database setup, use these roles to test:

| Role | What you can do |
|------|----------------|
| Admin | Manage all users, loads, view analytics |
| Dispatcher | Create and assign loads to drivers |
| Driver | View available loads, self-assign, update status |
| Customer | Create shipment requests, track deliveries |

---

## 💡 Key Concepts Demonstrated

- Multi-role authentication and authorization
- RESTful API design (GET/POST/PUT/DELETE)
- Role-based access control (RBAC) at API level
- PDO prepared statements for security
- Laravel MVC architecture (Controllers, Models, Views)
- Full load lifecycle management
- Multi-dashboard analytics per user role
- Responsive frontend with custom CSS
- Deployment scripts (Linux + Windows)

---

## 📬 Contact

**Mudasir Ahmad**
📧 me.mudasirr@gmail.com
💼 [LinkedIn](https://www.linkedin.com/in/muhammad-mudasir-ahmad/)