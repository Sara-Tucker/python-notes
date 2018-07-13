The view layer:  
Django uses views to encapsulate the logic responsible for processing a user’s request and for returning the response. The model layer is made up of different parts.

# URLconfs / URL dispatcher
To design URLs for an app, you create a Python module called a URLconf (URL configuration).

#### How Django processes a request
When a user requests a page from your Django-powered site, this is the algorithm the system follows to determine which Python code to execute:

    Django determines the root URLconf module to use. Ordinarily, this is the value of the ROOT_URLCONF setting, but if the incoming HttpRequest object has a urlconf attribute (set by middleware), its value will be used in place of the ROOT_URLCONF setting.
    Django loads that Python module and looks for the variable urlpatterns. This should be a Python list of django.urls.path() and/or django.urls.re_path() instances.
    Django runs through each URL pattern, in order, and stops at the first one that matches the requested URL.
    Once one of the URL patterns matches, Django imports and calls the given view, which is a simple Python function (or a class-based view). The view gets passed the following arguments:
        An instance of HttpRequest.
        If the matched URL pattern returned no named groups, then the matches from the regular expression are provided as positional arguments.
        The keyword arguments are made up of any named parts matched by the path expression, overridden by any arguments specified in the optional kwargs argument to django.urls.path() or django.urls.re_path().
    If no URL pattern matches, or if an exception is raised during any point in this process, Django invokes an appropriate error-handling view. See Error handling below.



<br>
<br>

# Views
A view function is a Python function that takes a Web request and returns a Web response. This response can be the HTML contents of a Web page, a 404 error, an XML document, an image, or anything really. The view itself contains whatever arbitrary logic is necessary to return that response. The convention is to put views in a views.py file.

<br>

#### A View:
```python
from django.http import HttpResponse

# the view function (aka view)
def view_name(request):
    # view functions take a HttpRequest object as a first parameter (typically named request)
    html = "<html>The page HTML goes here.</html>"
    
    # a view returns a HttpResponse object that contains the generated response
    return HttpResponse(html)
```

<br>

#### Returning errors:
You can pass the HTTP error code into the constructor for HttpResponse to create a return class for any error code.
```python
from django.http import HttpResponse

def my_view(request):
    # ...

    # Return a "created" (201) response code.
    return HttpResponse(status=201)
```

<br>

#### HttpResponseNotFound 404:
In order to show customized HTML when Django returns a 404, you can create an HTML template named 404.html and place it in the top level of your template tree. This template will then be served when DEBUG is set to False.

When DEBUG is True, you can provide a message to Http404 and it will appear in the standard 404 debug template. Use these messages for debugging purposes; they generally aren’t suitable for use in a production 404 template.
```python
raise Http404('Custom message')

# Example:
from django.http import Http404
from django.shortcuts import render
from polls.models import Poll

def detail(request, poll_id):
    try:
        p = Poll.objects.get(pk=poll_id)
    except Poll.DoesNotExist:
        raise Http404("Poll does not exist")
    return render(request, 'polls/detail.html', {'poll': p})
```

