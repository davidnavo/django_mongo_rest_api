
# Django mongodb Project

## Project documentation


## Development Board


# Django mongodb Backend

## Setup environment

python3 -m venv venv

source venv/bin/activate

pip install -r requirements.txt


## Create superuser

python manage.py createsuperuser --email <xxx@xxx,com> --username xxxx

## Make migrations / migrate

python manage.py makemigrations

python manage.py migrate

## Run Django App

python manage.py runserver 0.0.0.0:8000

<http://localhost:8000/admin>

## Loading / Saving data

python manage.py dumpdata > data.json

python manage.py loaddata data.json

## Installing / Saving requirements

pip freeze > requirements.txt

## Create docker file

docker build -t organization/image .
