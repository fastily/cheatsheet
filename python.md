## django
```bash
# create new project
django-admin startproject '<PROJECT_NAME>'

# add sub-app to project
python3 manage.py startapp '<APP_NAME>'

# start server
python3 manage.py runserver

# create migration
python3 manage.py makemigrations

# migrate db
python3 manage.py migrate

# create superuser for admin panel
python3 manage.py createsuperuser

# collect static files into one folder
python3 manage.py collectstatic
```

## gunicorn
```bash
# restart a gunicorn service
sudo systemctl restart gunicorn
```

## pip
```bash
# generate requirements.txt
pip freeze > requirements.txt

# upgrade a package
pip install --upgrade '<PACKAGE_NAME>'

# list outdated packages
pip list --outdated
```