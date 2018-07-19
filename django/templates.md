# Templates
Templates generate HTML dynamically. A template contains the static parts of the desired HTML output as well as some special syntax describing how dynamic content will be inserted.

Django defines a standard API for loading and rendering templates regardless of the backend. Loading consists of finding the template for a given identifier and preprocessing it, usually compiling it to an in-memory representation. Rendering means interpolating the template with context data and returning the resulting string.

#### Configuration:
DIRS defines a list of directories where the engine should look for template source files, in search order.
```python
# /settings.py

TEMPLATES = [
    {
        'DIRS': [
        '/home/html/example.com',
        '/home/html/default',
        ]
    }
]
```

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
