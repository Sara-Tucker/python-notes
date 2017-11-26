## Dictionary / Hash / Hash Table:
Holds key-value pairs called items

Create a dictionary:
```python
dictionaryName = {key1:value1, key2:value2, keyN:valueN}
dictionaryName = {}
```

<br>

Access values by their keys:
```python
dictionaryName[key]
# outputs value for that key
```

<br>

Delete items:
```python
del dictionaryName[key]
```

<br>

Check if a key is in a dictionary:
```python
if key in dictionaryName.keys():
	print('dictionaryName[key])
```

<br>

Check if a value is in a dictionary:
```python
print(key in dictionaryName.values())
```

<br>

Loop through dictionary:
All items will be processed but in random order.
for key in dictionaryName:
	print('The value for {} is {}.'.format(key, dictionaryName[key]))
# actually use the word key instead of i

Loop with two variables: (same as above)
for key, value in dictionaryName.items():
	print('The value for {} is {}.'.format(key, value))
# actually use the words key and value instead of i

Create a dictionary from lists:
keysList = ['a', 'b', 'c']
valuesList = [1, 2, 3]
dictionaryName = dict(zip(keysList, valuesList))

print(dictionary)
# prints {'a': 1, 'b': 2, 'c': 3}
