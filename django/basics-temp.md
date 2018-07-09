# Django

#### Create a Django project(environment):
```
$ django-admin startproject mysite
```

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

#### Run the development server:
cd to the directory with manage.py
```
$ manage.py runserver
```
The development server automatically reloads Python code for each request as needed.  
You don’t need to restart the server for code changes to take effect.  
However, some actions like adding files don’t trigger a restart, so you’ll have to restart the server in these cases.

#### Create an app:
To create your app, make sure you’re in the same directory as manage.py and type this command:
```
$ manage.py startapp polls
```
That’ll create a directory called polls, which will house the app and is laid out like this:
```
polls/
    __init__.py
    admin.py
    apps.py
    migrations/
        __init__.py
    models.py
    tests.py
    views.py
```


Package - a directory of code  
https://docs.python.org/3/tutorial/modules.html

<br>
<br>
<br>
<br>
<br>

ASP.NET Core is a web framework. The old version is ASP.NET 4. ASP.NET Core includes the MVC framework.

.NET - old
.NET Core - new

ASP.NET - Web app
ASP.NET Core - .NET Core - Web app
ASP.NET Core - .NET - Web app

- .csproj - dependencies for libraries and frameworks
- Startup.cs - the Startup class configures your application
    - Configure() method - where you build your HTTP processing pipeline.



Middleware - software components that are assembled into an application pipeline to handle requests and responses.

Middleware in ASP.NET Core controls how our application responds to HTTP requests. It can also control how our application looks when there is an error, and it is a key piece in how we authenticate and authorize a user to perform specific actions.

Each component chooses whether to pass the request on to the next component in the pipeline, and can perform certain actions before and after the next component is invoked in the pipeline.

Request delegates are used to build the request pipeline. The request delegates handle each HTTP request.

Each piece of middleware in ASP.NET Core is an object, and each piece has a very specific, focused, and limited role.

Ultimately, we need many pieces of middleware for an application to behave appropriately.


Logging middleware component:
This logger can see everything about the incoming request, but chances are a logger is simply going to record some information and then pass along this request to the next piece of middleware.


wwwroot (web root) folder - files served over an http request


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


#### Project solution explorer:
- App_Data - where the database file will be stored
- App_Start - classes that are called when the application is started
    - RouteConfig - the configuration of the routing rules
        - url: "{controller}/{action}/{id}"
            - the controller used, the Action of that controller, id is an argument passed to that Action
            - Example: request to /movies/popular
            - {controller} = MoviesController
            - {action} = Popular()
            - Example: request to /movies/edit/351
            - {controller} = MoviesController
            - {action} = Edit(int id)
        - defaults: new { controller = "Home", action = "Index", id = UrlParameter.Optional }
            - Example: if url doesn't have anything in the url ^ thing above -> passed to HomeController
            - Example: /movies -> handled by the MoviesController.Index() Action
            - id is an optional parameter
- Content - store client side assets (.css, images)
- Controllers
    - AccountController - Actions for sign in, log out, etc
    - HomeController - homepage
    - ManageController - Actions for users to manage their profiles
- Models - all the domain classes will be here
- Scripts - JS files
- Views
- Startup.cs (old ver is Global.asax) - provides hooks for various events in the application's life cycle. Contains method that is called when app is started. It registers a few things, like the routes.
packages.config - used by NuGet package manager. Package managers manage the dependencies of the app.
    - Example: if app has dependencies on 5 external libraries. instead of going to 5 different sites and downloading them, NuGet gets all the packages for you.
- Web.config - xml doc of the apps config. <connectionStrings> and <appSettings> are most used.


Partial View - not a complete page. A widget that can be used on different Views.
Layout page - a template or master page. if you want all your pages to have the same look and feel use a layout.
