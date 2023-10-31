FROM python:3.7-slim

WORKDIR /app

# Install system dependencies
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Install python dependencies
RUN pip install --upgrade pip
COPY requirements.txt .
RUN pip install --upgrade pip \
    && pip install -r requirements.txt

# Copy your application files
COPY . .

CMD ["gunicorn", "stockpredictor.wsgi:application", "--bind", "0.0.0.0:8000"]
