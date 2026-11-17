# Devine Adventures

Devine Adventures is a Flask web application for discovering adventure tours, booking available dates, and connecting travelers with tour operators. It includes traveler, operator, and administrator workflows, with support for reviews and payment integrations.

## Features

- Browse featured tours and view tour details, dates, itineraries, and reviews.
- Register and sign in as a traveler or tour operator.
- Book tour dates, join waitlists, manage bookings, and submit reviews.
- Let operators manage bookings and check in guests.
- Provide administrator tools for tours, users, bookings, reviews, community photos, and shop items.
- Integrate payment and email services, with simulation flows available for development.

## Architecture

The application uses Flask's application factory in `app/__init__.py`. Route modules are registered as blueprints and render Jinja templates from `app/templates`. SQLAlchemy models in `app/models` describe users and tour operators, tours and itineraries, bookings, payments, waitlists, and reviews. Flask extensions provide database access and migrations, login management, CSRF protection, and scheduled review-request jobs. Static CSS, JavaScript, and images are served from `app/static`.

The default development database is SQLite. Production can use PostgreSQL through `DATABASE_URL`; Render deployment configuration is provided in `render.yaml`.

## Technology stack

- Python 3 (see `runtime.txt`)
- Flask 3, Jinja, Flask-SQLAlchemy, and Flask-Migrate
- Flask-Login and Flask-WTF
- SQLite for local development; PostgreSQL is supported through SQLAlchemy
- APScheduler for scheduled review requests
- Cloudinary, Stripe, M-Pesa, and SendGrid packages for optional media, payment, and email integrations
- Gunicorn for production serving

## Local setup

From the repository root, create and activate a virtual environment in PowerShell:

```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
```

Install dependencies and create a local environment file:

```powershell
python -m pip install -r requirements.txt
Copy-Item .env.example .env
```

Edit `.env` before running the application. Set a unique `SECRET_KEY`; the example value is for local development only. `DATABASE_URL` defaults to a local SQLite database. Cloudinary, Stripe, M-Pesa, and SendGrid credentials are only needed when configuring their corresponding integrations.

Start the development server:

```powershell
python run.py
```

Open [http://localhost:5000](http://localhost:5000). The app factory creates database tables on startup and seeds default demo accounts when the database has no users. The seeded accounts use known development passwords and are not safe for deployment; remove or replace this behavior and credentials before exposing any environment to users.

## Deployment

`render.yaml` describes a Render web service using Gunicorn. Configure a strong `SECRET_KEY` and a production `DATABASE_URL` in the hosting environment, and set any required third-party integration credentials there rather than committing secrets to the repository.

## Project layout

```text
app/
  models/       SQLAlchemy models
  routes/       Flask blueprints
  static/       CSS, JavaScript, and images
  templates/    Jinja page templates
  utils/        Email, payment, scheduling, and utility modules
run.py          Local application entry point
seed.py         Optional deployment seed script
requirements.txt
render.yaml
```

## License

This repository is proprietary and confidential. See [LICENSE](LICENSE) for the applicable terms.
