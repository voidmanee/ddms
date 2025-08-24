# District Device Management System

A Django-based web application for managing device inventory, assignments, repairs, and damage reports within a district or organization.

## Features

- Device inventory management
- Device assignment tracking
- Cart/checkout system for device distribution
- Damage report management
- Device repair tracking
- Import/export functionality for bulk data operations
- Admin interface for system management

## Prerequisites

Before setting up the project locally, ensure you have the following installed:

- **Python 3.8+** ([Download Python](https://python.org/downloads/))
- **pip** (Python package installer - comes with Python)
- **Git** ([Download Git](https://git-scm.com/downloads))
- **Virtual environment tool** (venv, virtualenv, or conda)

## Local Setup Instructions

### 1. Clone the Repository

```bash
git clone <your-repository-url>
cd district-device-system
```

### 2. Create and Activate Virtual Environment

**On Windows:**
```bash
python -m venv venv
venv\Scripts\activate
```

**On macOS/Linux:**
```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Environment Configuration

Create a `.env` file in the root directory and add the following variables:

```env
SECRET_KEY=your-secret-key-here
DEBUG=True
DATABASE_URL=sqlite:///db.sqlite3
ALLOWED_HOSTS=localhost,127.0.0.1
```

**Generate a new SECRET_KEY:**
```bash
python -c "from django.core.management.utils import get_random_secret_key; print(get_random_secret_key())"
```

### 5. Database Setup

Navigate to the Django project directory:
```bash
cd device_district
```

Run migrations to set up the database:
```bash
python manage.py makemigrations
python manage.py migrate
```

### 6. Create Superuser (Admin Account)

```bash
python manage.py createsuperuser
```

Follow the prompts to create an admin account for accessing the Django admin interface.

### 7. Collect Static Files

```bash
python manage.py collectstatic --noinput
```

### 8. Run the Development Server

```bash
python manage.py runserver
```

The application will be available at: `http://127.0.0.1:8000/`

## Accessing the Application

- **Main Application:** `http://127.0.0.1:8000/`
- **Admin Interface:** `http://127.0.0.1:8000/admin/`
- **Device Management:** `http://127.0.0.1:8000/device_management/`

## Application Structure

```
district-device-system/
├── device_district/          # Django project root
│   ├── device_district/      # Project configuration
│   │   ├── settings.py       # Django settings
│   │   ├── urls.py          # URL routing
│   │   └── wsgi.py          # WSGI configuration
│   ├── device_management/    # Main application
│   │   ├── models.py        # Database models
│   │   ├── views.py         # View functions
│   │   ├── forms.py         # Django forms
│   │   ├── admin.py         # Admin configuration
│   │   ├── urls.py          # App-specific URLs
│   │   └── templates/       # HTML templates
│   ├── static/              # Static files (CSS, JS, images)
│   ├── media/               # User uploaded files
│   └── manage.py            # Django management script
└── requirements.txt         # Python dependencies
```

## Key Features & Usage

### Device Management
- Add, edit, and delete device records
- Track device assignments to users/locations
- Monitor device status (available, assigned, damaged, under repair)
- Bulk import/export device data using CSV/Excel files

### Cart System
- Create carts for device distribution
- Add/remove devices from carts
- Process cart checkouts for device assignments

### Damage Reports
- Report damaged devices
- Track repair status
- View damage report history

### Import/Export
- Import device data from CSV/Excel files
- Export device lists and reports
- Bulk operations for large datasets

## Common Commands

### Development
```bash
# Run development server
python manage.py runserver

# Create new migrations after model changes
python manage.py makemigrations

# Apply migrations
python manage.py migrate

# Create superuser
python manage.py createsuperuser

# Collect static files
python manage.py collectstatic

# Access Django shell
python manage.py shell
```

### Database Management
```bash
# Reset database (WARNING: This will delete all data)
rm db.sqlite3
python manage.py migrate

# Load sample data (if fixtures are available)
python manage.py loaddata fixture_name.json
```

## Dependencies

The project uses the following main packages:

- **Django 5.2.4** - Web framework
- **django-import-export 4.3.8** - Import/export functionality for admin
- **tablib 3.8.0** - Data manipulation library
- **diff-match-patch 20241021** - Text comparison utilities

## Troubleshooting

### Common Issues

**1. ModuleNotFoundError**
- Ensure virtual environment is activated
- Run `pip install -r requirements.txt`

**2. Database errors**
- Delete `db.sqlite3` and run migrations again
- Check for migration conflicts: `python manage.py showmigrations`

**3. Static files not loading**
- Run `python manage.py collectstatic`
- Check `STATIC_URL` and `STATIC_ROOT` in settings.py

**4. Permission errors**
- Ensure proper file permissions
- On Unix systems: `chmod +x manage.py`

### Development Tips

- Use `DEBUG=True` in development
- Set `DEBUG=False` in production
- Check Django logs for detailed error messages
- Use Django admin interface for quick data management

## Production Deployment

For production deployment:

1. Set `DEBUG=False` in settings
2. Configure proper database (PostgreSQL/MySQL recommended)
3. Set up web server (nginx + gunicorn/uwsgi)
4. Configure static files serving
5. Set up SSL/HTTPS
6. Use environment variables for sensitive settings

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Run tests (if available)
5. Submit a pull request

## License

MIT License

