# Class Feedback Management System

A learning project for recording and reviewing class-related notes/feedback, with a **FastAPI + SQLAlchemy** backend, **PostgreSQL**, and a small HTML/CSS/JavaScript management interface.

## Features found in the code
- Create user accounts and store user records
- Submit positive/negative notes with message, date, and username
- Filter notes/reports by user, date range, and other criteria
- View users and manage stored records through manager endpoints
- Docker configuration files for backend and frontend (need corrections)

## Tech stack
Python, FastAPI, Pydantic, SQLAlchemy, PostgreSQL, HTML, Bootstrap, JavaScript, Docker Compose.

## Repository layout

```text
back/                 # FastAPI, models and requirements
front/                # HTML, CSS and browser JavaScript
docker-compose.yml    # Current compose configuration
```

## Local backend setup (after configuring the database)

```bash
git clone https://github.com/mahdiramezanif/class-management.git
cd class-management/back
python -m venv .venv
# Activate the virtual environment for your operating system
pip install -r requirements.txt
uvicorn main:app --reload --port 8000
```

Open http://localhost:8000/docs for the generated API documentation. The database connection is configured in [`back/DataBase.py`](back/DataBase.py) and must point to your own database.

The frontend consists of static files in [`front/`](front/). Its API URLs may also need updating to point to the locally running backend.

## Known limitations / security
- **Do not run the current `docker-compose.yml` as-is.** It refers to `./backend` and `./frontend`, but the actual directories are `back` and `front`.
- The Compose file contains a PostgreSQL credential. Replace it with environment-based configuration and rotate the credential if it is real.
- The FastAPI source contains a hard-coded manager password and compares stored passwords as plaintext. This is **not production authentication**.
- The current database configuration, Dockerfiles, and frontend integration should be fixed and tested together before claiming a one-command deployment.

## Scope
Educational prototype, not a production-ready class administration service.
