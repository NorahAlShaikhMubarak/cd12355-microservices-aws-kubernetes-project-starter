# 1) Base image: match your local Python (3.10 or 3.11 is fine)
FROM python:3.10-slim

# 2) System deps for psycopg2
RUN apt-get update -y && apt-get install -y --no-install-recommends \
    build-essential libpq-dev && \
    rm -rf /var/lib/apt/lists/*

# 3) App files
WORKDIR /app
COPY requirements.txt /app/
RUN pip install --no-cache-dir --upgrade pip setuptools wheel && \
    pip install --no-cache-dir -r requirements.txt

COPY . /app

# 4) Env (Flask listens on 5153)
ENV PYTHONUNBUFFERED=1
EXPOSE 5153

# 5) Run the app
CMD ["python", "app.py"]
