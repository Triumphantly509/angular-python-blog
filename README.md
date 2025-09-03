# Blog Project (Django + Angular + Docker)

This is a full-stack blog application built with **Django (backend)** and **Angular (frontend)**.  
The project is containerized using **Docker Compose**, with **PostgreSQL** as the production database and **SQLite** for local development.

---

# Features
- **Backend**: Django + Django REST Framework (API)
- **Frontend**: Angular (Bootstrap for styling)
- **Database**: PostgreSQL (Docker) / SQLite (local dev)
- **CORS Support** for Angular–Django communication
- **Swagger/OpenAPI docs** for REST API (`drf-yasg`)
- **Dockerized** for easy deployment

---

# Project Structure

blog_front_back_end/
│── blog_project/ # Angular frontend
│── blog_project_python/ # Django backend
  │── .env # Environment variables
  │── Dockerfile # Multi-stage Dockerfile (frontend + backend)
│── docker-compose.yml # Multi-service Docker Compose setup
│── README.md # Documentation (this file)
│── .gitignore # Git ignore rules


# ⚙️ Setup Instructions

1️⃣ Clone the Repository
```bash
git clone https://github.com/your-username/blog_front_back_end.git
cd blog_front_back_end

2️⃣ Configure Environment Variables

Create a .env file in the project root:

# Django
SECRET_KEY=your-secret-key
DEBUG=True
ALLOWED_HOSTS=localhost,127.0.0.1,0.0.0.0

# CORS
CORS_ALLOWED_ORIGINS=http://localhost:4200,http://127.0.0.1:4200

# Database (Postgres in Docker)
DATABASE_ENGINE=django.db.backends.postgresql
DATABASE_NAME=blogdb
DATABASE_USER=bloguser
DATABASE_PASSWORD=blogpassword
DATABASE_HOST=db
DATABASE_PORT=5432

# Django running inside Docker
RUNNING_IN_DOCKER=True

3️⃣ Run with Docker Compose
docker compose up -d --build


Backend (Django) → http://localhost:8000

Frontend (Angular + Nginx) → http://localhost:4200

Postgres Database → exposed internally as db:5432

4️⃣ Run Locally (without Docker)

Backend:

cd blog_project_python
python manage.py migrate
python manage.py runserver

Frontend:

cd blog_project
npm install
ng serve --open

API Documentation

Swagger docs are available at:
http://localhost:8000/swagger/

Docker Services

frontend → Angular app served with Nginx

backend → Django REST Framework app

db → PostgreSQL database

Tech Stack

Backend: Django, Django REST Framework

Frontend: Angular, Bootstrap

Database: PostgreSQL, SQLite (dev)

Tools: Docker, Docker Compose, Nginx

Development Notes
***********************************************************************
In local dev, Django runs with SQLite.

In Docker, Django automatically connects to PostgreSQL.

Update .env if you add new origins to CORS_ALLOWED_ORIGINS.

Remember to add new allowed hosts to ALLOWED_HOSTS when deploying.

**********************************************************************
License

This project is licensed under the MIT License.
