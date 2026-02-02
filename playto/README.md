# Playto Community Feed

## Setup Instructions

### Backend
```bash
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
cd backend
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

Open:
[http://127.0.0.1:8000/](http://127.0.0.1:8000/)

### Admin

[http://127.0.0.1:8000/admin/](http://127.0.0.1:8000/admin/)

## AI Usage Disclosure

AI tools were used to accelerate development.
All queries, data models, and aggregation logic were reviewed,
tested, and optimized manually to ensure correctness,
performance, and compliance with the assignment constraints.