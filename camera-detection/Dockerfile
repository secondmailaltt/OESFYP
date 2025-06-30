# Dockerfile for Railway

FROM python:3.10-slim

# set working directory
WORKDIR /app

# install system deps (ffmpeg for video encoding)
RUN apt-get update \
 && apt-get install -y ffmpeg \
 && rm -rf /var/lib/apt/lists/*

# copy and install Python deps
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# copy source
COPY . .

# expose the port your Flask app listens on
EXPOSE 5001

# use Gunicorn to serve the app
CMD ["gunicorn", "--bind", "0.0.0.0:5001", "app:app", "--workers", "1"]
