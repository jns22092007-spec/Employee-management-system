# Employee Management System — Project Report

## Problem statement

Manual employee records are difficult to search, update, validate, and keep consistent. This application provides a secure, centralized system in which authorized users can manage employee information and use the same data through a web interface or REST API.

## Objectives

The system implements all CRUD operations, reliable data validation, search and filtering, responsive pages, authentication, persistent database storage, API access, automated tests, and clear installation documentation.

## Users and scope

HR staff and administrators can sign in, view workforce statistics, search/filter employees, and add, update or remove records. API clients can perform the same operations after authentication.

## Technology stack

| Layer | Technology |
|---|---|
| Frontend | HTML5, CSS3, JavaScript, Django templates |
| Backend | Python, Django 5, Django REST Framework |
| Database | SQLite through Django ORM |
| Testing | Django TestCase, DRF APIClient, Postman |
| Version control | Git/GitHub ready |

## Architecture and workflow

The browser sends a request to a Django URL. A view enforces authentication and processes an `EmployeeForm`. The form validates input, and the model uses Django ORM to persist it in SQLite. Templates render results back to the browser. REST requests pass through a DRF ViewSet and serializer before using the same model and database.

## Database design

The `Employee` table uses an automatic integer primary key. `employee_id` and `email` are unique. Required attributes are first name, last name, phone, department, designation, salary, joining date, and status. Creation and modification timestamps are maintained automatically.

## CRUD implementation

| Function | Web interface | REST API |
|---|---|---|
| Create | Add employee form | `POST /api/employees/` |
| Read | Dashboard table | `GET /api/employees/` |
| Update | Edit employee form | `PUT/PATCH /api/employees/{id}/` |
| Delete | Confirmation page | `DELETE /api/employees/{id}/` |

## Validation and exception handling

Employee IDs must use `EMP` plus 3–9 digits. Emails are validated and unique. Indian mobile numbers are checked. Salary cannot be negative, joining dates cannot be in the future, mandatory fields cannot be blank, and department/status values are limited to defined choices. Forms and APIs return field-specific validation errors; invalid record IDs return HTTP 404.

## Testing results

The included automated tests verify protected access, valid web-form creation, authenticated API listing, partial update, and deletion. `python manage.py test` completes with all tests passing. Additional manual cases are documented in the README testing checklist and can be executed with the included Postman collection.

## Security

Authentication, CSRF protection, session security, ORM parameterization, input validation, and environment-based settings are used. Secrets, local databases, virtual environments, and editor artifacts are excluded from Git.

## Challenges and solutions

The web list and API router initially generated the same URL name. Giving API routes an explicit `employee-api` basename removed the collision. Shared model validation keeps data rules consistent across the web and API layers.

## Future enhancements

Potential additions include role-based permissions, attendance and leave modules, payroll, CSV/PDF export, employee photographs, audit history, dashboards, and email notifications.

