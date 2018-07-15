# HttpRequest and HttpResponse objects

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
