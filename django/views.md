# Views
A view function is a function that is passed a Web request and returns a Web response. This response can be the HTML contents of a Web page, a 404 error, an XML document, an image, or anything really. The view itself contains whatever arbitrary logic is necessary to return that response. The convention is to put views in a views.py file.

Views encapsulate the logic responsible for processing a user’s request and return the response.

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

