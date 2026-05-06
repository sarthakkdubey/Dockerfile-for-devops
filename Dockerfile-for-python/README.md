# Python Application with Docker

This project contains a simple Docker setup for running a Python application in a containerized environment.

The Dockerfile uses a lightweight Python image and installs all required dependencies from the `requirements.txt` file before starting the application.

## Dockerfile

```dockerfile
FROM python:3.12-slim

ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

WORKDIR /app

COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

COPY . .

EXPOSE 8000

CMD ["python", "app.py"]
```

---

## Build the Docker Image

Run the following command inside the project directory:

```bash
docker build -t python-app .
```

This command creates a Docker image named `python-app`.

---

## Run the Container

```bash
docker run -p 8000:8000 python-app
```

After the container starts, the application will be available at:

```text
http://localhost:8000
```

---

## Project Notes

- Uses the official Python 3.12 slim image
- Installs dependencies using `requirements.txt`
- Runs the application using `app.py`
- Exposes port `8000`
- Suitable for small Python projects and API applications

You can modify the start command depending on the framework you are using, such as Flask, FastAPI, or Django.
