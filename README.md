% - Modulo Operator - Returns the remainder - 3%2=1; 4%2=0<br>
** - Exponent Operator<br>
Print number with specific decimals - {:.2f}

<br>

### OOP - Object Oriented Programming:
Everything in Python is an object. Every object has a type.<br>
'apple' is a string object type<br>
fruit = 'apple' - the variable fruit is a string object

<br>

### Jupyter Notebook:
Ctrl + Enter = Run cell<br>
Escape + a or b = Insert cell above or below

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
function
	parameter is subsection of functions

def function(parameters):
parameters are variables that can be used inside of the function
to assign the variable call the function with the variable value inside the ()
def sayhello(name):
	print('Hi ' + name)
sayhello('Seth')


Nesting Functions:
print(len('apple')) - the len function is nested in the print function


### Parameters:
Parameter - variables used inside of functions

function_name(parameter)

def function_name(parameter):
	print(parameter)
function_name(value for parameter)

Example 1:
```python

def say_hi(name):
	print('Hi {}!'.format(name))

say_hi('Jason')  # <-- Executing the function with the value 'Jason'
say_hi('everybody') # <-- Executing the function with the value 'everybody'
```
```python
Hi Jason!
Hi everybody!
```

#will output Hi Jason! then Hi everybody!

You can also declare parameters in functions. This will make an input optional:
Example 2: (declaring a parameter in the function)
def say_hi(name = 'there'):
	print('Hi {}!'.format(name))

say_hi()
say_hi('Jason')

#will output Hi there! then Hi Jason!

Functions can return data using the return statement.
Once the return statement is called no further code is executed.

Example:
def odd_or_even(number):
	"""Determine if a number is odd or even."""
	if number % 2 == 0:
		return 'Even'
	else:
		return 'Odd'

odd_or_even_string = odd_or_even(7)
print(odd_or_even_string)

Docstring:
def print():
	'''Prints string'''
	Code
