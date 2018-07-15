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

#### Request and response objects
Requests and responses go through middleware. Think of middleware as your house window, where requests go out and responses come in, both of them going through the window.
```python
def home_view(request):
    return HttpResponse('Hello world')
    
def home_view(request):
    response = HttpResponse()
    
    response.write('<p>Web page text.</p>')
    # use other methods here to customize the response
    
    return response
```
