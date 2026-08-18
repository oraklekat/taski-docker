FROM python:3.12

WORKDIR /app

RUN pip install gunicorn==25.3.0

COPY requirements.txt .

RUN pip install -r requirements.txt --no-cache-dir

COPY . .

CMD ["gunicorn", "--bind", "0.0.0.0:8000", "backend.wsgi"]
FROM python:3.12

WORKDIR /app

# Устанавливаем системные зависимости для PostgreSQL
RUN apt-get update && apt-get install -y libpq-dev gcc

RUN pip install gunicorn==25.3.0

COPY requirements.txt .

# Добавляем psycopg2-binary для работы с PostgreSQL
RUN pip install -r requirements.txt --no-cache-dir && pip install psycopg2-binary

COPY . .

CMD ["gunicorn", "--bind", "0.0.0.0:8000", "backend.wsgi"]
