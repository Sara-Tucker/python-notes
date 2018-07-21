# URLconfs / URL dispatcher
To design URLs for an app, you use a Python module called URLconf (URL configuration).

To design URLs for an app, you use a Python module for URL configuration. It is called a URLconf module and named ```urls.py```.

<br>
<br>

## How Django processes a request:
#### Request
1. A user requests a URL
2. Django creates a HttpRequest object that contains metadata about their request

#### URL routing / finding the suitable view
1. Django loads the Urlconf module set in ROOT_URLCONF in settings.py
    - However, if the incoming HttpRequest object has a urlconf attribute (set by middleware) that module is used instead
2. Django loads the "urlpatterns" list of django.urls.path() and/or django.urls.re_path() instances
3. Django iterates over each URL pattern, in order, and stops at the first one that matches the requested URL
    - If no URL pattern matches, or if an exception is raised during any point in this process, Django invokes an appropriate error-handling view

#### The view
1. Once a URL pattern matches the requested URL, Django imports and calls the given view function and passes the HttpRequest as the first arguement
    - If the matched URL pattern returned no named groups, then the matches from the regular expression are provided as positional arguments
    - The keyword arguments are made up of any named parts matched by the path expression, overridden by any arguments specified in the optional kwargs argument to django.urls.path() or django.urls.re_path()
2. The view returns a HttpResponse object

<br>
<br>

#### /urls.py
urlpatterns map a url to a view.
```
urlpatterns = [
    path('mysite/', view, optionalname),
    
    path('admin/', admin.site.urls),
]
```

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

### Path converters
To capture a value from the URL, use angle brackets. Captured values can optionally include a converter type. For example, use \<int:name\> to capture an integer parameter. If a converter isn’t included, any string, excluding a / character, is matched.

There’s no need to add a leading slash, because every URL has that. For example, it’s articles, not /articles.

<br>

### What the URLconf searches against
The URLconf searches for the requested URL, as a normal Python string. It doesn't include GET or POST parameters, or the domain name. The URLconf doesn’t look at the request method. In other words, all request methods – POST, GET, HEAD, etc. – will be routed to the same function for the same URL.

For example for a request to:
```
https://www.example.com/myapp/ - the URLconf will look for myapp/

https://www.example.com/myapp/?page=3 - the URLconf will look for myapp/
```

<br>

### Using "include"
At any point, your urlpatterns can “include” other URLconf modules. This essentially “roots” a set of URLs below other ones.

For example, here’s an excerpt of the URLconf for the Django website itself. It includes a number of other URLconfs:
```python
from django.urls import include, path

urlpatterns = [
    path('community/', include('aggregator.urls')),
    path('contact/', include('contact.urls')),
]
```
Whenever Django encounters include(), it chops off whatever part of the URL matched up to that point and sends the remaining string to the included URLconf for further processing.

Another possibility is to include additional URL patterns by using a list of path() instances. For example, consider this URLconf:
```python
from django.urls import include, path

from apps.main import views as main_views
from credit import views as credit_views

urlpatterns = [
    path('', main_views.homepage),
    path('help/', include('apps.help.urls')),
    path('credit/', include(extra_patterns)),
]

extra_patterns = [
    path('reports/', credit_views.report),
    path('reports/<int:id>/', credit_views.report),
    path('charge/', credit_views.charge),
]
```
This can be used to remove redundancy from URLconfs where a single pattern prefix is used repeatedly. For example, consider this URLconf:
```python
from django.urls import include, path
from . import views

urlpatterns = [
    path('<page_slug>-<page_id>/history/', views.history),
    path('<page_slug>-<page_id>/edit/', views.edit),
    path('<page_slug>-<page_id>/discuss/', views.discuss),
    path('<page_slug>-<page_id>/permissions/', views.permissions),
]

#We can improve this by stating the common path prefix only once and grouping the suffixes that differ

urlpatterns = [
    path('<page_slug>-<page_id>/', include([
        path('history/', views.history),
        path('edit/', views.edit),
        path('discuss/', views.discuss),
        path('permissions/', views.permissions),
    ])),
]
```

<br>

### Passing extra options to view functions
URLconfs have a hook that lets you pass extra arguments to your view functions, as a Python dictionary. The path() function can take an optional third argument which should be a dictionary of extra keyword arguments to pass to the view function.

For example:
```python
from django.urls import path
from . import views

urlpatterns = [
    path('blog/<int:year>/', views.year_archive, {'foo': 'bar'}),
]
```
In this example, for a request to /blog/2005/, Django will call views.year_archive(request, year=2005, foo='bar'). This technique is used in the syndication framework to pass metadata and options to views.

Similarly, you can pass extra options to include() and each line in the included URLconf will be passed the extra options.
```python
# main.py
from django.urls import include, path

urlpatterns = [
    path('blog/', include('inner'), {'blog_id': 3}),
]


# inner.py
from django.urls import path
from mysite import views

urlpatterns = [
    path('archive/', views.archive),
    path('about/', views.about),
]
```
Note that extra options will always be passed to every line in the included URLconf, regardless of whether the line’s view actually accepts those options as valid. For this reason, this technique is only useful if you’re certain that every view in the included URLconf accepts the extra options you’re passing.
