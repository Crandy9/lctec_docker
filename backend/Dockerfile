FROM python:3.11-slim

WORKDIR /backend

ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1 

RUN apt-get update \
    && apt-get -y install libpq-dev gcc \
    && pip install psycopg2

RUN pip install --upgrade pip

COPY requirements.txt /backend/

RUN pip install -r requirements.txt

COPY . /backend/

EXPOSE 8000

#  CMD ["gunicorn", "lctec_project.wsgi:application", "--bind", "0.0.0.0:8000"]
# CMD ["DJANGO_SETTINGS_MODULE=lctec_project.dev_settings", "python", "manage.py", "runserver", "0.0.0.0:8000"]