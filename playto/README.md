# Playto Community Feed

## Overview
This project is a prototype Community Feed built for the Playto Engineering Challenge.
It supports threaded discussions, likes with concurrency safety, and a dynamic leaderboard
based on karma earned in the last 24 hours.

## Tech Stack
- Backend: Django, Django REST Framework
- Database: SQLite
- Frontend: (API-ready, frontend optional)

## Features
- Posts with like counts
- Nested (threaded) comments
- Concurrency-safe likes
- Dynamic karma-based leaderboard (last 24 hours)

## How to Run Locally

```bash
git clone https://github.com/dineshkarthik18/playto-community-feed.git
cd playto-community-feed
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver
```

## API Endpoints

* GET /api/feed/
* POST /api/posts/{id}/like/
* GET /api/leaderboard/

## AI Usage Disclosure

AI tools were used to accelerate development.
All data models, queries, and aggregation logic were manually reviewed,
tested, and optimized to ensure correctness and performance.