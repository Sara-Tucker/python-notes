# Django

#### CRUD - Create, Read, Update, Delete
CRUD are the four functions that models should always have.  
are the four basic functions of a database.

- Create — take all the fields for a database item and create a new item
- Read — display a database item and all the items
- Update — change existing database items
- Delete — supply one or more fields of the database item to be able to search it, and delete the item

<br>

Operation |	SQL	| RESTful WS (HTTP)
--- | --- | ---
Create | INSERT | POST
Read (Retrieve) |	SELECT | GET
Update (Modify) |	UPDATE | PUT
Delete | DELETE | DELETE

<br>

#### User interface
CRUD is also relevant at the user interface level of most applications. As a bare minimum, the software must allow the user to:

- Create or add new entries
- Read, retrieve, search, or view existing entries
- Update or edit existing entries
- Delete/deactivate/remove existing entries

Without at least these four operations, the software cannot be considered complete. Because these operations are so fundamental, they are often documented and described under one comprehensive heading, such as "content management".

<br>

#### CRUD and REST
In a REST environment, CRUD often corresponds to the HTTP methods POST, GET, PUT, and DELETE. These are the fundamental elements of a persistent storage system (database).

Throughout the rest of the article, we will recommend standards and response codes that are typically followed by developers when creating RESTful applications.

Imagine we are working with a system that is keeping track of meals and their corresponding prices for a restaurant. Let’s look at how we would implement CRUD operations.

#### Create
To create resources in a REST environment, we most commonly use the HTTP POST method. POST creates a new resource of the specified resource type.

For example, let’s imagine that we are adding a new food item to the stored list of dishes for this restaurant, and the dish objects are stored in a dishes resource. If we wanted to create the new item, we would use a POST request:

Request:
```python
POST http://www.myrestaurant.com/dishes/


# Body
{
  "dish": {
    "name": “Avocado Toast”,
    "price": 8
  }
}
```
This creates a new item with a name value of “Avocado Toast” and a price value of 8. Upon successful creation, the server should return a header with a link to the newly-created resource, along with a HTTP response code of 201 (CREATED).

Response:
```python
Status Code - 201 (CREATED)


# Body
{
  "dish": {
    "id": 1223,
    "name": “Avocado Toast”,
    "price": 8
  }
}
```
From this response, we see that the dish with name “Avocado Toast” and price 8 has been successfully created and added to the dishes resource.

<br>

#### Read
To read resources in a REST environment, we use the GET method. GET can be used to read an entire list of items.

Request:
```python
GET http://www.myrestaurant.com/dishes/
```

Response:
```py
Status Code - 200 (OK)


# Body
{
  "dishes": [
    {
      "id": 1,
      "name": “Spring Rolls”,
      "price": 6
    },
    {
      "id": 2,
      "name": “Mozzarella Sticks”,
      "price": 7
    },
    ...
    {
      "id": 1224,
      "name": “Muesli and Yogurt”,
      "price": 5
    }
  ]
}
```

GET requests can also be used to read a specific item, when its id is specified in the request:

Request:
```python
GET http://www.myrestaurant.com/dishes/1223
```

Response:
```python
Status Code - 200 (OK)


# Body
{
  "id": 1223,
  "name": “Avocado Toast”,
  "price": 8
}
```
After this request, no information has been changed in the database. The item with id 1223 has been retrieved from the dishes resource, and not modified. When there are no errors, GET will return the HTML or JSON of the desired resource, along with a 200 (OK) response code. If there is an error, it most often will return a 404 (NOT FOUND) response code.

<br>

#### Update
PUT is the HTTP method used for the CRUD operation, Update.

For example, if the price of Avocado Toast has gone up, we should go into the database and update that information. We can do this with a PUT request.

Request:
```python
PUT http://www.myrestaurant.com/dishes/1223


#Body
{
  "dish": {
    "name": “Avocado Toast”,
    "price": 10
  }
}
```
This request should change the item with id 1223 to have the attributes supplied in the request body. This dish with id 1223 should now still have the name “Avocado Toast”, but the price value should now be 10, whereas before it was 8.

Response:
```python
Status Code - 200 (OK)

# Body - not necessary
```
The response includes a Status Code of 200 (OK) to signify that the operation was successful, but it need not return a response body.

<br>

#### Delete
The CRUD operation Delete corresponds to the HTTP method DELETE. It is used to remove a resource from the system.

Let’s say that the world avocado shortage has reached a critical point, and we can no longer afford to serve this modern delicacy at all. We should go into the database and delete the item that corresponds to “Avocado Toast”, which we know has an id of 1223.

Request:
```python
DELETE http://www.myrestaurant.com/dishes/1223
```

Such a call, if successful, returns a response code of 204 (NO CONTENT), with no response body. The dishes resource should no longer contain the dish object with id 1223.

Response:
```python
Status Code - 204 (NO CONTENT)

Body - None
```

Calling GET on the dishes resource after this DELETE call would return the original list of dishes with the {"id": 1223, "name": “Avocado Toast”, "price": 10} entry removed. All other dish objects in the dishes resource should remain unchanged. If we tried to call a GET on the item with id 1223, which we just deleted, we would receive a 404 (NOT FOUND) response code and the state of the system should remain unchanged.

Calling DELETE on a resource that does not exist should not change the state of the system. The call should return a 404 response code (NOT FOUND) and do nothing.





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

#### Admin:
```
$ manage.py createsuperuser
```

Make an app modifiable in the admin:
```python
# polls/admin.py

from django.contrib import admin
from .models import MyModel

admin.site.register(MyModel)
```

<br>

#### manage.py makemigrations:
After making a change to a model you need to run this.

By running makemigrations, you’re telling Django that you’ve made some changes to your models (in this case, you’ve made new ones) and that you’d like the changes to be stored as a migration.

Migrations are how Django stores changes to your models (and thus your database schema) - they’re just files on disk. You can read the migration for your new model if you like; it’s the file polls/migrations/0001_initial.py.
```
$ manage.py makemigrations
```

<br>

#### manage.py migrate:
The migrate command looks at the INSTALLED_APPS setting and creates any necessary database tables.
```
$ manage.py migrate
```

<br>
<br>
<br>

Middleware is in settings.py

database schema (CREATE TABLE statements)

Package - a directory of code  
https://docs.python.org/3/tutorial/modules.html

<br>
<br>
<br>

---

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
