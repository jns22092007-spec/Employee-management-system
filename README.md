# Employee Management System

A responsive full-stack CRUD application for maintaining employee records. It supports secure login, employee creation, listing, editing and deletion, search/filtering, validation, an admin panel, and a REST API.

## Technology stack

- Frontend: HTML5, CSS3, JavaScript, Django templates
- Backend: Python, Django, Django REST Framework
- Database: SQLite (easily configurable for MySQL/PostgreSQL)
- Testing: Django TestCase and DRF APIClient

## Features

- Authenticated employee dashboard with summary statistics
- Create, read, update and delete employee records
- Search by ID, name, email or designation
- Filter by department and employment status
- Client- and server-side form validation
- Unique employee IDs and email addresses
- Responsive desktop/mobile interface
- REST API with search, ordering and browsable documentation
- Django admin panel
- Automated UI/authentication and API CRUD tests

## Installation and execution

```bash
cd employee-management
python -m venv .venv
```

Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
pip install -r requirements.txt
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

If PowerShell blocks activation, run `.venv\Scripts\python.exe -m pip install -r requirements.txt` and replace `python` in later commands with `.venv\Scripts\python.exe`.

Open `http://127.0.0.1:8000/`, choose **Create an account**, register, and use the application. No terminal account creation is required. A superuser is needed only for access to `/admin/` and can optionally be created with `python manage.py createsuperuser`.

## REST API

Authentication uses the Django session login. Visit `/api-auth/login/` or log into the web application first.

| Operation | Method | Endpoint |
|---|---|---|
| Create | POST | `/api/employees/` |
| Read all | GET | `/api/employees/` |
| Read one | GET | `/api/employees/{id}/` |
| Update | PUT/PATCH | `/api/employees/{id}/` |
| Delete | DELETE | `/api/employees/{id}/` |

Search example: `/api/employees/?search=engineering`. Ordering example: `/api/employees/?ordering=-salary`.

## Run tests

```bash
python manage.py test
```

## Database design

The `Employee` entity contains: database ID (primary key), employee ID (unique), first name, last name, email (unique), phone, department, designation, salary, joining date, status, created time and updated time.

## Architecture

Browser UI → Django views/forms → Employee model → Django ORM → SQLite

API client → DRF ViewSet/serializer → Employee model → Django ORM → SQLite

## Security and quality

The project uses authentication, CSRF protection, ORM queries, server-side validation, environment-based settings, and no committed credentials. For production, set `DJANGO_SECRET_KEY`, set `DJANGO_DEBUG=False`, configure allowed hosts, and use PostgreSQL or MySQL.

## Testing checklist

- Create: valid, blank, duplicate and invalid data
- Read: empty and populated database
- Update: valid and invalid record IDs
- Delete: valid and invalid record IDs with confirmation
- Search/filter: matching and empty results
- Authentication: protected pages redirect anonymous users
- Responsive layout: desktop, tablet and mobile
- API: GET, POST, PATCH and DELETE using Postman or the browsable API

## Future enhancements

Role-based access, profile photographs, attendance and leave management, payroll reports, CSV/PDF export, audit logs, and email notifications.
