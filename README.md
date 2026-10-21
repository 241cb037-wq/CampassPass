# CampusPass – Student Opportunity & Achievement Passport

CampusPass is a Django full-stack mini project for maintaining student achievements and discovering career-building opportunities in one place.

## Problem statement
Students often keep certificates, project records, internship details, and opportunity applications across different places. CampusPass provides one student-owned digital passport and a staff review workflow to organize records and track verification.

## Main features
- Student registration, login, and logout
- Student profile management
- Achievement CRUD with proof-file upload and verification status
- Staff-only achievement approval/rejection with feedback and notifications
- Opportunity listing, search, type filtering, and pagination
- Track opportunity applications and withdraw them
- Dashboard statistics, recent activity, and upcoming deadlines
- Achievement CSV export
- Django admin for managing users and records

## Technology
- Python and Django
- PostgreSQL (default database)
- HTML, CSS, Bootstrap 5, JavaScript
- Django ORM and migrations

## Requirements
- Python 3.10+
- PostgreSQL 14+ recommended
- pip

## Setup on Windows (PowerShell or CMD)
1. Extract this project folder and open a terminal inside `CampusPass`.
2. Create and activate a virtual environment:
   ```bat
   py -m venv venv
   venv\Scripts\activate
   ```
3. Install dependencies:
   ```bat
   python -m pip install --upgrade pip
   pip install -r requirements.txt
   ```
4. Create a PostgreSQL database named `campuspass_db` and set your database credentials. For CMD:
   ```bat
   set DB_NAME=campuspass_db
   set DB_USER=postgres
   set DB_PASSWORD=YOUR_POSTGRES_PASSWORD
   set DB_HOST=localhost
   set DB_PORT=5432
   ```
   Replace `YOUR_POSTGRES_PASSWORD` with your local PostgreSQL password. Do not commit it to GitHub.
5. Apply migrations and create an admin/staff account:
   ```bat
   python manage.py makemigrations passport
   python manage.py migrate
   python manage.py createsuperuser
   ```
6. Run the app:
   ```bat
   python manage.py runserver
   ```
7. Open `http://127.0.0.1:8000/`.

### Quick UI preview without PostgreSQL
For a temporary local preview only, open a new CMD terminal in the project folder and run:
```bat
set DB_ENGINE=sqlite
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```
This preview uses SQLite and does **not** meet the assignment's PostgreSQL requirement. Switch back to PostgreSQL for the final project demonstration.

## First-time demo checklist
1. Register a normal student account.
2. Log in and edit profile details.
3. Add an achievement and upload a sample/dummy proof file.
4. Log in to `/admin/` with the superuser, then use the staff review page `/staff/achievements/` to approve or request corrections.
5. Add an opportunity in Django admin (or use the staff-only opportunity form).
6. Log in as a student, track an opportunity, and review the dashboard and notifications.
7. Export achievements as CSV.

## Database design (text ER overview)
- User 1 — 1 StudentProfile
- User 1 — many Achievement
- User 1 — many Opportunity (as poster)
- User many — many Opportunity through OpportunityApplication (unique per student/opportunity)
- User 1 — many Notification
- Opportunity 1 — many OpportunityApplication

A diagram source is provided in `docs/ER_DIAGRAM.mmd`.

## GitHub
```bat
git init
git add .
git commit -m "Initial CampusPass mini project"
```
Create an empty repository on GitHub, then follow GitHub's instructions to add its remote and push. Never commit secrets, real student data, or uploaded private documents.

## Important
This is a student mini-project starter implementation. Test it locally and understand the code before the review. Do not present untested code as fully verified. External opportunity links are examples entered by an administrator; tracking an opportunity in CampusPass does not submit an application to the external organization automatically.
