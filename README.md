# FastAPI Calculator with CI/CD Pipeline

A production-ready FastAPI application with automated testing, security scanning, and Docker deployment.

---

## 🚀 Quick Start

### Prerequisites
- Python 3.10+
- Docker (optional)
- Git

### Local Setup

```bash
# Clone and navigate
git clone <https://github.com/techy-Nik/assignment-8>
cd <assignment-8>

# Create virtual environment
python3 -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate.bat

# Install dependencies
pip install -r requirements.txt
playwright install

# Run application
uvicorn main:app --host 0.0.0.0 --port 8000 --reload
```

Access at: `http://localhost:8000`

---

## 🐳 Docker

### Run with Docker
```bash
docker build -t fastapi-calculator .
docker run -p 8000:8000 fastapi-calculator
```

### Run with Docker Compose
```bash
docker-compose up --build
```

### Pull from Docker Hub
```bash
docker pull techynik/module8:latest
docker run -p 8000:8000 techynik/module8:latest
```

---

## 🧪 Testing

```bash
# All tests
pytest tests/ --cov=src

# Specific test suites
pytest tests/unit/        # Unit tests
pytest tests/integration/ # Integration tests
pytest tests/e2e/         # End-to-end tests
```

---

## 🔄 CI/CD Pipeline

The GitHub Actions pipeline includes three stages:

1. **Test** - Runs unit, integration, and E2E tests with coverage
2. **Security** - Scans Docker image with Trivy for vulnerabilities
3. **Deploy** - Builds and pushes multi-platform images to Docker Hub

### Required GitHub Secrets
- `DOCKERHUB_USERNAME`
- `DOCKERHUB_TOKEN`

### Pipeline Features
- Automatic testing on push/PR
- Security scanning (fails on CRITICAL/HIGH vulnerabilities)
- Multi-platform builds (AMD64, ARM64)
- Tagged releases: `latest` and `<commit-sha>`

---

## 📚 API Documentation

- Swagger UI: `http://localhost:8000/docs`
- ReDoc: `http://localhost:8000/redoc`

---

## 🔒 Security Features

- Trivy vulnerability scanning
- Non-root Docker user
- Minimal base image (`python:3.10-slim`)
- Health check endpoint: `/health`

---

## 📞 Quick Commands

| Action | Command |
|--------|---------|
| Start server | `uvicorn main:app --reload` |
| Run tests | `pytest tests/` |
| Build Docker | `docker build -t app .` |
| Docker Compose | `docker-compose up --build` |
| Security scan | `trivy image app:test` |