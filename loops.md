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

#### Range
range(n) - generates a list of numbers and is paired with a for loop<br>
Starts at 0 and will go n number of times
```python
for i in range(start, stop, step):
    #codeblock


#Example:
for i in range(3):
    print(number)
# starts at 0, goes 3 times
# prints 0, 1, 2

for i in range(1,3):
    print(number)
# prints 1, 2

for i in range(1,10,2):
    print(number)
# prints 1, 3, 5, 7, 9
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
    count++


finished = false
while finished == false:
    if condition:
        finished = true
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

## Use Break statements!!
