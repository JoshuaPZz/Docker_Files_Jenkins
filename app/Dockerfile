FROM python:3.10

WORKDIR /app
COPY . .
RUN apt-get update && apt-get install -y \
    gcc \
    postgresql-client \
    && rm -rf /var/lib/apt/lists/*

EXPOSE 8000
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]