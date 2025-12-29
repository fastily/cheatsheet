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

## pip
```bash
# Create an editable install that works with vscode/pylance
pip install -e '<PATH_TO_PKG_DIR>' --config-settings editable_mode=compat
```

## uv
```bash
# bump patch version of module before publishing (updates uv.lock & pyproject.toml)
uv version --bump patch

# build artifacts
uv build

# publish to pypi
uv publish
```