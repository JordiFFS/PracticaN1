# backend/Dockerfile

# Usamos Python 3.10 versión ligera
FROM python:3.10-slim

# Variables para optimizar Python en Docker
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1

# Directorio de trabajo dentro del contenedor
WORKDIR /app

# 1. Instalar dependencias del sistema necesarias para PostgreSQL y compilación
RUN apt-get update && apt-get install -y \
    gcc \
    libpq-dev \
    pkg-config \
    && rm -rf /var/lib/apt/lists/*

# 2. Copiar e instalar dependencias de Python
COPY requirements.txt .
# Instalamos las dependencias. Nota: Asegúrate de tener psycopg2-binary en tu txt
RUN pip install --no-cache-dir -r requirements.txt

# 3. Copiar el código fuente
COPY . .

# Exponer el puerto 8000
EXPOSE 8000

# Comando por defecto (modo desarrollo para que veas los logs)
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]