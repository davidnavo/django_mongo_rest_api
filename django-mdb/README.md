
# Darvel Project

## Project documentation

[Darvel documentation](https://drive.google.com/drive/folders/0ALAue658glZsUk9PVA)

## Development Board

[Jamboard](https://jamboard.google.com/d/1TouRusrNHlcUvzo2b5CNYEKJq4SzwW_PFeKFOdCRaSM)

# Darvel Backend

## Setup environment

python3 -m venv venv

source venv/bin/activate

pip install -r requirements.txt


## Create superuser

python manage.py createsuperuser --email <darvel@darvel.com> --username darvel

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

docker build -t rdspain/darvel .
