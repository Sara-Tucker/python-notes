# HttpRequest and HttpResponse objects

Django uses request and response objects to pass state through the system.

1. User requests a URL
2. Django creates a HttpRequest object that contains metadata about their request
3. Django searches then finds the appropriate view and passes the HttpRequest as the 1st arguement to the view function
4. The view will return a HttpResponse object (all views must return one)


#### Create a Django project (environment):
```
$ django-admin startproject mysite
```

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
### Fields (attributes)
#### HttpRequest.path
- A string representing the full path to the requested page, not including the scheme or domain.
- Example: "/music/bands/the_beatles/"

#### HttpRequest.COOKIES
- A dictionary containing all cookies. Keys and values are strings.
    
#### HttpRequest.META
- A dictionary containing all available HTTP headers. Available headers depend on the client and server.

<br>

### Fields (attributes) set by middleware
#### HttpRequest.session
- From the SessionMiddleware: A readable and writable, dictionary-like object that represents the current session.

#### HttpRequest.site
- From the CurrentSiteMiddleware: An instance of Site or RequestSite as returned by get_current_site() representing the current site.

#### HttpRequest.user
- From the AuthenticationMiddleware: An instance of AUTH_USER_MODEL representing the currently logged-in user. If the user isn’t currently logged in, user will be set to an instance of AnonymousUser. You can tell them apart with is_authenticated, like so:
```python
    if request.user.is_authenticated:
        # Do something for logged-in users.
    else:
        # Do something for anonymous users.
```

<br>
