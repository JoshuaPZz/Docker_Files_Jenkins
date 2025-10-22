# Usar una imagen base de Python
FROM python:3.9-slim

# Establecer variables de entorno para Python
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

# Instalar dependencias del sistema necesarias para Django y posibles dependencias
RUN apt-get update && apt-get install -y \
    gcc \
    postgresql-client \
    && rm -rf /var/lib/apt/lists/*

# Crear y establecer el directorio de trabajo
WORKDIR /app

# Copiar el archivo de requirements
COPY requirements.txt /app/

# Instalar las dependencias de Python
RUN pip install --upgrade pip
RUN pip install -r requirements.txt

# Copiar todo el código del proyecto Django
COPY . /app/

# Exponer el puerto en el que Django correrá
EXPOSE 8000

# Crear migraciones y correr la aplicación Django
CMD ["sh", "-c", "python manage.py migrate && python manage.py runserver 0.0.0.0:8000"]