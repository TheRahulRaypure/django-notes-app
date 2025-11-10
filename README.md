```markdown
# 📝 Django Notes App

A simple yet production-grade **Notes Management Web Application** built using **Django**, **MySQL**, and **Nginx**, fully containerized using **Docker Compose**.  
This project demonstrates a scalable multi-container setup suitable for real-world web applications.

---

## 🚀 Features

- ✅ Create, edit, and delete notes
- ✅ Django-powered backend with authentication
- ✅ MySQL database for persistent storage
- ✅ Nginx as reverse proxy for Gunicorn server
- ✅ Docker Compose setup for local or cloud deployment
- ✅ Environment variables for secure configuration

---

## 🏗️ Tech Stack

| Layer | Technology |
|--------|-------------|
| **Frontend** | HTML, CSS (Django Templates) |
| **Backend** | Django (Python 3) |
| **Web Server** | Gunicorn + Nginx |
| **Database** | MySQL 8 |
| **Containerization** | Docker & Docker Compose |
| **OS** | Linux (Ubuntu) |

---

## ⚙️ Project Structure

```

django-notes-app/
├── nginx/
│   ├── Dockerfile
│   └── nginx.conf
├── notesapp/
│   ├── settings.py
│   ├── urls.py
│   ├── wsgi.py
│   └── ...
├── manage.py
├── requirements.txt
├── Dockerfile
├── docker-compose.yaml
└── .env

```

---

## 🧩 Environment Variables

Create a `.env` file in the project root with:

```

DEBUG=1
SECRET_KEY=your-secret-key
DB_NAME=test_db
DB_USER=root
DB_PASSWORD=root
DB_HOST=mysql
DB_PORT=3306

````

---

## 🐳 Docker Setup

### 1️⃣ Build and start all services:
```bash
docker-compose up --build
````

### 2️⃣ Access the app:

* **Web App:** [http://localhost](http://localhost)
* **Django Admin:** [http://localhost/admin](http://localhost/admin)
* **MySQL:** localhost:3306

### 3️⃣ Stop and remove containers:

```bash
docker-compose down -v
```

---

## 🩺 Health Checks

Each service includes built-in Docker **health checks** to ensure reliability:

| Service    | Health Check                          |
| ---------- | ------------------------------------- |
| **MySQL**  | `mysqladmin ping`                     |
| **Django** | `curl -f http://localhost:8000/admin` |

---

## 🧠 How It Works

* **Nginx** forwards incoming HTTP requests (port 80) to the **Gunicorn** app server (port 8000).
* **Gunicorn** runs the Django WSGI application.
* **MySQL** stores note data persistently using a named Docker volume.
* The **Docker Compose** file orchestrates all containers in one isolated network.

---

## 🧰 Development Commands

Run Django migrations manually:

```bash
docker exec -it django_cont python manage.py migrate
```

Create a superuser:

```bash
docker exec -it django_cont python manage.py createsuperuser
```

Access Django shell:

```bash
docker exec -it django_cont python manage.py shell
```

---

## 🧪 Testing the API / Views

You can test app endpoints locally via:

```bash
curl http://localhost/api/notes/
```

or open the web UI in a browser to manage notes visually.

---

## 📦 Production Deployment Notes

For deploying to cloud (AWS EC2, Azure, GCP):

* Use **Gunicorn** with **Nginx** (already configured here).
* Update `.env` for production (disable DEBUG, change DB creds).
* Configure persistent storage for MySQL volume.
* Optionally add HTTPS (Certbot + Nginx SSL).

---

## 🌟 Future Enhancements

* 🟢 Add user authentication for personal note access
* 🟢 Add REST API using Django REST Framework
* 🟢 Integrate CI/CD (GitHub Actions + Docker Hub)
* 🟢 Add frontend with React or Vue
* 🟢 Deploy on AWS ECS / ECR

---

## 👨‍💻 Author

**Shubham Londhe**
📦 [GitHub Repository](https://github.com/LondheShubham153/django-notes-app)
💼 DevOps Engineer & Trainer | Docker, Kubernetes, AWS

---

## 🧾 License

This project is licensed under the **MIT License** — free to use and modify.

```
