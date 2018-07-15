# HttpRequest and HttpResponse objects

Django uses request and response objects to pass state through the system.

1. User requests a URL
2. Django creates a HttpRequest object that contains metadata about their request
3. Django searches then finds the appropriate view and passes the HttpRequest as the 1st arguement to the view function
4. The view will return a HttpResponse object (all views must return one)


Requests and responses go through middleware. Think of middleware as your house window, user's where requests come in and responses go out, both of them going through the window.
```python
def home_view(request):
    return HttpResponse('Hello world')
    
def home_view(request):
    response = HttpResponse()
    
    response.write('<p>Web page text.</p>')
    # use other methods here to customize the response
    
    return response
```
## HttpRequest


## HttpResponse
In contrast to HttpRequest objects, which are created automatically by Django, HttpResponse objects are your responsibility. Each view you write is responsible for instantiating, populating, and returning an HttpResponse.

<br>

#### Passing strings
```python
from django.http import HttpResponse
response = HttpResponse("Here's the text of the Web page.")
response = HttpResponse("Text only, please.", content_type="text/plain")

# If you want to add content incrementally, you can use response as a file-like object:
response = HttpResponse()
response.write("<p>Here's the text of the Web page.</p>")
response.write("<p>Here's another paragraph.</p>")
```

<br>

#### Setting header fields
To set or remove a header field in your response, treat it like a dictionary:
```python
response = HttpResponse()
response['Age'] = 120
del response['Age']
# Note that unlike a dictionary, del doesn’t raise KeyError if the header field doesn’t exist.
```

<br>

#### Treat the response as a file attachment
To treat the response as a file attachment, use the content_type argument and set the Content-Disposition header. For example, this is how you might return a Microsoft Excel spreadsheet:
```python
response = HttpResponse(my_data, content_type='application/vnd.ms-excel')
response['Content-Disposition'] = 'attachment; filename="foo.xls"'
```

<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>


### Fields (attributes):
**HttpRequest.path**  
A string representing the full path to the requested page, not including the scheme or domain.  
Example: "/music/bands/the_beatles/"

**HttpRequest.COOKIES**  
A dictionary containing all cookies. Keys and values are strings.
    
**HttpRequest.META**  
A dictionary containing all available HTTP headers. Available headers depend on the client and server.

<br>

### Fields (attributes) set by middleware:
**HttpRequest.session**  
From the SessionMiddleware: A readable and writable, dictionary-like object that represents the current session.

**HttpRequest.site**  
From the CurrentSiteMiddleware: An instance of Site or RequestSite as returned by get_current_site() representing the current site.

**HttpRequest.user**  
From the AuthenticationMiddleware: An instance of AUTH_USER_MODEL representing the currently logged-in user. If the user isn’t currently logged in, user will be set to an instance of AnonymousUser. You can tell them apart with is_authenticated, like so:
```python
    if request.user.is_authenticated:
        # Do something for logged-in users.
    else:
        # Do something for anonymous users.
```

<br>

### Methods:
**HttpRequest.get_host()**  
Returns the originating host of the request using information from the HTTP_X_FORWARDED_HOST (if USE_X_FORWARDED_HOST is enabled) and HTTP_HOST headers, in that order. If they don’t provide a value, the method uses a combination of SERVER_NAME and SERVER_PORT. Example: "127.0.0.1:8000"

