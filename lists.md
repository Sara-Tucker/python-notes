## Lists
Holds ordered collection of items, various data types  
The index of the first item in a list is 0.  

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
    import copy
    new_list = copy.deepcopy(old_list)

# Find number of items in a list:
    print(len(list_name))

# Find largest element in a list:
    print(max(list_name))
    
# Find smallest element in a list:
    print(min(list_name))
    
# Sort a list from smallest to largest and/or alphabetically:
    # sorted(list) - Returns a new sorted list
    print(sorted(list)) #This does not change the order of the list it just prints it
    
    # list.sorted()
    # This method sorts the list it is called on, it returns None
    
# Remove duplicates from a list:
def remove_duplicates(source_list):
    new_list = []

    for i in source_list:
        if i not in new_list:
            new_list.append(i)

    return new_list

new = remove_duplicates(list)

#Operations with two lists
a = [1, 2, 3]
b = [4, 5, 6]
atimesb = []

for i in range(0, len(a)):
	atimesb.append(a[i] * b[i])
#prints 4, 10, 18
```

<br>

List Comprehensions:  
Create new lists where each item is the result of some operation applied to each member of another list
```python
a = [1, 2, 3]
doubled_a = [i * 2 for i in a]
#prints 2, 4, 6

# Take a list where elements are a fucked up float decimal and
# change to 2 decimals while still remaining a float type
list_name = [float('%.2f' % i) for i in list_name]
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

Good example:
```python
card_deck = [4, 11, 8, 5, 13, 2, 8, 10]
hand = []

while sum(hand) <= 17:
    hand.append(card_deck.pop())

print(hand)
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
Slice - a section (subset) of a list<br>
Will get the items in the specified range of the slice:
```python
list[start:end:step]
list[1:3]
list[:7]
list[3:]
```

<br>

Slices do not include the last index, so if list has 3 indices, and have:<br>
a	b	c	d<br>
0	1	2	3

list[:3] - Would print out a,b,c

Example:
```python
	animals = ['bear', 'pig', 'cow', 'duck', 'horse']
	some_animals = animals[1:3]
	# prints pig, cow
```

<br>

### Range (also in loops doc)
range(n) - generates a list of numbers and is paired with a for loop<br>
Starts at 0 and will go n number of times

```python
for i in range(start, stop, step):
    #codeblock
```

<br>

Example:
```python
for i in range(3):
    print(i)
# starts at 0, goes 3 times
# prints 0, 1, 2

for i in range(1,3):
    print(i)
# prints 1, 2

for i in range(1,10,2):
    print(i)
# prints 1, 3, 5, 7, 9
```

<br>
