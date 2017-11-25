## Jupyter Notebook
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

## OOP - Object Oriented Programming:
Everything in Python is an object. Every object has a type.<br>
'apple' is a string object type<br>
fruit = 'apple' - the variable fruit is a string object

<br>

## Compound Conditional: (Two end conditions)
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

## Functions and Parameters:
You should be making a # docstring for all your functions.

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

## Lists
Holds ordered collection of items, various data types<br>
The index of the first item in a list is 0.<br>
DONT MAKE SPACES AFTER COMMAS IN LISTS<br>
count_list = [1,2,3,a,5,6,7,8,b,10]

<br>

Beginner:
```python
# Create a list:
    listname = [item1, item2, itemN]
    listname = []
    
# Access item in list:
    list[0]
    
# Negative index:
    # Last index of the list, -2 is 2nd last
    list[-1]

# Combine lists:
    combined_list = list1 + list2

# Print all items in list on seperate line:
    for i in list:
        print(i)
```

<br>

Advanced:
```python
# Copy a list:
    new_list = list(old_list)

# Find number of items in a list:
    print(len(list_name))

# Find largest element in a list:
    print(max(list_name))
    
# Find smallest element in a list:
    print(min(list_name))
    
# Sort a list from smallest to largest and/or alphabetically:
    # This does not change the order of the list it just prints it
    print(sorted(list))
    
    # Create a new list that is sorted
    new_list = list(old_list)
    sorted_list = sorted(new_list)
    
# Remove duplicates from a list:
def remove_duplicates(source_list):
    new_list = []

    for i in source_list:
        if i not in new_list:
            new_list.append(i)

    return new_list

new = remove_duplicates(list)
```

<br>

## List Methods

### .append(x)
Adds a single element (x) to the end of a list.
```python
arr.append(9)   
print(arr) 
# prints [1, 2, 3, 9]
```

### .extend(list)
Merges another undefined list (list) or a defined list to the end.
```python
# Undefined list
arr.extend([10,11])
# Defined list
arr.extend(listName)

print(arr) 
# prints [1, 2, 3, 9, 10, 11]
```

### .insert(index,x)
Inserts element (x) at (index).
```python
arr.insert(3,7)
print(arr) 
# prints [1, 2, 3, 7, 9, 10, 11]
```

### .remove(x)
Removes the first occurrence of element (x).
```python
arr.remove(10)  
print(arr) 
# prints [1, 2, 3, 7, 9, 11]
```

### .pop(i)
Removes the element at index (i). If no argument is passed, the last element of the list is removed.
```python
temp = arr.pop()
print(temp)
# prints 11
```

### .index(x)
Returns the first index of a value in the list. Throws an error if it's not found.
```python
temp = arr.index(3)
print(temp)
# prints 2
```

### .count(x)
Counts the number of occurrences of element (x).
```python
temp = arr.count(1)
print(temp)
# prints 1
```

<br>

## Slices
```python
Slice - a section (subset) of a list
will get the items in the specified range of the slice
The start index will be included while the end index is not.
list[start:end:step]
list[1:3]
list[:7]
list[3:]

Does not include the last index, so if list has 3 indexs, and you say
a	b	c	d
0	1	2	3
list[:3] - it will print out a,b,c
list[index1:index2]
list[:index2]
list[index1:]

Example:
	animals = ['bear', 'pig', 'cow', 'duck', 'horse']
	some_animals = animals[1:3]
	Important, does not include last index when slicing, only 1 and 2 are in new list ^
```
