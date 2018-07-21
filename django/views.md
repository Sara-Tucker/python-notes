# Views
A view function is a function that is passed a Web request and returns a Web response. This response can be the HTML contents of a Web page, a 404 error, an XML document, an image, or anything really. The view itself contains whatever arbitrary logic is necessary to return that response. The convention is to put views in a views.py file.

Views encapsulate the logic responsible for processing a user’s request and return the response.

In Django, web pages and other content are delivered by views. Each view is represented by a simple Python function (or method, in the case of class-based views). Django will choose a view by examining the part of the requested URL after the domain name.

A view is a function responsible for rendering a page.

<br>

#### A View:
```python
# the file is likely appname/views.py
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

<br>

#### CRUD List view / Query sets
```python
#views.py

from .models import MyModel

def my_model_list_view(request):
    qs = MyModel.objects.all()
    return render(????????????????????????)
```

<br>

#### View decorators
The decorators in django.views.decorators.http can be used to restrict access to views based on the request method. These decorators will return a django.http.HttpResponseNotAllowed if the conditions are not met.

- require_GET()
- require_POST()
- require_http_methods(request_method_list)
    - Decorator to require that a view only accepts specified request methods.
```python
from django.views.decorators.http import require_http_methods

@require_http_methods(["GET", "POST"])
def my_view(request):
    # I can assume now that only GET or POST requests make it this far
    #code
```

<br>
<br>

### django.shortcuts
#### render(request, template_name, context=None, content_type=None, status=None, using=None)
Combines a given template with a given context dictionary and returns an HttpResponse object with that rendered text.

Required arguments:
- request - The request object used to generate this response.
- template_name - The full name of a template to use or sequence of template names. If a sequence is given, the first template that exists will be used.

Optional arguments:
- context - A dictionary of values to add to the template context. By default, this is an empty dictionary. If a value in the dictionary is callable, the view will call it just before rendering the template.
- content_type - The MIME type to use for the resulting document.
- status - The status code for the response. Defaults to 200.
- using - The NAME of a template engine to use for loading the template.

The following example renders the template myapp/index.html with the MIME type application/xhtml+xml:
```python
from django.shortcuts import render

def my_view(request):
    # View code here...
    return render(request, 'myapp/index.html', {'foo': 'bar'},
    content_type='application/xhtml+xml')
```

<br>

#### redirect(to, permanent=False, \*args, \*\*kwargs)
Returns an HttpResponseRedirect to the appropriate URL for the arguments passed. The arguments could be:
- A model: the model’s get_absolute_url() function will be called.
- A view name, possibly with arguments: reverse() will be used to reverse-resolve the name.
- An absolute or relative URL, which will be used as-is for the redirect location.

By default, redirect() returns a temporary redirect; pass permanent=True to issue a permanent redirect.

You can use the redirect() function in a number of ways:

By passing some object; that object’s get_absolute_url() method will be called to figure out the redirect URL:
```python
from django.shortcuts import redirect

def my_view(request):
    # ...
    object = MyModel.objects.get(...)
    return redirect(object)
```

By passing the name of a view and optionally some positional or keyword arguments; the URL will be reverse resolved using the reverse() method:
```python
def my_view(request):
    # ...
    return redirect('some-view-name', foo='bar')
```

By passing a hardcoded URL to redirect to:
```python
def my_view(request):
    # ...
    return redirect('/some/url/')
    # or
    return redirect('https://example.com/')
```

<br>

[get_object_or_404()](https://docs.djangoproject.com/en/2.0/topics/http/shortcuts/#get-object-or-404)  
[get_list_or_404()](https://docs.djangoproject.com/en/2.0/topics/http/shortcuts/#get-list-or-404)
