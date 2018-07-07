## for loop
Executes a codeblock for each element in a collection. Used when you know when to stop looping because you know it will loop until every element has been iterated over.
```python
for element in list_name:
    #codeblock

names = ['alice', 'bob', 'charlie']
for name in names:
    print(name.title())
```

<br>

#### range()
Generates a tuple of numbers and is paired with a for loop.
```python
for i in range(stop):
# stop - number of integers to generate starting from zero

for i in range(start, stop, step):
# start - starting number of the sequence
# stop - generate numbers up to, but not including this number


#Example:
for i in range(3):
    print(i)
# 0, 1, 2

for i in range(1,3):
    print(i)
# 1, 2

for i in range(1,10,2):
    print(i)
# 1, 3, 5, 7, 9
```

<br>

## while loop
Repeats a codeblock until a condition evaluates to false.

- The while condition should be made with: ==  or  >  or  <  
- The condition should be defined outside of the loop.  
- The code block will alter a variable that is part of the condition.  
- Eventually the condition will evaluate to false.
```python
defined condition

while conditionistrue:
    #codeblock


count = 0
while count < 5:
    print(count)
    count += 1


finished = False
while not finished:
    if condition:
        finished = True
    else:
        #codeblock
```

<br>

## Example of using Loops - List with one end condition:
```python
list = []
finished = False

while finished == False:
    task = input('Enter a task for your to-do list. Press <enter> when done:\n')

    if len(task) == 0:
        finished = True
    else:
        list.append(task)
        print('Task added.')

print('Your To- Do List:')
for i in list:
    print(i)
```

<br>
<br>

## break statement:
The break statement terminates the entire loop.
```python
foo = 10

while foo > 0:
    print(foo)
    foo -= 1
    
    if foo == 5:
        break
```

<br>
<br>

## continue statement:
The continue statement passes control to the next iteration of the loop.
```python
for i in range(1, 11):
    if i < 9:
        continue
    print(i)

# 9
# 10
```
