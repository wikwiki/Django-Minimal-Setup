# Minimal Django setup

This is a minimal django dev setup with:

- Django
- python-dotenv
- dj-database-url

## Django commands

```bash
#Start new django project
django-admin startproject projectname

#Start new django project with manage.py in root
django-admin startproject projectname .

#Create new app in project
./manage.py startapp appname

#Run the server
./manage.py runserver

#Run migration
./manage.py migrate

#Create migration files
./manage.py makemigrations

#Run tests
./manage.py test

#Create a superuser to access the admin site
./manage.py createsuperuser
```

## Django settings

1. Create a .env file for secret variables.
 *<https://pypi.org/project/python-dotenv/>*

2. Put the following in the .env file.

```env
#https://pypi.org/project/python-dotenv/

#SET DEBUG: 1 is True, empty is False
DEVELOPMENT = 1

#Secret key required by django
#i.e. generate one here  https://djskgen.herokuapp.com/
SECRET_KEY = "m6dd7i2mvlsq6h(5$rr-umqc$2c1iio$pusid#0#^=-+smidb@"

#Database urls https://pypi.org/project/dj-database-url/
#https://github.com/jacobian/dj-database-url
DEV_DATABASE_URL = "sqlite:///db.sqlite3"
DATABASE_URL = ""

#Set Email: 1 is Console, empty is SMTP
EMAIL = 1
EMAIL_ADDRESS = ""
EMAIL_PASSWORD = ""
```
