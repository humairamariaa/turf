# 🏟️ Find Your Turf

> A web-based platform that makes it easy for players to discover, browse, and book sports turfs near them — and for turf owners to manage their venues and host tournaments.

---

## 📖 About The Project

**Find Your Turf** is a PHP + MySQL web application built as a university project. The idea is simple: finding and booking a turf shouldn't be a hassle. Whether you want to book a quick football slot with friends or organize a full-on tournament, this platform handles it all in one place.

The system supports three types of users — **Players (Users)**, **Turf Owners**, and **Admins** — each with their own dashboard and set of features.

---

## ✨ Features

### 👤 For Players
- Browse all available turfs with details like location, price, capacity, and operating hours
- Filter turfs by location, price range, capacity, and time slot
- Book a turf slot and pay online via **bKash**, **Nagad**, or **Rocket**
- View booking history
- Manage personal profile

### 🏢 For Turf Owners
- Register and list their turf with facilities, operating hours, and pricing
- View bookings made on their turf
- Request to host tournaments at their venue
- Manage their owner profile

### 🛠️ For Admins
- Approve or decline turf listing requests from owners
- Approve or decline tournament requests
- View all registered users and their details
- View all booked turfs across the platform
- Notification indicators for pending requests

---

## 🗂️ Project Structure

```
turf/
├── home.php                   # Landing page (public, no login needed)
├── login.php                  # Login page for all user types
├── signup.php                 # Player registration
├── signup_admin.php           # Admin registration
├── logout.php                 # Handles session logout
├── connect.php                # Database connection
│
├── user_dashboard.php         # Player dashboard — browse & book turfs
├── user_profile.php           # Player profile management
├── turf_history.php           # Player's booking history
├── submit_payment.php         # Handles payment & booking submission
├── success.php                # Booking success page
│
├── owner_dashboard.php        # Turf owner dashboard
├── owner_dashboard_login.php  # Owner login
├── owner_bookCheck.php        # View bookings on owner's turf
├── owner_tournament.php       # Owner submits tournament requests
├── tournament_history.php     # Tournament history view
│
├── admin_dashboard.php        # Admin dashboard
├── admin_dashboard1.php       # Admin dashboard (alternate/extended view)
├── admin_manage.php           # Manage turf listings
├── admin_tournament.php       # Manage tournament requests
├── turf_requests.php          # Approve/decline turf listing requests
├── admin_booked_turfs.php     # View all bookings platform-wide
├── admin_user_info.php        # View all registered users
├── admin_profile.php          # Admin profile
│
└── turf sql                   # MySQL database dump (import this to set up DB)
```

---

## 🗄️ Database

The database is called `turf` and contains the following tables:

| Table | Description |
|---|---|
| `users` | Registered players |
| `owners` | Turf owners |
| `admins` | Admin accounts |
| `turfs` | Turf listings (with status: pending/accepted/declined) |
| `turf_types` | Type, capacity, price, and slot duration per turf |
| `bookings` | All booking records with date, time slot, and status |
| `payments` | Payment records linked to bookings |
| `tournaments` | Approved tournament listings |
| `tournament_requests` | Tournament requests pending admin approval |

---

## ⚙️ Tech Stack

- **Backend:** PHP (with MySQLi)
- **Frontend:** HTML, CSS (vanilla), JavaScript
- **Database:** MySQL / MariaDB
- **Local Server:** XAMPP (Apache + MySQL)
- **Font:** Google Fonts — Poppins

---

## 🚀 Getting Started

### Prerequisites
- [XAMPP](https://www.apachefriends.org/) (or any local PHP/MySQL server)
- A browser

### Installation

1. **Clone or download the repo** into your XAMPP `htdocs` folder:
   ```
   C:\xampp\htdocs\turf\
   ```

2. **Import the database:**
   - Open [phpMyAdmin](http://localhost/phpmyadmin)
   - Create a new database named `turf`
   - Click **Import** and upload the `turf sql` file from the project root

3. **Check the database connection** in `connect.php`:
   ```php
   $servername = 'localhost';
   $USERNAME = 'root';
   $PASSWORD = '';       // change this if your MySQL has a password
   $DATABASE = 'turf';
   ```

4. **Start XAMPP** (make sure Apache and MySQL are running)

5. **Open the app** in your browser:
   ```
   http://localhost/turf/home.php
   ```

---

## 🔐 Default Credentials (from the SQL dump)

> These are seeded accounts included in the database dump, for testing purposes.

| Role | Username | Password |
|---|---|---|
| Admin | `Humaira` | *(hashed — reset via phpMyAdmin if needed)* |
| Owner | `ahmed` | *(hashed — reset via phpMyAdmin if needed)* |
| User | `humairaa` | *(hashed — reset via phpMyAdmin if needed)* |

You can also **sign up** fresh accounts directly through the app.

---

## 📱 User Roles & Login Flow

```
home.php
  └── login.php
        ├── role = Admin   → admin_dashboard.php
        ├── role = Owner   → owner_dashboard.php
        └── role = User    → user_dashboard.php
```

---

## 📸 Pages Overview

| Page | What it does |
|---|---|
| `home.php` | Hero landing page with video background, about section, and contact info |
| `user_dashboard.php` | Browse and filter turfs, open booking modal, pay and confirm |
| `owner_dashboard.php` | Manage turf listing, view bookings, request tournaments |
| `admin_dashboard.php` | Overview with pending notification badges, links to all admin tools |

---

## 💳 Supported Payment Methods

- **bKash**
- **Nagad**
- **Rocket**

Payment is submitted along with the booking. Users provide their phone number, transaction ID, and amount.

---

## 👥 Team / Contact

Built by:

- **Humaira** — [@humairamariaa](https://instagram.com/humairamariaa)
- **Ifaz** — [@ifaz_07](https://instagram.com/ifaz_07)
- **Upoma** — [@mir_upoma](https://instagram.com/mir_upoma)

---

## 📝 Notes

- This is an academic project built for learning purposes.
- Passwords are hashed using PHP's `password_hash()` with bcrypt.
- The app does **not** process real payments — users manually enter a transaction ID as proof of payment.
- Some pages may have minor bugs or unfinished features; this was a work-in-progress during development.

---

*Made with ⚽ and a lot of late nights.*
