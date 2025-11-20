# djangoproject — Simple Django Blog Demo

A small Django demo project that implements a blog app with post listing, detail, create/edit, and basic admin integration. This repository is intended as a compact example for learning and local development.

## Features

- Simple blog app in `blog/` with models, views, forms and templates
- Admin integration for managing posts
- User authentication views (login/logout) using Django's built-in system
- Static assets under `static/` and templates under `templates/`

## Requirements

- Python 3.10+ (project was created and tested with Python 3.11)
- Django (see `requirements.txt` for exact version)

## Quickstart (Windows PowerShell)

1. Create and activate a virtual environment (if you don't have one):

```powershell
python -m venv myenv
.\myenv\Scripts\Activate.ps1
```

2. Install dependencies:

```powershell
pip install -r requirements.txt
```

3. Run database migrations:

```powershell
python manage.py migrate
```

4. Create a superuser for the admin site:

```powershell
python manage.py createsuperuser
```

5. Run the development server:

```powershell
python manage.py runserver
```

Open `http://127.0.0.1:8000/` in your browser.

## Running Tests

Run the Django test suite:

```powershell
python manage.py test
```

## Static Files (Production)

Collect static assets before deploying:

```powershell
python manage.py collectstatic --noinput
```

## Environment & Configuration

The project uses Django settings in `mysite/settings.py`. For production, set the following environment variables or equivalent configuration:

- `SECRET_KEY` — keep this secret in production
- `DEBUG` — set to `False` in production
- `ALLOWED_HOSTS` — list of allowed hostnames
- Database connection settings — replace the default SQLite if needed

For simple deployments consider setting up a WSGI server (e.g., Gunicorn) behind a reverse proxy (Nginx). On Windows, use a production-ready setup appropriate for your host.

### MySQL configuration

This project can use MySQL as its database. The Django settings have been updated to read MySQL credentials from environment variables. You can either install the `mysqlclient` package (recommended) or use `PyMySQL` (pure-Python driver).

- Install with `PyMySQL` (recommended, may require build tools on Windows):


```powershell
pip install PyMySQL
```

Set environment variables (PowerShell example):

```configuration at setting.py Change accourding to your requirement
MYSQL_DATABASE = "siteblog"
MYSQL_USER = "root"
MYSQL_PASSWORD = "root"
MYSQL_HOST = "127.0.0.1"
MYSQL_PORT = "3306"
```

Create the database in MySQL (example using MySQL CLI):

```powershell
mysql -u root -p -e "CREATE DATABASE siteblog CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;"
```

Run migrations and start the server:

```powershell
python manage.py migrate
python manage.py runserver
```

If you'd rather keep using SQLite locally, set the environment variable `DJANGO_DB_ENGINE` to `django.db.backends.sqlite3` and the project will fall back to the SQLite example (see `mysite/settings.py`).

## Project Structure

- `mysite/` — core Django project settings, URLs and WSGI/ASGI
- `blog/` — blog app (models, views, templates, forms, tests)
- `templates/` — shared templates (including registration/login)
- `static/` — static assets (CSS, icons)
- `requirements.txt` — pinned Python dependencies

## Useful Commands

- `python manage.py makemigrations` — create new migrations after model changes
- `python manage.py migrate` — apply migrations
- `python manage.py createsuperuser` — create admin user
- `python manage.py runserver` — run development server

## Notes

- This repo includes a `myenv/` virtual environment folder. You can remove it and create your own environment (recommended).
- The sample is intended for learning and local development; do not use the default settings in production without reviewing security best practices.

## License

This project is provided as-is for demonstration and learning purposes. Modify and reuse as you like.
