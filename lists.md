## Lists

List - holds an ordered collection of items  
Tuple - holds an ordered collection of items and can't be changed after being initialized  
Set - holds an unordered and unindexed collection of items with no duplicate items

<br>

#### Create a list:
```python
# Create a list:
    listname = [item1, item2, itemN]
    listname = []

# Combine lists:
    combined_list = list1 + list2

# Copy a list:
    import copy
    new_list = copy.deepcopy(old_list)
```

<br>

#### Access items in a list:
```python
# Access an item in list:
    list[0]
    
# Negative index:
    # -1 is the last index of the list, -2 is 2nd last
    list[-1]

# Print all items in a list on seperate lines:
    for i in list:
        print(i)
```

<br>

#### Find:
```python
# Find number of items in a list:
    print(len(list_name))

# Find largest element in a list:
    print(max(list_name))
    
# Find smallest element in a list:
    print(min(list_name))
```

<br>

#### Advanced:
```python
# Sort a list from smallest to largest or alphabetically:
    # sorted(list_name) - Returns a new sorted list, it does not sort the list it is passed
    # list_name.sorted() - This method sorts the list it is called on, it returns None
    
# Remove duplicates from a list:
def remove_duplicates(source_list):
    new_list = []

    for i in source_list:
        if i not in new_list:
            new_list.append(i)

    return new_list

new = remove_duplicates(list)

# Operations with two lists
a = [1, 2, 3]
b = [4, 5, 6]
a_times_b = []

for i in range(0, len(a)):
	a_times_b.append(a[i] * b[i])
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


# Good example:
card_deck = [4, 11, 8, 5, 13, 2, 8, 10]
hand = []

while sum(hand) <= 17:
    hand.append(card_deck.pop())

print(hand)
```

### .index(x)
Searches for the specified value and returns the index of its first occurrence. Throws an error if it's not found.
```python
temp = arr.index(3)
print(temp)
# prints 2 (because it found the value 3 at index 2)
```

### .count(x)
Counts the number of occurrences of element (x).
```python
temp = arr.count(1)
print(temp)
# prints 1
```

<br>
<br>

## range(n)
(also in loops doc)  
Generates a list of numbers and is paired with a for loop  
Starts at 0 and will go n number of times
```python
for i in range(start, stop, step):
    #codeblock


# Example:
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
<br>

## Slices
Slice - a section (subset) of a list  
Gets the items in the specified range of the slice:
```python
list[start_index:end_index:step]
list[1:3]
list[:7]
list[3:]
```

<br>

Slices do not include the last index, so if list has 3 indices, and have:  
a	b	c	d  
0	1	2	3

list[:3] would print out a,b,c

<br>

Example:
```python
animals = ['bear', 'pig', 'cow', 'duck', 'horse']
some_animals = animals[1:3]
# prints pig, cow
```

<br>
