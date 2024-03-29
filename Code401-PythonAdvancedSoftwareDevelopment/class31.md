# A Beginner's Guide to Docker

- Docker is a way to isolate and run entire applications.
- The entire development env is isolated: programming language, software packages, databases, and more.
- Don't need virtual environments.
- Can be shared among team members so everyone is working on the same setup.
- Docker is complex under the hood.

## Linux Containers

- Docker is basically Linux Containers which are a type of virtualization.
- Virtual machines are complete copies of a computer system from the operating system on up.
- Linux Containers, also known as "containerization," has become increasingly popular.
- A virtual machine provides far more resources than are needed and a container is more than sufficient.

## Containers vs Virtual Env

- VE are used to isolate Python software packages locally.
- VE are limited to only isolating these packages.. they still rely on a global, system-level installation of Python.

## Install Docker

- To install Docker we need to download the desktop app on your computer and create a free account.
- Docker Compose is an additional tool that is automatically included with Mac and Windows download of Docker.
- A good command to inspect Docker is `docker info`. It contains a lot of output but focus on the top lines which show we now have 1 container which is `stopped` and 1 image.

## Images and Containers

- Images and containers are the two fundemental concept to grasp when you start with Docker. An image is a snapshot in time of what a project contains.
- A container is a running instance of the image.
- A `Dockerfile` is the recipe for a cake
- An image is a snapshot of the recipe at a given time
- A `docker-compose.yml` says how to make the cake
- And the contianer is teh actual, baked cake.

## Images

- First create a local directory on your computer for your code.
- define teh image with a `Dockerfile`.. on a mac run `touch Dockerfile`
- with text editor add the following single linek of code to the `Dockerfile` # Dockerfile
- Dockerfiles are read from top-to-bottom. The first instruction must be the `FROM` commnad which lets us import a base image to use for our image.

## Image Builds

- to "build" or create the image for the first time. Don't forget to add the period `.` at the end of the command.
$ docker image build .
Sending build context to Docker daemon  2.048kB
Step 1/1 : FROM python:3.7-alpine
3.7-alpine: Pulling from library/python
c9b1b535fdd9: Pull complete
2cc5ad85d9ab: Pull complete
53a2fca3c2ea: Pull complete
30fce49de8b1: Pull complete
49bcb9571cc7: Pull complete
Digest: sha256:7655eea15dfd981eeb7d243af21e8561e967709caba938d50b136cdb992f3546
Status: Downloaded newer image for python:3.7-alpine
 ---> b2c276538711
Successfully built b2c276538711

## Image Layers

- Every image is made up of one or more image layers. The base layer is often a flavor of Linux, like `alpine`.
- Each image layer is immutabvle-unchange-like a git commit. This helps ensure consistency when two devs build the same image.
- Docker caches the steps in a `Dockerfile` to speed up subsequent builds. When a chagne is made to a step, all steps following it will be executed from scratch.
- Order matters in a `Dockerfile` so typically you'll want to put code that won't change often at the top.

## Containers

- `docker-compose.yml` file is a list of contianer instructions.
- Docker can run a web application completely on its own.
- Create a new django project from scratch
- add project `django-admin startproject example_project`
- run server `python manage.py runserver`
- stop the local server with `control + c` and exit the virtual env by typing `exit`

## Dockerized Django

- create a `Dockerfile` for our image which will completely replace our local dev env.
- Then add `docker-compose.yml` for the container instructions. Make each file via the command line.
`touch Dockerfile`
`touch docker-compose.yml`
- Dockerfile has several commands. `RUN`, `COPY`, and `ADD` each create a new labyer.
- Use `FROM` to install python: 3.7-alpine as our base image and ste two env variable with `ENV`.
- The first, `PTYHONDONTWRITEBYTECODE` will remove the `.pyc` files from our container which is good optimization.
- The second, `PYTHONUNBUFFERED` will buffer our ouput so it will look "normal" within Docker for us.
- The use the `WORKDIR` command to create and set `/code` as our default directory within Docker.
- Copy over the `Pipfile` 
- Install Pipenv itself via pip and then run `pipenv install` to install the software packages in our Pipfile. 

## Django for APIs

- Django REST FW works alongside the Django web framework to create web APIs.
- always must be added to a prject after Django itself has been installed and configured.
- Django created websites containing webpages, while Django REST FW creates web APIs which are a colleciton of URL endpoints containing available HTTP verbs that return JSON data.

## Traditional Django

- a traditional Django webiste consists of a single project and one (or more) apps representing discrete functionality.
- `__init__.py` is a python way to treat a directory as a package.
- `asgi.py` stands for Asynchronous Server Gateway Interface and is a new option in Django 3.0+
- `setting.py` contains all the config for the project.
- `urls.py` controls teh top-level URL routes.
- `wsgi.py` Web Sever Gateway Interface and helps Django serve the eventual web pages.
- `manage.py` executes various Django commands such as running the local server or creating a new app.
- Run `migrate` to sync the databse with Django's default settings and start up the local Django web server. `python manage.py migrate`

## First App

- start adding apps by running `python manage.py startapp app_name`
- each app has a `__init__.py` file identifying it as a Python package.
- There are 6 new files created: 
- `admin.py` a configuration file for the built-in Django Admin app
- `apps.py` a config file for the app itself
- `migrations/` direcotry stores migrations files for database changes
- `models.py` is where we define our database models.
- `tests.py` is for our app-specific tests.
- `view.py` is where we handle the request/response logic for our web app.
- devs will also create a `urls.py` file within each app to for app level url routing.
- add new app to the `settings.py` file inside the `INSTALLED_APPS` configuration. Add at the top of this list.
- then run `migrate` to sync our database with the changes. `python manage.py migrate`

## Models

- open up the `new_app/model.py` and update the following:
from django.db import models

class Book(models.Model):
    title = models.CharField(max_length=250)
    subtitle = models.CharField(max_length=250)
    author = models.CharField(max_length=100)
    isbn = models.CharField(max_length=13)

    def __str__(self):
        return self.title
- this is a basic Django model where we import `models` from Django on the top line and then create a `Book` class that extends it.
- Including is the `__str__` method so that the title of a book will displayt in the admin later on.
- Since we created a new database model, we need to create a migration file to go along with it, then update our database. `python manage.py makemigrations new_app` `python manage.py migrate`

## Admin

- We can start entering data into the new model via the built-in Django app. but first you must create a superuser account and update `admin.py` so the `new_app` app is displayed.
- createsuper run: `python manage.py createsuperuser`
- follow the prompts to enter username, email and password.
- update the `new_app` app's `admin.py` file.
from django.contrib import admin
from .models import New_App

admin.site.register(New_APP)

## Views

- The `views.py` file controls how the database model content is displayed.
- Use the built-in generic class `ListView` to list item in our new app.
- Update the `new_app/view.py` file:
from django.views.generic import ListView
from .models import New_APP

class AppListView(ListView):
    model = Book
    template_name = 'new_app_list.html'
- import `ListView` and our `New_App` model, then create a `New_AppListView` class that specifies the model to use and the template.

## URLs

- we need to set up both the project-level `urls.py` file and the app-level `urls.py`
- from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('books.urls')),
]

## Django REST Framework

- `poetry add djangorestframework`
- add to the `INSTALLED_APPS` config in our `settings.py` file.
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',

    # 3rd party
    'rest_framework', # new

    # Local
    'books',
]
- our API will expose a single endpoint that list out all books in JSON and we'll need a new URL route, a new view, and a new serializer file.
- Create a dedicated `api` app by running `pythoon manage.py startapp api`
- add to the `INSTALLED_APPS` LIST.
- THE `api` app will not have its own database models so no need to create migration file and run `migrate` to update the DB.

## URLs

- adding an API endpoint is just like configuring a traditional Django app's routes.
- add route to project-level `urls.py` file in the `urlpatterns = [path('api/', include('api.urls'))]`
- create a `urls.py` file in the `api` app and add the following lines of code.
from django.urls import path
from .views import BookAPIView

urlpatterns = [
    path('', BookAPIView.as_view()),
]

## Views

- the `views.py` field relies on Django REST Framework's built-in generic class views.
- to avoid confusion, call API view file `apiviews.py` or `api.py`
- Within the `apiviews.py` file, update the following code:
from rest_framework import generics

from books.models import Book
from .serializers import BookSerializer


class BookAPIView(generics.ListAPIView):
    queryset = Book.objects.all()
    serializer_class = BookSerializer

## Serializers

- A serializer translates data into a format that is easy to consumer over the internet, typically JSON, and is displayed at an API endpoint.
- make a `serializer.py` file within our `api` app then update the following code.
from rest_framework import serializers

from books.models import Book


class BookSerializer(serializers.ModelSerializer):
    class Meta:
        model = Book
        fields = ('title', 'subtitle', 'author', 'isbn')

## cURL

- use the popular cURL program to execute HTTP request via the command line. All we need for a basic `GET` request is to specify `curl` and the URL we want to call.
