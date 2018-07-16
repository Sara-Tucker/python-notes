# Models
A model is the single and definitive source of information about your data. It contains the fields and behaviors of the data you’re storing. Generally each model maps to a single database table.

Models structure and manipulate the data of your Web application.

Models are essentially your database layout, with additional metadata.  

Best definition - models are database table templates

<br>

- Each model is a class that inherits from the django.db.models.Model class
- Each DatabaseField of the model represents a database column.

#### Creating models:
```python
from django.db import models

class Person(models.Model):
    first_name = models.CharField(max_length=30)
    last_name = models.CharField(max_length=30)
```
first_name and last_name are DatabaseFields of the model. Each DatabaseField maps to a database column.

The above Person model would create a database table like this:
```python
CREATE TABLE myapp_person (
    "id" serial NOT NULL PRIMARY KEY,
    "first_name" varchar(30) NOT NULL,
    "last_name" varchar(30) NOT NULL
);
```

<br>
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
<br>

#### DatabaseFields:
The most important part of a model – and the only required part of a model – is the list of DatabaseFields it defines. DatabaseFields are specified by attributes(fields) that are classes.

DatabaseFields are an abstract class (classes and class members that are incomplete and must be implemented in a derived class) that represents a database table column. Django uses DatabaseFields to create the database table to map Python types to the database.

In models, a DatabaseField is instantiated as a class and represents a particular table column. It has attributes(fields) such as null and unique, and methods that Django uses to map the attribute(field) value to database-specific values.
```python
class Question(models.Model):
    #dbfield_inst = models.---Field()
    question_text = models.CharField(max_length=200)
    pub_date = models.DateTimeField('date published')
    # a human readable can be given as an optional first position argument

class Choice(models.Model):
    question = models.ForeignKey(Question, on_delete=models.CASCADE)
    # a relationship is defined using ForeignKey
    # That tells Django each Choice is related to a single Question
    # Django supports many different database relationship types
    choice_text = models.CharField(max_length=200)
    votes = models.IntegerField(default=0)
```

<br>

DatabaseField class types:  
Each attribute(field) in your model should be an instance of the appropriate DatabaseField class. Django uses the various DatabaseField classes to determine:
- The column type, which tells the database what kind of data to store (e.g. INTEGER, VARCHAR, TEXT)
- The default HTML widget to use when rendering a form field (e.g. ```<input type="text">, <select>```)
- The minimal validation requirements, used in Django’s admin and in automatically-generated forms

<br>

### DatabaseField arguments:
Each DatabaseField takes a set of DatabaseField-specific arguments. For example, CharField (and its subclasses) require a max_length argument which specifies the size of the VARCHAR DatabaseField used to store the data.

There’s also a set of common optional arguments available to all DatabaseField types. Here’s the most often-used ones:
#### null
- If True, Django will store empty values as NULL in the database. Default is False.
    
#### blank
- If True, the field is allowed to be blank. Default is False.
- Note that this is different than null. null is purely database-related, whereas blank is validation-related. If a DatabaseField has blank=True, form validation will allow entry of an empty value. If a field has blank=False, the field will be required.
- Simplified: You can have only blank true, you can have blank and null true, but you can't have only null true because there's no way to give the DatabaseField an empty value if blank isn't true.
    
#### choices
- An iterable (collection) of tuples of two items ([(A, B), (A, B) ...]) to use as choices for this DatabaseField. The default form widget will be a select box with these choices instead of the standard text field.
- The first element in each tuple is the value to be assigned to the model's DatabaseField and stored in the database. The second element is displayed by the DatabaseField’s form widget.
- A choices list looks like this:
```python
YEAR_IN_SCHOOL_CHOICES = (
    ('FR', 'Freshman'),
    ('SO', 'Sophomore'),
    ('JR', 'Junior'),
    ('SR', 'Senior'),
)
```
- The display value for a DatabaseField with choices can be accessed using the model_inst.get_dbFieldVarName_display() method. For example:
```python
from django.db import models

class Person(models.Model):
    SHIRT_SIZES = (
        ('S', 'Small'),
        ('M', 'Medium'),
        ('L', 'Large'),
    )
    name = models.CharField(max_length=60)
    shirt_size = models.CharField(max_length=1, choices=SHIRT_SIZES)

>>> p = Person(name="Fred Flintstone", shirt_size="L")
>>> p.save()
>>> p.shirt_size
'L'
>>> p.get_shirt_size_display()
'Large'
```
- Generally, it’s best to define the choice's tuple inside a model class, and to define the choice's database values as static constant fields. Though you can define a choices list outside of a model class and then refer to it, defining the choices and names for each choice inside the model class keeps all of that information with the class that uses it, and makes the choices easy to reference (e.g, Student.SOPHOMORE will work anywhere that the Student model has been imported).
```python
from django.db import models

class Student(models.Model):
    FRESHMAN = 'FR'
    SOPHOMORE = 'SO'
    JUNIOR = 'JR'
    SENIOR = 'SR'
    YEAR_IN_SCHOOL_CHOICES = (
        (FRESHMAN, 'Freshman'),
        (SOPHOMORE, 'Sophomore'),
        (JUNIOR, 'Junior'),
        (SENIOR, 'Senior'),
    )
    year_in_school = models.CharField(
        max_length=2,
        choices=YEAR_IN_SCHOOL_CHOICES,
        default=FRESHMAN,
    )

    def is_upperclass(self):
        return self.year_in_school in (self.JUNIOR, self.SENIOR)
```

#### default
- The default value for the DatabaseField. This can be a value or a callable object. If callable it will be called every time a new object is created.

#### help_text
- Extra “help” text to be displayed with the form widget. It’s useful for documentation even if your DatabaseField isn’t used on a form.

#### primary_key
- If True, this field is the primary key for the model.
- If you don’t specify primary_key=True for any fields in your model, Django will automatically add an IntegerField to hold the primary key, so you don’t need to set primary_key=True on any of your fields unless you want to override the default primary-key behavior. For more, see Automatic primary key fields.
- The primary key field is read-only. If you change the value of the primary key on an existing object and then save it, a new object will be created alongside the old one. For example:
```python
from django.db import models

class Fruit(models.Model):
    name = models.CharField(max_length=100, primary_key=True)

>>> fruit = Fruit.objects.create(name='Apple')
>>> fruit.name = 'Pear'
>>> fruit.save()
>>> Fruit.objects.values_list('name', flat=True)
<QuerySet ['Apple', 'Pear']>
```

#### unique
- If True, this DatabaseField must be unique throughout the table.



An iterable (e.g., a list or tuple) (collection)
