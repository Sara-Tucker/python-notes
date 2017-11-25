## Loops
for loop - Use when you know when to stop looping. That's because you know it will loop until every item has been iterated over.<br>
while loop - Use when you don't know how many times you'll need to loop or when to stop looping.

### for loop
Used to perform an action on every item in a list<br>
```python
for item_variable in list_name:
    #codeblock
```

<br>

Example:
```python
animals = ['man', 'bear', 'pig']
for i in animals:
    print(animal.upper())
```

<br>

### Range
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

### while loop
If the condition is true the code will execute until it is false.

How to make:<br>
The while condition should be made with: ==  or  >  or  < <br>
The condition should be defined outside of the loop.<br>
The code block will alter a variable that is part of the condition.<br>
Eventually the condition will evaluate to false.

```python
defined condition

while condition is true:
    #codeblock
```

<br>

Example:
```python
count = 0
while count < 5:
    print count
    count += 1
```

Using Loops Correctly:
List with one end condition:

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


break - ends a loop
Example:
this code is actually incorrect cuz if it doesnt calculate the added weight
```python
manifest = [["bananas", 15], ["mattresses", 34], ["dog kennels",42], ["machine that goes ping!", 120], ["tea chests", 10], ["cheeses", 0]]

cargo_weight = 0
cargo_hold = []

for cargo in manifest:
    if cargo_weight >= 100:
        break
    else:
        cargo_hold.append(cargo[0])
        cargo_weight += cargo[1]


# pop method. removes an item from a list and returns the items value
card_deck = [4, 11, 8, 5, 13, 2, 8, 10]
hand = []

while sum(hand) <= 17:
    hand.append(card_deck.pop())

print(hand)
```
