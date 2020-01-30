# djapp

- create a github repository
- init, commit, then push
- .gitignore
  venv
  _.pyc
  staticfiles
  .env
  _.sqlite3
  .env

\$ pipenv install django
\$ pipenv shell
\$ django-admin startproject vidly .

- install dependencies

\$ pipenv install pylint --dev
\$ pipenv install autopep8 --dev
\$ pipenv install pylint-django -
create .pylintrc file on root folder  
 load-plugins = pylint-django

$ python manage.py migrate
$ python manage.py startpp movies

settings.py

    INSTALLED_APPS = [
        'movies.apps.Movies.Config
    ]

models.py

    class Genre(models.Model):
        name = models.Charfield(max_length = 120)

    def __str__(self):
        return self.name

admin.py

    from .models import Genre

    admin.site.register(Genre)

\$ python manage.py makemigrations
\$ python manage.py migrate
\$ python manage.py createsuperuser

HEROKU

- create a runtime.txt file
  \$ python -V
  python-3.7.3

- create a Procfile
  web: gunicorn vidly.wsgi --log-file -

$ pipenv install django-heroku
$ pipenv install gunicorn

settings.py

    import django_heroku
    <!-- at the bottom -->
    STATIC_ROOT = os.path.join(BASE_DIR,'staticfiles')
    django_heroku.settings(locals())

\$ python manage.py collectstatic # check if it doesnt affect

- create requirements.txt file

\$ pip freeze > requirements.txt

$ heroku login
$ heroku create
$ git push heroku master
$ heroku config:set DISABLE_COLLECTSTATIC=1
$ heroku run python manage.py migrate
$ heroku run python manage.py createsuperuser
\$ heroku open

note:

\$ heroku ps:scale web=1

\$ heroku local web

------------------------------------------------------------

create app
create view
create urls.py
    from django.urls import path
    from . import views

    urlpatterns = [
        path('',views.index, name='index')
    ]
