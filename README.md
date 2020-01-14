# Minimal Django setup

[![Build Status](https://travis-ci.com/Wickedm777/Django-minimal-setup.svg?branch=master)](https://travis-ci.com/Wickedm777/Django-minimal-setup)

This is a minimal django dev setup with:

- Django
- python-dotenv
- dj-database-url
- Travis ci integration

## Local deployment

1. Git clone this repo
2. Create a virtualenv

        virtualenv envname

        python3 -m venv envname

3. Install requirements.txt

        pip install -r requirements.txt

Table of Contents:

- [Django commands](#Django%20commands)
- [Django settings](#Django%20settings)
- [Travis CI](#Travis%20CI)

## Django commands

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

## Django settings

1. Create a .env file for secret variables.
 *<https://pypi.org/project/python-dotenv/>*

2. Put the following in the .env file.

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

## Travis CI

1. Login to travis ci with your github account and activate repos

2. Create a .travis.yml file

3. For python put this in the created file.
Note that if travis does not build check for indentation and hidden chars.

        # Minimal
        language: python
        install:
        - "pip install -r requirements.txt"
        before_script:
        - export DATABASE_URL="sqlite:///db.sqlite3"
        script:
        - SECRET_KEY="whatever" ./manage.py test

        # Specific with postgresql
        language: python
        python:
        - "3.7"
        install:
        - "pip install -r requirements.txt"
        services:
        - postgresql
        before_script:
        - psql -c 'create database hiware;' -U postgres
        - export DATABASE_URL="postgres://postgres@localhost:5432/hiware"
        script:
        - SECRET_KEY="whatever" ./manage.py test

