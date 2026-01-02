## In chapter 1 (Creating a django project) we learn't about 
### The role of backend developer.

The backend development handles the behind the scenes of modern applications. Most of the time it's made of code that connects to the database, manages user connections and also powers web application or the API.
### What is client - server architecture.

The client server architecture represents an environment in which applications running on a client machine can interact with applications running on a server which provides services or a data from database.

### What is API ? What are RESTful APIs.

An API (Application Programming Interface) is a bridge that let's two different pieces of software communicate with each other using predefined set of rules.

The RESTful (Representatinal State Transfer) APIs are a type of api. It's not a piece of software it's a style you follow. If your api looks like this, it is REST api.

1. Everything is a resource, like for ex: Post /post, User /user, Comment /comment.

2. Use HTTP Verbs like GET, PUT , POST, PATCH , DELETE.

- GET: "Give me this." (Fetching a list of blog posts).

- POST: "Create this." (Submitting a new blog post).

- PUT: "Replace this." (Updating an entire post).

- PATCH: "Fix this part." (Changing just the title of a post, not the whole thing).

- DELETE: "Remove this." (Deleting the post).

### What is venv.

A venv is used to keep the working env isolated and avoid version conflicts.

### What is django.

Django is a web framework written in python, which follows MVC (Model View Controller) architectural pattern. But in Django it is used as MVT (Model View Template).

M - Model (Data) = This is a python class that defines your database table. Instead of writing raw sql, you write python code. Handles everything related to data -- validation, storage and retreival.

V - View (Logic) = This is the brain of django. This is the part that handles business logic. It receives an HTTP request, fetches the right data from the model and passes it to the template.

T - Template (Presentation) = This is the face of the application. It is usually an HTML file mixed with django templace language (DTL). It displays the data.

### How to initialize the demo project to check setup of django.

First create the venv `python -m venv venv`. 

Activate the venv `source venv/bin/activate`

Create a requirement.txt file and in that write `django`

Now install the requirements using `pip install -r requirements.txt`

Now run this command in order to create a demo project `python -m django startproject CoreRoot .`

Now perform migrations `python manage.py migrate`

###  File structure of django.

Root level files : 
 - manage.py = This is the command line utility that helps you interact with your django project. You use it to run server. Create database tables, create new apps.

- db.sqlite3 = This is the actual database. Because django comes pre-configured with sqlite. Which stores your data in single file.

    The config folder (CoreRoot)
    - __init__.py : An empty file that tells python to treat this directory as a package. This allows you to import settings from this folder into other parts of your code. 

    - settings.py : It containes your db connection info, list of installed apps, security keys and middleware.

    - urls.py : It maps url address like /home , /api/login to specific views.

    - wsgi.py and asgi.py : These are web server interfaces.
    wsgi = Web server gateway interface is the standard for synchronous web servers. 

    - asgi = Asynchronous server gateway interface. Newer version that allows django to handle things like websocket or 'async' code for faster performance.

    - A web server like (Nginx, Apache) don't speak python. It speaks HTTP, so these files act the bridge that translates those HTTP to format that django can understand.

    - __pycache__ : A folder created by python automatically. It stores compiled version of your code. so that your app starts up faster the next time you run it. You should ignore this folder.

###  How to setup postgres database and grant permissions.

First install `pip install psycopg2-binary`

This psycopg2-binary helps your django code to talk to postgresql database. It translates the python/django commands to sql that PGSQL understands. 

The -binary version comes pre-compiled. This means you install it instantly without needing complex extra tools.

After installing add it to your requirements.txt file.

Then in command line do following: 

`psql postgres`

`CREATE DATABASE coredb;`

`CREATE USER core WITH PASSWORD 'aman'`

`GRANT ALL PRIVILEGES ON DATABASEcoredb TO core;`

`ALTER USER core CREATEDB;`

###  How to connect django application to postgres database

In settings.py file, copy paste the following credentials.

```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME' : 'coredb',
        'USER' : 'core',
            'PASSWORD' : 'aman',
        'HOST' : 'localhost',
        'PORT' : '5432',
        }
}
```


