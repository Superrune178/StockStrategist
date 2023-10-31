# Use the specified python version
FROM python:3.11.3

# Set working directory
WORKDIR /app

# Update system and cleanup
RUN apt-get update \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Upgrade pip and install python dependencies
COPY requirements.txt .
RUN pip install --upgrade pip \
    && pip install -r requirements.txt

# Copy the application files to the container
COPY . .

# Run collectstatic AFTER copying your Django app
RUN python manage.py collectstatic --noinput

# Start Gunicorn when the container runs
CMD ["gunicorn", "stockpredictor.wsgi:application", "--bind", "0.0.0.0:8000"]
