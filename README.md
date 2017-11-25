### Jupyter Notebook
View -> Toggle header and toolbar on new projects<br>
Ctrl + Enter = Run cell<br>
Escape + a or b = Insert cell above or below<br>


% - Modulo Operator - Returns the remainder - 3%2=1; 4%2=0<br>
** - Exponent Operator<br>
Print number with specific decimals - {:.2f}

Using integer division and .format method with return in function:
```python
def readable_timedelta(days):
    #to get the number of weeks we use integer division
    weeks = days // 7
    remainder = days % 7
    return "{} week(s) and {} day(s)".format(weeks, remainder)
```

<br>

### OOP - Object Oriented Programming:
Everything in Python is an object. Every object has a type.<br>
'apple' is a string object type<br>
fruit = 'apple' - the variable fruit is a string object

<br>

### Compound Conditional: (Two end conditions)
```python
keepGoing = True
correct = "Python"
tries = 3

while keepGoing == True:
    guess = input("Please enter the password: ")
    tries = tries - 1
    
    if guess == correct:
        print "You may proceed"
        keepGoing = False
    else:
        print "That's not correct."

        if tries <= 0:
            print "Sorry. You only had three tries"
            keepGoing = False
        else:
            print "You have %d tries left" % tries
```

<br>

### Functions:
You should be making a # docstring for all your functions.

<br>

### Parameters:
Parameter - variables used inside of functions

Parameter is used when defining a function. Argument is the value you give for the parameter when calling a function.
```
def function_name(parameter):
    #code
function_name(argument)
```

<br>

Example of using a parameter:
```python

def say_hi(name):
    print('Hi {}!'.format(name))

say_hi('Jason')#  <-- Executing the function with the value 'Jason'
say_hi('everybody')#  <-- Executing the function with the value 'everybody'
```
```
Hi Jason!
Hi everybody!
```

<br>

You can also declare parameters in functions. This will make an input for a defined parameter optional.<br>
Example of declaring a parameter in the function:
```python
def say_hi(name = 'there'):
    print('Hi {}!'.format(name))

say_hi()
say_hi('Jason')
```
```
Hi there!
Hi Jason!
```

<br>

Functions can return data using the return statement. Once the return statement is called no further code is executed.<br>
Example of returning something with a function:
```python
def odd_or_even(number):
    #Determine if a number is odd or even
	
    if number % 2 == 0:
        return 'Even'
    else:
        return 'Odd'

print(odd_or_even(7))
```

<br>

Another example of returning values with functions:
```python
def cylinder_volume(height, radius):
    pi = 3.14159
    return height * pi * radius ** 2
    
>>> cylinder_volume(10, 3)
282.7431
```

<br>

### List
Holds ordered collection of items, various data types<br>
The index of the first item in a list is 0.<br>
DONT MAKE SPACES AFTER COMMAS IN LISTS<br>
count_list = [1,2,3,a,5,6,7,8,b,10]

<br>

```python
# Create a list:
    listname = [item1, item2, itemN]
    listname = []
    
# Access item in list:
    listname = [0]

# Print all items in list on seperate line:
    for i in list:
        print(i)
	
#
```

<br>
