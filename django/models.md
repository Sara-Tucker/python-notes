# Models
A model is the single and definitive source of information about your data. It contains the fields and behaviors of the data you’re storing. Generally each model maps to a single database table.  
Models are essentially your database layout, with additional metadata.

<br>

- Each model is a class that inherits from the django.db.models.Model class
- Each field of the model represents a database field

#### Creating models:
```python
from django.db import models

class Person(models.Model):
    first_name = models.CharField(max_length=30)
    last_name = models.CharField(max_length=30)
```
first_name and last_name are fields of the model. Each field maps to a database column.

The above Person model would create a database table like this:
```python
CREATE TABLE myapp_person (
    "id" serial NOT NULL PRIMARY KEY,
    "first_name" varchar(30) NOT NULL,
    "last_name" varchar(30) NOT NULL
);
```

<br>

#### Activate a model:
Once you have defined your models, you need to tell Django you’re going to use those models. Do this by editing your settings file and changing the INSTALLED_APPS setting to add the name of the module that contains your models.py.

For example, if the models for your application live in the module myapp.models (the package structure that is created for an application by the manage.py startapp script), INSTALLED_APPS should read, in part:
```python
INSTALLED_APPS = [
    'myapp',
]
```
Description #2:  
To include the app in our project, we need to add a reference to its configuration class in the INSTALLED_APPS setting. The PollsConfig class is in the polls/apps.py file, so its dotted path is 'polls.apps.PollsConfig'. Edit the mysite/settings.py file and add the dotted path to the INSTALLED_APPS setting. It’ll look like this:
```python
# in mysite/settings.py file

INSTALLED_APPS = [
    'polls.apps.PollsConfig',
]
```
When you add new apps to INSTALLED_APPS, be sure to run manage.py migrate, optionally making migrations for them first with manage.py makemigrations.

<br>

#### Fields (aka database Fields):



The most important part of a model – and the only required part of a model – is the list of database Fields it defines. Fields are specified by attributes(fields) that are classes.
```python
class Question(models.Model):
    #field_instance = models.XxxField()
    # fields are actually classes from Django
    
    question_text = models.CharField(max_length=200)
    pub_date = models.DateTimeField('date published')
    # a human readable can be given as an optional first position argument

class Choice(models.Model):
    question = models.ForeignKey(Question, on_delete=models.CASCADE)
    # a relationship is defined using ForeignKey
    # That tells Django each Choice is related to a single Question
    # Django supports all the common database relationships
    
    choice_text = models.CharField(max_length=200)
    votes = models.IntegerField(default=0)
```

Field is an abstract class (classes and class members that are incomplete and must be implemented in a derived class) that represents a database table column. Django uses Fields to create the database table to map Python types to the database.



In models, a Field is instantiated as a class and represents a particular table column. It has attributes(fields) such as null and unique, and methods that Django uses to map the attribute(field) value to database-specific values.


Field types¶

Each field in your model should be an instance of the appropriate Field class. Django uses the field class types to determine a few things:

    The column type, which tells the database what kind of data to store (e.g. INTEGER, VARCHAR, TEXT).
    The default HTML widget to use when rendering a form field (e.g. <input type="text">, <select>).
    The minimal validation requirements, used in Django’s admin and in automatically-generated forms.

Django ships with dozens of built-in field types; you can find the complete list in the model field reference. You can easily write your own fields if Django’s built-in ones don’t do the trick; see Writing custom model fields.
