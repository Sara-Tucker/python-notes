# Dictionary / Hash / Hash Table:
Holds a collection of key-value pairs called pairs.  
It is unordered, values are accessed by keys and that's all.

<br>

#### Create a dictionary:
```python
dictName = {key1:value1, key2:value2, keyN:valueN}


# Create a dictionary from lists:
keysList = ['a', 'b', 'c']
valuesList = [1, 2, 3]
dictName = dict(zip(keysList, valuesList))

print(dictName) # prints {'a': 1, 'b': 2, 'c': 3}
```

<br>

#### Access a value using its key:
```python
# value == dictName[key]
dictName[key]
```

<br>

#### Adding, changing, or deleting pairs:
```python
# Add a pair (changes it if the key already exists)
dictName[key] = value

# Delete a pair
del dictionaryName[key]
```

<br>

### Check if a key is in a dictionary: ???
```python
if key in dictionary.keys():
    print('dictionary[key])

# ????
print(value in dictionaryName.keys())
```

<br>

### Check if a value is in a dictionary: ???
```python
print(key in dictionaryName.values())
```

<br>

### Loop through dictionary:
All items will be processed but in random order.
```python
for key in dictionaryName:
	print('The value for {} is {}.'.format(key, dictionaryName[key]))
# actually use the word key instead of i
```

<br>

### Loop with two variables: (same as above)
```python
for key, value in dictionaryName.items():
	print('The value for {} is {}.'.format(key, value))
# actually use the words key and value instead of i
```

<br>

Advanced dictionary stuff, like web and idk- https://www.datacamp.com/community/tutorials/python-dictionary-tutorial
