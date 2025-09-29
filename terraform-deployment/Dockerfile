# Use a minimal Python image
FROM python:3.11-slim

# Prevent Python from writing .pyc files & enable stdout/stderr
ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1

# Set the working directory for the application
WORKDIR /app

# Install system dependencies & pip
RUN apt-get update && \
    apt-get install -y python3-pip build-essential ca-certificates && \
    pip install --upgrade pip

# Copy requirements file
COPY requirements.txt .

# Install Python dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the application code
COPY . .

# Expose the application port
EXPOSE 8080

# Set Flask environment variables
ENV FLASK_APP=app.py
ENV FLASK_RUN_HOST=0.0.0.0
ENV FLASK_RUN_PORT=8080

# Start the application
CMD ["flask", "run"]
