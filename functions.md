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

<br>
<br>
<br>

### Jupyter:
D + D = Delete cell  
Ctrl + Enter = Run cell  
Escape + a or b = Insert cell above or below  
Cell -> all outputs -> toggle scrolling  
View -> Toggle header and toolbar on new projects

<br>

### Print float with n decimal places:
```python
print('{:.nf}'.format(variable))
```

<br>

### Web scraping:
https://www.datacamp.com/community/tutorials/web-scraping-python-nlp<br>
https://www.udacity.com/course/introduction-to-python--ud1110

<br>

### Classes:
https://www.datacamp.com/community/tutorials/functions-python-tutorial

<br>
<br>
<br>

## Files:
### Automatically open and close a file:
```python
with open('file_path') as file_variable_name:
    #code


with open('/etc/hosts') as hosts:
    print(hosts.read())
    
    #Print every line on new line:
    for line in file_name:
        print(line)
    
    #Remove any whitespace or \n from lines:
    for line in file_name:
        print(line.rstrip())
```

<br>

### open('file_path', 'mode')
Opens a file and returns a file object.
```python
#Absolute path
open('D:/zPython/currentfolder/subfolder/file.type')

#Relative path
open('file.type')
open('currentfolder/subfolder/file.type')
```
```
File modes:
Default (r) - Open for reading
a - Open for writing and append to the end of the file
w - Open for writing and clear all existing data
x - Create a new file and open it for writing
r+ - Open for reading and appending

b - Binary file (image, video, compressed file)
Append b to one of the modes above.
Example:
open('/pics/cat.jpg', 'rb')
```

<br>

### .read()
Returns a single string containing the content of the file.
```python
hosts = open('hosts.txt')
print(hosts.read())
```

<br>

### .readlines()
Returns a list of strings, every string is a new line in the file.
```python
file_content = file.readlines()
```

<br>

### .close()
Closes a file.

<br>

### .write('string')
Writes to a file. If the file already exists, the argument is appended to the file.
```python
file_name.write('string goes here.\n')
```

<br>
<br>
<br>

## datetime and time:
```python
# Get current time and set a time
import datetime

# libr     static class
# datetime.datetime.method()

now = datetime.datetime.now()
freeTimeStart = now.replace(hour = 19, minute = 45)


# Delay execution for n seconds. (seconds can be an int or float)
import time
time.sleep(seconds)
```

<br>
<br>
<br>

## Check user input strings for mispelling:
```python
from difflib import get_close_matches

listName = get_close_matches(input, possibilities, n=3, cutoff=0.6)
```

<br>

Returns a list of the best “good enough” matches. Possibilities is a list of (typically) strings to check for.

Optional argument n (default 3) is the maximum number of close matches to return.

Optional argument cutoff (default 0.6) is a float that cuts off possibilities. Results that are 1 = Extremely similar, so a cutoff of .9 would be very strict.
