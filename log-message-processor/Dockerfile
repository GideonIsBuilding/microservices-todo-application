# Use the official Python 3.9 slim image as base
FROM python:3.9-slim

WORKDIR /app

RUN apt-get update && apt-get install -y \
    gcc \
    make \
    python3-dev \
    libssl-dev \
    libffi-dev \
    build-essential \
    libsasl2-dev \
    libldap2-dev

COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

COPY . .

# Run the queue processor script when the container starts
CMD ["python", "main.py"]
