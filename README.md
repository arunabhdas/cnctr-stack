# Cnctr Stack


## Steps

## Branches

main is the default development branch


==> python --version
Python 3.8.5

# M1 python troubleshooting
==> which -a python3
/usr/bin/python3
==> python3 -V
Python 3.8.9
Upgrade pip
==> python3 -m pip install --upgrade pip
Successfully installed pip-21.3.1

## Git push to heroku

==> git push heroku main

## Bootstrap
==> django-admin startproject cnctr


==> heroku config:set DISABLE_COLLECTSTATIC=1


==> pip install gunicorn

==> pip freeze > requirements.txt

==> cd cnctr && python manage.py startapp portal

==> python manage.py migrate

==> python manage.py createsuperuser


## Improved admin with django-admin-interface

Install 

https://pypi.org/project/django-admin-interface/

Installation
Run pip install django-admin-interface
Add admin_interface, flat_responsive, flat and colorfield to settings.INSTALLED_APPS before django.contrib.admin
INSTALLED_APPS = (
    #...
    'admin_interface',
    'flat_responsive', # only if django version < 2.0
    'flat', # only if django version < 1.9
    'colorfield',
    #...
    'django.contrib.admin',
    #...
)

X_FRAME_OPTIONS='SAMEORIGIN' # only if django version >= 3.0
Run python manage.py migrate
Run python manage.py collectstatic
Restart your application server

Upgrade
Run pip install django-admin-interface --upgrade
Run python manage.py migrate (add --fake-initial if you are upgrading from 0.1.0 version)
Run python manage.py collectstatic --clear
Restart your application server
Optional themes
This package ships with optional themes as fixtures, they can be installed using the loaddata admin command. Optional themes are activated on installation.
DJANGO THEME (DEFAULT):
Run python manage.py loaddata admin_interface_theme_django.json
BOOTSTRAP THEME:
Run python manage.py loaddata admin_interface_theme_bootstrap.json
FOUNDATION THEME:
Run python manage.py loaddata admin_interface_theme_foundation.json
U.S. WEB DESIGN STANDARDS THEME:
Run python manage.py loaddata admin_interface_theme_uswds.json

# Development

python manage.py makemigrations
python manage.py migrate
python manage.py runserver

# DjangoRestFramework

python manage.py startapp core

## Production Deploy to heroku

heroku login
heroku apps:info
heroku git:remote -a <appname>

git push heroku main
heroku run python manage.py migrate
heroku run python manage.py collectstatic
~~~
brew tap heroku/brew && brew install heroku
~~~

## Deploy

==> git remote -v

==> git push origin heroku

==> heroku run python manage.py migrate

==> heroku run python manage.py createsuperuser

==> heroku run python manage.py createsuperuser
Running python manage.py createsuperuser on ⬢ .. up, run.4227 (Free)
Username (leave blank to use 'u48470'): 
Error: That username is already taken.
Username (leave blank to use 'u48470'):
Password: 
Password (again): 
Superuser created successfully.


python manage.py collectstatic

~~~
==> cat requirements.txt 
asgiref==3.3.4
Django==3.2.2
gunicorn==20.1.0
pytz==2021.1
sqlparse==0.4.1
~~~
##

Install environ
https://pypi.org/project/django-environ/

pip install django-environ


## Postgres

==> psql
psql (13.2)
Type "help" for help.

=# CREATE DATABASE <db_name>;
CREATE DATABASE
=# CREATE USER <db_user> WITH PASSWORD <db_password>;
CREATE ROLE
=# ALTER ROLE <db_user> SET client_encoding TO 'utf8';
ALTER ROLE
=# ALTER ROLE <db_user> SET default_transaction_isolation TO 'read committed';
ALTER ROLE
=# ALTER ROLE <db_user> SET timezone TO 'UTC';
ALTER ROLE
ALTER ROLE
=# GRANT ALL PRIVILEGES ON DATABASE <db_name> TO <db_user>;

# Troubleshooting 


If admin CSS not displaying on heroku - 
Install and follow - 

https://pypi.org/project/dj-static/


if psycopg2-binary not installing 

brew install libpq --build-from-source
brew install openssl

export LDFLAGS="-L/opt/homebrew/opt/openssl@1.1/lib -L/opt/homebrew/opt/libpq/lib"
export CPPFLAGS="-I/opt/homebrew/opt/openssl@1.1/include -I/opt/homebrew/opt/libpq/include"

pip3 install psycopg2

What worked for me on Mac:

$ brew install postgresql

$ brew link openssl
Warning: Refusing to link macOS provided/shadowed software: openssl@1.1
If you need to have openssl@1.1 first in your PATH, run:
echo 'export PATH="/opt/homebrew/opt/openssl@1.1/bin:$PATH"' >> ~/.zshrc

For compilers to find openssl@1.1 you may need to set:
export LDFLAGS="-L/opt/homebrew/opt/openssl@1.1/lib"
export CPPFLAGS="-I/opt/homebrew/opt/openssl@1.1/include"

For pkg-config to find openssl@1.1 you may need to set:
export PKG_CONFIG_PATH="/opt/homebrew/opt/openssl@1.1/lib/pkgconfig"

Then I downloaded and installed PG Admin from https://www.pgadmin.org/download/
Then my system will be able to resolve the psycopg2 requirements and "pip install psycopg2-binary" worked just fine.



# References

https://www.youtube.com/watch?v=YkpEtE_x6xk

https://www.youtube.com/watch?v=RPsDhoWY_kc&t=675s


S3 - 
https://github.com/yunojuno/django-s3-upload

https://www.caktusgroup.com/blog/2014/11/10/Using-Amazon-S3-to-store-your-Django-sites-static-and-media-files/


https://www.youtube.com/watch?v=nzLMA9WZqMM

pip install boto3
pip install django-storages


## Requirements.txt

```
asgiref==3.3.4
boto3==1.18.65
botocore==1.21.65
dj-database-url==0.5.0
dj-static==0.0.6
Django==3.2.2
django-admin-interface==0.16.3
django-colorfield==0.4.1
django-environ==0.4.5
django-filter==2.4.0
django-flat-responsive==2.0
django-flat-theme==1.1.4
django-jet==1.0.8
django-storages==1.12.2
djangorestframework==3.12.4
gunicorn==20.1.0
jmespath==0.10.0
Markdown==3.3.4
Pillow==8.4.0
psycopg2==2.9.1
python-dateutil==2.8.2
pytz==2021.1
s3transfer==0.5.0
six==1.16.0
sqlparse==0.4.1
static3==0.7.0
urllib3==1.26.7
```
