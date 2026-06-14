🛒 My-shop Website (Flask)

A full-stack E-Commerce web application built using **Flask, SQLAlchemy, Jinja2, and JavaScript**.  
This project focuses on **backend architecture, database relationships, role-based access, and admin controls**.

🔗 GitHub Repository:  
https://github.com/DobariyaMayank1/my-shop

---

## 📌 Project Overview

This application allows:

- **Buyers** to browse, search, filter, and like products
- **Sellers** to add, update, manage, and hide their own products
- **Admins** to manage users and control platform access

The primary goal of this project is to demonstrate **clean Flask architecture**, **ORM usage**, **migrations**, and **real-world business logic** rather than UI design.

---

## ✨ Features

### 👤 Authentication & Roles
- User Registration
- Login & Logout
- Session-based authentication
- Password hashing
- CSRF protection
- Role-based access:
  - Buyer
  - Seller
  - Admin

---

### 🧑‍💼 Admin Panel
- View all users
- Update username & email
- Block / Activate users
- Prevent admin from being blocked
- Automatically **hide seller products when seller is blocked**
- Reactivate seller products when seller becomes active

---

### 🛍️ Product Management
- View all active products (LIFO order)
- Product status:
  - `active`
  - `hide`
- Sellers can:
  - Add products
  - Update products
  - Delete products
  - View only their own products
  - Hide / activate products
- Blocked sellers’ products are automatically hidden

---

### 🔍 Search & Filter
- Search products by name
- Filter by:
  - Category (Shirt, Pant, Shoes)
  - Gender (Men, Women, Kids)
  - Price range
- Hidden products never appear in results

---

### ❤️ Favorite / Like System
- Like & unlike products
- Favorites stored in database
- Favorite state persists after reload
- AJAX-based (Fetch API)
- No page reload required
- View all liked products

---

## 🧱 Database Models

### User
- id
- username (unique)
- email (unique)
- password (hashed)
- user_type (`buyer`, `seller`, `admin`)
- status (`active`, `block`)

---

### Product
- id
- product_name
- product_price
- product_image
- product_details
- product_category
- product_gender
- product_stock
- seller_id (ForeignKey → User)
- status (`active`, `hide`)

---

### UserProduct (Favorites)
- id
- user_id
- product_id

---

### Order
- id
- user_id
- product_id
- quantity

---

## 🗂️ Project Structure


```text
my-shop/
│
├── app/
│ ├── admin/
│ ├── auth/
│ ├── filter/
│ ├── home/
│ ├── interaction/
│ ├── models/
│ ├── payment/
│ ├── product/
│ ├── user/
├─├── static/
│    ├── uploads/
│    └── style.css
│ ├── templates/
│ ├── __init__.py/
│ ├── forms.py/
│ └── extensions.py
│
├── instance/
│ └── data.db
│
├── migrations/
│
│
├── .env
├── run.py
├── config.py
├── requirements.txt
└── README.md
```

---

---

## 🛠️ Tech Stack

| Layer        | Technology        |
|-------------|------------------|
| Backend     | Flask            |
| ORM         | SQLAlchemy       |
| Database    | SQLite           |
| Templates   | Jinja2           |
| Forms       | Flask-WTF        |
| Migrations  | Flask-Migrate    |
| Frontend    | HTML, CSS, JS    |
| AJAX        | Fetch API        |

---

## 🚀 How to Run the Project

### 1️⃣ Clone the Repository
```bash
git clone https://github.com/DobariyaMayank1/my-shop.git
```
```bash
cd my-shop

```

### 2️⃣ Create & Activate Virtual Environment

**macOS / Linux**

```bash
python3 -m venv .venv
```
```bash
source .venv/bin/activate
```

**Windows**

```bash
python -m venv .venv
```
```bash
.venv\Scripts\activate
```

### 3️⃣ Install Dependencies

```bash
pip install -r requirement.txt
```

---

## 🔐 Environment Variables

Create a `.env` file in the project root:

```env
SECRET_KEY=your_key
DATABASE_URL=sqlite:///data.db
MAIL_ID=your_gmail@gmail.com
MAIL_PASSWORD=your_email_app_password
```

⚠️ **Do not commit `.env` to Git**
It contains sensitive information.

---

### 4️⃣ Set Flask App Environment Variable

**macOS / Linux**

```bash
export FLASK_APP="app:create_app"
```

**Windows**

```bash
set FLASK_APP=app:create_app
```

---

## 🗄️ Database Migration

If `migrations/` folder does **not** exist (run once):

```bash
flask db init
```

Then run:

```bash
flask db stamp head
```
```bash
flask db migrate -m "initial migration"
```
```bash
flask db upgrade
```



---

## ▶️ Run the Application

```bash
flask run
```


Open your browser and visit:

```
http://127.0.0.1:5000
```

---

## 👤 User Flow

1. Open the application
2. Register as Buyer or Seller
3. Login
4. Browse all products
5. Search & filter products
6. Like favorite products ❤️
7. Sellers manage their products
8. View profile and favorites

---

## ❗ Error Handling

The application handles:

* Invalid login credentials
* Unauthorized access
* Invalid form submissions
* Product ownership validation
* Image upload validation

---

## 🔒 Security Notes

* Passwords are hashed
* Session-based authentication
* CSRF protection enabled
* `.env` excluded from version control

---

## 🚧 Future Improvements

* Product pagination
* Reviews & ratings
* Payment gateway integration
* Admin dashboard
* Improved UI/UX

---

## 👨‍💻 Author

**Mayank Dobariya**
GitHub 👉 [https://github.com/DobariyaMayank1/my-shop](https://github.com/DobariyaMayank1/my-shop)

⭐ *If you like this project, please give it a star!*
