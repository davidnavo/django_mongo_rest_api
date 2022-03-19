https://www.bezkoder.com/django-mongodb-crud-rest-framework/


python3 -m venv venv
source venv/bin/activate 
pip install django
pip install djangorestframework

##postgresql support
pip install psycopg2-binary

##mongodb support
pip install djongo


django-admin startproject djmdb .
cd djmdb
django-admin startapp api
cd ..

>pico settings.py

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'darvel_backend',
        'USER': 'darvel',
        'PASSWORD': 'darvel',
        'HOST': '127.0.0.1',
        'PORT': '5432',
    }
}

DATABASES = {
    'default': {
        'ENGINE': 'djongo',
        'NAME': 'djmdb',
        'HOST': '127.0.0.1',
        'PORT': 27017,
        'USER': 'admin',
        'PASSWORD': 'admin',
    }
}

pip install django-cors-headers

>pico settings.py

INSTALLED_APPS = (
    ...,
    'corsheaders'
)

MIDDLEWARE_CLASSES = (
    ...
    'django.contrib.sessions.middleware.SessionMiddleware',
    'corsheaders.middleware.CorsMiddleware',
    ...
)

At the end of the file:

CORS_ORIGIN_ALLOW_ALL = True
CORS_ALLOW_CREDENTIALS = True
CORS_ORIGIN_WHITELIST = [
    'http://localhost:3030',
]
CORS_ORIGIN_REGEX_WHITELIST = [
    'http://localhost:3030',
]

pip install psycopg2-binary

brew install libpq
/usr/local/opt/libpq/bin/psql --host=localhost --user=darvel --password
CREATE DATABASE darvel_backend;
DROP DATABASE darvel_backend;

python manage.py makemigrations
python manage.py migrate
python manage.py createsuperuser --email admin@admin.com --username admin


python manage.py dumpdata > db.json
python manage.py loaddata db.json

python manage.py runserver 0.0.0.0:8000
http://localhost:8000/admin


pip install django-extensions

INSTALLED_APPS = (
    ...
    'django_extensions',
    ...
)

python manage.py createapp darvel_backend.api

INSTALLED_APPS = (
    ...
    'darvel_backend.api',
    ...
)

pip install django-jsonfield

>pico urls.py
>pico api/models.py
>pico api/serializers.py
>pico api/urls.py

nohup ./manage.py runserver &

pip freeze > requirements.txt



-------

Adding Celery tasks to the project


pip install celery
Follow steps in:
https://docs.celeryproject.org/en/stable/django/first-steps-with-django.html

1. add celery.py
2. add tasks.py

celery -A restproject worker -l INFO -Q restproject
nohup celery -A darvel_backend worker -l info -Q darvel_backend &

## Delete sh jobs execution
ps -aux | grep celery
kill <pid>

# Delete task execution with psql
psql -h localhost smartflow postgres
truncate table workflow_execution cascade;
