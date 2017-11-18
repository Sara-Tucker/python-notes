% - Modulo Operator - Returns the remainder - 3%2=1; 4%2=0<br>
** - Exponent Operator<br>
Print number with specific decimals - {:.2f}
<br>

### OOP - Object Oriented Programming:
Everything in Python is an object. Every object has a type.<br>
'apple' is a string object type<br>
fruit = 'apple' - the variable fruit is a string object<br>

<br>

### Jupyter Notebook:
Ctrl + Enter = Run cell

Escape + a or b = Insert cell above or below


### Compound Conditional: (Two end conditions)
```python
keepGoing = True
correct = "Python"
tries = 3

while keepGoing == True:
    guess = raw_input("Please enter the password: ")
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
