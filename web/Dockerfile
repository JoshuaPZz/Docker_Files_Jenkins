FROM python:3.9-slim

ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

RUN apt-get update && apt-get install -y \
    gcc \
    postgresql-client \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

# Instalar pip y herramientas básicas
RUN pip install --upgrade pip

EXPOSE 8000

# Script que espera a que exista manage.py e instala dependencias
CMD sh -c "\
    while [ ! -f manage.py ]; do \
    echo 'Esperando que Jenkins suba el código...'; \
    sleep 2; \
    done && \
    echo 'Código detectado, instalando dependencias...' && \
    pip install -r requirements.txt && \
    echo 'Ejecutando migraciones de Django...' && \
    python manage.py migrate && \
    echo 'Iniciando servidor Django en el puerto 8000...' && \
    python manage.py runserver 0.0.0.0:8000"
