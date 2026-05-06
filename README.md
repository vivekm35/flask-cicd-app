# Flask CI/CD Pipeline on AWS

![CI Pipeline](https://github.com/vivekm35/flask-cicd-app/actions/workflows/ci.yml/badge.svg)
![Python](https://img.shields.io/badge/Python-3.11-blue)
![Docker](https://img.shields.io/badge/Docker-Containerized-blue)
![AWS](https://img.shields.io/badge/AWS-EC2-orange)
![License](https://img.shields.io/badge/License-MIT-green)

A production-style CI/CD pipeline built from scratch using Python Flask, Docker, GitHub Actions, and AWS EC2.

---

## Live Demo

Visit the live application: [http://18.217.117.71](http://18.217.117.71)

| Endpoint  | Method | Response              |
|-----------|--------|-----------------------|
| `/`       | GET    | Hello from my DevOps app! |
| `/health` | GET    | `{"status": "ok"}`   |

---

## Architecture

```
Developer pushes code
        |
        v
  GitHub Repository
        |
        v
GitHub Actions Pipeline
   |            |
   v            v
Run Tests    Build Docker Image
(pytest)     (only if tests pass)
        |
        v
   AWS EC2 Server
   (Live Application)
```

---

## Tech Stack

| Tool            | Purpose                        |
|-----------------|-------------------------------|
| Python & Flask  | Backend web application        |
| pytest          | Automated testing              |
| Docker          | Containerization               |
| GitHub Actions  | CI/CD pipeline automation      |
| AWS EC2         | Cloud deployment               |
| Linux & Bash    | Server configuration           |
| Git & GitHub    | Version control & collaboration|

---

## Features

- Automated tests run on every push to `main`
- Docker image builds automatically after tests pass
- App deployed and accessible live on AWS EC2
- Health check endpoint at `/health`
- Zero manual deployment steps

---

## Project Structure

```
flask-cicd-app/
├── .github/
│   └── workflows/
│       └── ci.yml          # GitHub Actions pipeline
├── tests/
│   ├── __init__.py
│   └── test_app.py         # Automated test suite
├── app.py                  # Flask application
├── Dockerfile              # Docker configuration
├── .dockerignore           # Docker ignore rules
├── requirements.txt        # Python dependencies
└── README.md               # Project documentation
```

---

## Getting Started

### Run Locally with Python

```bash
# Clone the repository
git clone https://github.com/vivekm35/flask-cicd-app.git
cd flask-cicd-app

# Create virtual environment
python3 -m venv venv
source venv/bin/activate

# Install dependencies
pip3 install -r requirements.txt

# Run the app
python3 app.py
```

Visit [http://localhost:5000](http://localhost:5000)

### Run with Docker

```bash
# Build the image
docker build -t flask-cicd-app .

# Run the container
docker run -p 5000:5000 flask-cicd-app
```

Visit [http://localhost:5000](http://localhost:5000)

---

## Run Tests

```bash
python3 -m pytest tests/
```

Expected output:
```
2 passed in 0.5s
```

---

## CI/CD Pipeline

Every push to `main` triggers the GitHub Actions pipeline automatically:

1. **Checkout** — pulls the latest code
2. **Setup Python** — installs Python 3.11
3. **Install dependencies** — runs `pip install -r requirements.txt`
4. **Run tests** — executes `pytest tests/`
5. **Build Docker image** — only runs if all tests pass

---

## Deployment

The application is deployed on **AWS EC2** (Amazon Linux 2023, t2.micro):

- Docker installed and running on the server
- App containerized and exposed on port 80
- Accessible publicly via EC2 Public IPv4 address

---

## Author

**Vivek Mekala**
MS in Computer Science — University of Cincinnati, Ohio

- GitHub: [@vivekm35](https://github.com/vivekm35)
- LinkedIn: [Connect with me](https://www.linkedin.com/in/vivekm35)

---

## Portfolio Roadmap

- [x] Project 1 — CI/CD Pipeline on AWS ← **YOU ARE HERE**
- [ ] Project 2 — Kubernetes on AWS EKS with Auto-Scaling
- [ ] Project 3 — Monitoring & Alerting with Prometheus + Grafana

---

## License

This project is open source and available under the [MIT License](LICENSE).
