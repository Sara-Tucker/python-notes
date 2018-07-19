# Templates
Templates generate HTML dynamically. A template contains the static parts of the desired HTML output as well as some special syntax describing how dynamic content will be inserted.

Django defines a standard API for loading and rendering templates regardless of the backend. Loading consists of finding the template for a given identifier and preprocessing it, usually compiling it to an in-memory representation. Rendering means interpolating the template with context data and returning the resulting string.

A Django template is simply a text document or a Python string marked-up using the Django template language. Some constructs are recognized and interpreted by the template engine. The main ones are variables and tags.

A template is rendered with a context. Rendering replaces variables with their values, which are looked up in the context, and executes tags. Everything else is output as is.

The syntax of the Django template language involves three constructs: variables, tags, and filters.

<br>

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

#### Variables
A variable outputs a value from the context, which is a dict-like object mapping keys to values.

Variables are surrounded by {{ and }} like this:
```
My first name is {{ first_name }}. My last name is {{ last_name }}.
```
With a context of {'first_name': 'John', 'last_name': 'Doe'}, this template renders to:
```
My first name is John. My last name is Doe.
```
Dictionary lookup, attribute lookup and list-index lookups are implemented with a dot notation:
```
{{ my_dict.key }}
{{ my_object.attribute }}
{{ my_list.0 }}
```
If a variable resolves to a callable, the template system will call it with no arguments and use its result instead of the callable.

<br>

#### Tags
Tags provide arbitrary logic in the rendering process.

This definition is deliberately vague. For example, a tag can output content, serve as a control structure e.g. an “if” statement or a “for” loop, grab content from a database, or even enable access to other template tags.

Tags are surrounded by {% and %} like this:
```
{% csrf_token %}
```
Most tags accept arguments:
```
{% cycle 'odd' 'even' %}
```
Some tags require beginning and ending tags:
```
{% if user.is_authenticated %}Hello, {{ user.username }}.{% endif %}
```
```
https://docs.djangoproject.com/en/2.0/ref/templates/builtins/#ref-templates-builtins-tags
https://docs.djangoproject.com/en/2.0/howto/custom-template-tags/#howto-writing-custom-template-tags
```

<br>

#### Filters
Filters transform the values of variables and tag arguments.

They look like this:
```
{{ django|title }}
```
With a context of {'django': 'the web framework for perfectionists with deadlines'}, this template renders to:
```
The Web Framework For Perfectionists With Deadlines
```
Some filters take an argument:
```
{{ my_date|date:"Y-m-d" }}
```
```
https://docs.djangoproject.com/en/2.0/ref/templates/builtins/#ref-templates-builtins-filters
https://docs.djangoproject.com/en/2.0/howto/custom-template-tags/#howto-writing-custom-template-filters
```
