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
    guess = raw_input("Please enter the password: ")
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
Nesting Functions:<br>
print(len('apple')) - the len function is nested in the print function

You should be making a # docstring for all your functions.

<br>

### Parameters:
Parameter - variables used inside of functions
```
def function_name(parameter):
	print(parameter)
function_name(value for parameter)
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

You can also declare parameters in functions. This will make an input optional.<br>
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
Example of returning a parameters value:
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
