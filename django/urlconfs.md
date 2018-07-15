# URLconfs / URL dispatcher
To design URLs for an app, you use a Python module called URLconf (URL configuration).

To design URLs for an app, you use a Python module for URL configuration. It is called a URLconf module and named ```urls.py```.

### How Django processes a request
#### Request
1. A user requests a URL
2. Django creates a HttpRequest object that contains metadata about their request

#### Routing / finding the suitable view / URL stuff
1. Django loads the Urlconf module set in ROOT_URLCONF in settings.py
    - However, if the incoming HttpRequest object has a urlconf attribute (set by middleware) that module is used instead
2. Django loads the "urlpatterns" Python list of django.urls.path() and/or django.urls.re_path() instances
3. 

- Django runs through each URL pattern, in order, and stops at the first one that matches the requested URL.
- Once one of the URL patterns matches, Django imports and calls the given view, which is just a function (or a class-based view). The view gets passed the following arguments:
    - An instance of HttpRequest
    - If the matched URL pattern returned no named groups, then the matches from the regular expression are provided as positional arguments.
    - The keyword arguments are made up of any named parts matched by the path expression, overridden by any arguments specified in the optional kwargs argument to django.urls.path() or django.urls.re_path().
- If no URL pattern matches, or if an exception is raised during any point in this process, Django invokes an appropriate error-handling view.




3. It is routed by Django which searches for the appropriate view, and once the correct view is found Django passes the HttpRequest as the first arguement to the view function
4. The view will return a HttpResponse object (all views must return one)


    

<br>

Here’s a sample URLconf module and its urlpatterns list:
```python
from django.urls import path
from . import views

urlpatterns = [
    path('articles/2003/', views.special_case_2003),
    path('articles/<int:year>/', views.year_archive),
    path('articles/<int:year>/<int:month>/', views.month_archive),
    path('articles/<int:year>/<int:month>/<slug:slug>/', views.article_detail),
]
```
A request to:
```
/articles/2005/03/
    Matches: path pattern #3
    Calls the function: views.month_archive(request, year=2005, month=3)

/articles/2003/
    Matches: path pattern #1, not the second, because the patterns are tested in order and the first
             one is the first test to pass. Feel free to exploit the ordering to insert special cases.
    Calls the function: views.special_case_2003(request)

/articles/2003
    Would not match any of these patterns, because each pattern requires that the URL end with a slash.

/articles/2003/03/building-a-django-site/
    Matches: path pattern #4
    Calls the function: views.article_detail(request, year=2003, month=3, slug="building-a-django-site")
```

<br>

#### Path converters
To capture a value from the URL, use angle brackets. Captured values can optionally include a converter type. For example, use \<int:name\> to capture an integer parameter. If a converter isn’t included, any string, excluding a / character, is matched.

There’s no need to add a leading slash, because every URL has that. For example, it’s articles, not /articles.

#### /urls.py
URLs map a url to a view.
```
urlpatterns = [
    path('route/', view, optionalname),
    
    path('admin/', admin.site.urls),
]
```
