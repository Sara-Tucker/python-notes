# Dictionary / Hash / Hash Table:
Holds key-value pairs. (called an item or pair)

<br>

#### Create a dictionary:
```python
dictionaryName = {key1:value1, key2:value2, keyN:valueN}
```

<br>

#### Create a dictionary from lists:
```python
keysList = ['a', 'b', 'c']
valuesList = [1, 2, 3]
dictionaryName = dict(zip(keysList, valuesList))

print(dictionary)
# prints {'a': 1, 'b': 2, 'c': 3}
```

<br>

#### Access a value using its key:
```python
dictionaryName[key]
# outputs the value for that key
```

<br>

#### Delete a pair:
```python
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
