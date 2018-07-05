# Dictionary / Hash / Hash Table:
Holds a collection of key-value pairs called pairs.  
It is unordered, values are accessed by keys and that's all.

<br>

### Create a dictionary:
```python
dictName = {key1:value1, key2:value2, keyN:valueN}


# Create a dictionary from lists:
keysList = ['a', 'b', 'c']
valuesList = [1, 2, 3]
dictName = dict(zip(keysList, valuesList))

print(dictName) # prints {'a': 1, 'b': 2, 'c': 3}
```

<br>

### Access a value using its key:
```python
# value == dictName[key]
dictName[key]
```

<br>

### Adding, changing, or deleting pairs:
```python
# Add a pair (changes it if the key already exists)
dictName[key] = value

# Delete a pair
del dictName[key]
```

<br>

### Check if a key or value is in a dictionary:
```python
# prints true or false
print(key in dictName.keys())
print(value in dictName.values())
```

<br>

### Loop through a dictionary:
All items will be processed in a random order.
```python
# Pairs (actually use the words key and value instead of i)
for key, value in dictName.items():
    print(f'The value for {key} is {value}.')

# Only keys
for key in dictName.keys():
    print(f'Key: {key}')

# Only values
for value in dictName.values():
    print(f'Value: {value}')
```

<br>

Advanced dictionary stuff:  
https://www.datacamp.com/community/tutorials/python-dictionary-tutorial
