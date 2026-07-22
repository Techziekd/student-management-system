# 🎓 Student Management System

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white" alt="Python 3.10+">
  <img src="https://img.shields.io/badge/Django-5.2%20LTS-092E20?logo=django&logoColor=white" alt="Django 5.2">
  <img src="https://img.shields.io/badge/Database-SQLite-003B57?logo=sqlite&logoColor=white" alt="SQLite">
  <img src="https://img.shields.io/badge/UI-AdminLTE%203-00A65A" alt="AdminLTE 3">
  <img src="https://img.shields.io/badge/License-MIT-yellow" alt="MIT License">
</p>

A full-featured **Student Management System** built with **Django 5.2 LTS** and the **AdminLTE 3** dashboard theme. It ships three role-based portals — **HOD (Admin)**, **Staff**, and **Student** — covering courses, subjects, academic sessions, attendance, results, leave requests, and feedback, with interactive Chart.js analytics on every dashboard.

---

## ✨ Features

### 👑 HOD / Admin
- 📊 Summary dashboard — students, staff, courses, subjects, attendance vs. leave charts
- 👨‍🏫 Manage **Staff** (add / update / delete)
- 🧑‍🎓 Manage **Students** (add / update / delete, with profile photos)
- 📚 Manage **Courses**, **Subjects**, and **Session Years**
- 🗓️ View any subject's attendance records
- 💬 Review & reply to student/staff feedback
- ✅ Approve or reject student/staff leave applications

### 👨‍🏫 Staff / Teacher
- 📊 Personal dashboard — their students, subjects, attendance and leave charts
- 🗓️ Take and update student attendance per subject & session
- 📝 Add / update student results (exam + assignment marks)
- 🏖️ Apply for leave
- 💬 Send feedback to the HOD

### 🧑‍🎓 Student
- 📊 Personal dashboard — attendance breakdown per subject
- 🗓️ View own attendance by subject and date range
- 🎯 View results
- 🏖️ Apply for leave
- 💬 Send feedback to the HOD

---

## 🛠️ Tech Stack

| Layer      | Technology                                                    |
|------------|---------------------------------------------------------------|
| Backend    | Python 3.10+, Django 5.2 LTS                                  |
| Database   | SQLite (dev) — swappable via `DATABASES` in `settings.py`     |
| Frontend   | AdminLTE 3, Bootstrap 4, jQuery, Chart.js                     |
| Auth       | Custom email-based auth backend + role-routing middleware     |

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/Techziekd/student-management-system.git
cd student-management-system
```

### 2. Create and activate a virtual environment

**Windows**
```bash
python -m venv venv
venv\Scripts\activate
```

**macOS / Linux**
```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Set up the database

```bash
python manage.py migrate
```

### 5. Create the HOD / admin account

```bash
python manage.py createsuperuser
```

You'll be prompted for a username, **email**, and password — you log in with the **email**.

### 6. Run the development server

```bash
python manage.py runserver 8080
```

Open **http://127.0.0.1:8080** and sign in with the superuser email and password. (Any port works — `runserver` alone uses 8000.)

### 7. First steps after logging in

1. **Add a Session Year** (Manage Session → Add Session)
2. **Add a Course** (Manage Course → Add Course)
3. Then add Staff, Subjects, and Students — students require an existing course and session.

---

## 📁 Project Structure

```
student-management-system/
├── manage.py
├── requirements.txt
├── static/                        # AdminLTE theme, JS/CSS vendor assets
├── student_management_system/     # Project config (settings, root urls, wsgi/asgi)
└── student_management_app/
    ├── models.py                  # CustomUser (role-based) + domain models
    ├── EmailBackEnd.py            # Email/password authentication backend
    ├── LoginCheckMiddleWare.py    # Per-role route guarding
    ├── HodViews.py                # Admin portal views
    ├── StaffViews.py              # Staff portal views
    ├── StudentViews.py            # Student portal views
    ├── forms.py                   # Student add/edit forms (dynamic choices)
    ├── urls.py
    ├── migrations/
    └── templates/                 # base, login, hod/staff/student templates
```

---

## ⚙️ Configuration Notes

- `DEBUG = True` and a hardcoded `SECRET_KEY` are for **local development only** — set environment-specific values before any real deployment.
- `ALLOWED_HOSTS = ['*']` should be restricted in production.
- Uploaded profile photos are stored under `media/` (created automatically).

---

## 📄 License

Released under the [MIT License](LICENSE).
