## django
```bash
# install dependencies
pip install Django pylint pylint-django

# create new project
django-admin startproject '<PROJECT_NAME>'

# add sub-app to project
python manage.py startapp '<APP_NAME>'

# start server
python manage.py runserver

# create migration
python manage.py makemigrations

# migrate db
python manage.py migrate

# create superuser for admin panel
python manage.py createsuperuser

# collect static files into one folder
python manage.py collectstatic
```

## gunicorn
```bash
# restart a gunicorn service
sudo systemctl restart gunicorn
```

## twine
```bash
# generate distribution files (from within project's root folder)
python -m build # requires build package - pip install build

# upload generated distribution files to pypi
twine upload '<DIST_FOLDER_WITH_GENERATED_PACKAGES>'/*
```