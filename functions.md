# Functions

You should be making a # docstring for all your functions.

Example using integer division and .format method with return in function:
```python
def readable_timedelta(days):
    #to get the number of weeks we use integer division
    weeks = days // 7
    remainder = days % 7
    return "{} week(s) and {} day(s)".format(weeks, remainder)
```

<br>

### Parameter and Argument
Parameter - A variable in the declaration of a function.  
Argument - The value of the variable that gets passed to the function.
```
def function_name(parameter):
    #code
function_name(argument)
```

<br>

### Good example of returning values with functions:
```python
def cylinder_volume(height, radius):
    pi = 3.14159
    return height * pi * radius ** 2
```

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
