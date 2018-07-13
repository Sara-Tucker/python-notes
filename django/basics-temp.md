# Django

#### Create a Django project (environment):
```
$ django-admin startproject mysite
```

<br>

#### Project directory:
```
mysite/
    manage.py - a command-line utility
    mysite/ - the actual Python package for your project; its name is what you’ll use to
                                             import anything inside it (e.g. mysite.urls)
        __init__.py
        settings.py - settings for the django project
        urls.py - the url declarations
        wsgi.py
```

<br>

#### Run the development server:
```
(cd to the manage.py directory)
$ manage.py runserver
```
The development server automatically reloads Python code for each request as needed.  
You don’t need to restart the server for code changes to take effect.  
However, some actions like adding files don’t trigger a restart, so you’ll have to restart the server in these cases.

<br>

#### Create an app:
Django apps are “pluggable”. You can use an app in multiple projects, because they don’t have to be tied to a given Django installation.
```
$ manage.py startapp appname
```
That’ll create a directory called appname, which will house the app and is laid out like this:
```
appname/
    __init__.py
    admin.py
    apps.py
    migrations/
        __init__.py
    models.py
    tests.py
    views.py
```

<br>

#### Create a view:
```python
# open appname/views.py
from django.http import HttpResponse

def index(request):
    return HttpResponse("Hello, world. You're at the appname index.")
```

<br>

#### /urls.py
URLs map a url to a view.
```
urlpatterns = [
    path('route/', view, optionalname),
    
    path('admin/', admin.site.urls),
]
```

<br>

#### manage.py migrate:
The migrate command looks at the INSTALLED_APPS setting and creates any necessary database tables.
```
$ manage.py migrate
```

<br>


#### manage.py makemigrations:
After making a change to a model you need to run this.

The migrate command looks at the INSTALLED_APPS setting and creates any necessary database tables.

By running makemigrations, you’re telling Django that you’ve made some changes to your models (in this case, you’ve made new ones) and that you’d like the changes to be stored as a migration.

Migrations are how Django stores changes to your models (and thus your database schema) - they’re just files on disk. You can read the migration for your new model if you like; it’s the file polls/migrations/0001_initial.py. Don’t worry, you’re not expected to read them every time Django makes one, but they’re designed to be human-editable in case you want to manually tweak how Django changes things.
```
$ manage.py makemigrations
```

<br>

#### Request and response objects
Requests and responses go through middleware. Think of middleware as your house window, where requests go out and responses come in, both of them going through the window.

Middleware in settings.py
```python
def home_view(request):
    return HttpResponse('Hello world')
    
def home_view(request):
    response = HttpResponse()
    
    response.write('<p>Web page text.</p>')
    # use other methods here to customize the response
    
    return response
```

<br>
<br>
<br>

database schema (CREATE TABLE statements)

Package - a directory of code  
https://docs.python.org/3/tutorial/modules.html

<br>
<br>
<br>
<br>
<br>

Middleware - software components that are assembled into an application pipeline to handle requests and responses.

Middleware in ASP.NET Core controls how our application responds to HTTP requests. It can also control how our application looks when there is an error, and it is a key piece in how we authenticate and authorize a user to perform specific actions.

Each component chooses whether to pass the request on to the next component in the pipeline, and can perform certain actions before and after the next component is invoked in the pipeline.

Request delegates are used to build the request pipeline. The request delegates handle each HTTP request.

Each piece of middleware in ASP.NET Core is an object, and each piece has a very specific, focused, and limited role.

Ultimately, we need many pieces of middleware for an application to behave appropriately.


Logging middleware component:
This logger can see everything about the incoming request, but chances are a logger is simply going to record some information and then pass along this request to the next piece of middleware.


An ASP.NET Core web application is actually a console project which starts executing from Main() in the Program class where we can create a host for the web application. 
Every ASP.NET Core web application requires a host to be executed. A host must implement IWebHost interface.


MVC Architectural Pattern
Model View Controller

An architectural pattern for implementing user interfaces.


Model:
Application data and behaviour in terms of its problem domain, and independent of the UI.

Domain Model of the movie app: classes will be:
- Movie
- Customer
- Rental
- Transaction

These classes have properties and methods which represent the application state and rules. They are not tied to the user interface, meaning they could be used the same for a desktop or mobile app.


View:
HTML markup displayed to the user.


Controller:
Responsible for handing a http request.


Example:
if a user requests http://vidly.com/movies, a Controller will be selected to handle their request. The Controller will get all the movies from the database (Model) and put them in a View and return the View to the user's browser.


Router:
Almost always part of MVC but not in the acronym. Selects the right Controller to handle a request. The Router knows that the request for http://vidly.com/movies should be handled by the MoviesController class Controller, (or more accurately the request should be handled by a method of that class). The methods of a controller are called Actions. So techincally an Action (method) of the class will handle the request.


MVC allows for:
Separation of concerns
More maintainable applications
