# Python Notes

**Methods:**  
```c#
Method Signature = Name of the method, the number of parameters, and the type of parameters


Method Overloading:
Having a method with the same name but different signatures.

public void Move(int x, int y) {}
public void Move(Point newLocation) {}
public void Move(Point newLocation, int speed) {}


Params modifier:
public class Calculator
{
    public int Add(int[] numbers)
    {
    }
}
var result = calculator.Add(new int[]{ 1, 2, 3, 4});

public class Calculator
{
    public int Add(params int[] numbers)
    {
    }
}
var result = calculator.Add(1, 2, 3, 4);


Ref and Out modifier are bad to use



readonly int a;



OOP:
- Encapsulation (information hiding)
    - Define fields as private
	- Provide public getter/setter methods
- Inheritance
- Polymorphism



if (!String.IsNullOrEmpty(stringName))
    //
	

private fields should be:
private int _camelCase;
```

<br>
<br>

**Debugging:**  
Set breakpoints and watch variable values with: Debug -> Windows -> Autos/Locales

<br>
<br>

**Keep the console window open:**  
```c#
input('Press <enter> to exit. ')
```

<br>
<br>

**Random:**  
```python
import random
num = random.randint(1, 5) #between 1-5 (correct)
```

<br>
<br>

**Conditional Operator:** - Returns one of two values depending on the value of a Boolean expression.
```python
# The condition evaluates to true or false.
[on_true] if [expression] else [on_false]

pos_or_neg = 'positive' if user_input > 0 else 'negative'
```

<br>
<br>

**enum** - An enum/enumeration is a set of named integer constants.
```python
from enum import Enum

class ShippingMethod(Enum):
    Regular = 1
    Priority = 2
    Express = 3


foo = ShippingMethod.Express
print(foo) #3

foo = 3
print(ShippingMethod(foo)) #Express
```

<br>
<br>

**Access modifier** - The accessibility of a member or type.
```
Everything is public by default.

Public - visible/accessible anywhere  
Private - only visible/accessible in the entire block where it's defined

self._color = color    # protected variable
self.__content = None  # private variable
```

<br>
<br>

---

<br>
<br>

### Class:
A template for creating objects that provides initial fields and methods for an object.

Field - A variable that is declared directly in a class.  
Member - Things that a class contains: Fields, Properties, Constructors, Methods.  
Namespace - A container for classes. "using Namespace;"

Hierarchy of a class:
```
1. Fields (available everywhere in the class)  
2. Constructor  
3. Methods
```

Declaring a class:
```c#
modifier class ClassName
{
    // Members
}
```
```c#
public class Person
{
    // Fields

    public Person()
    {
    }

    // Methods
}
```

<br>

### Constructor:
A method that is called when an object (instance of a class) is created. We use constructors to intialize fields in an object. Constructor methods have the same name as the class.
```c#
// Create a constructor of the current class:
// ctor + Tab


public class Person
{
    string first;
    string last;
    
    public Person(string firstName, string lastName)
    {
        first = firstName;
        last = lastName;
    }
}
```

<br>

### Object:
A particular instance of a class.

Create an object / Instantiate a class:
```c#
var objectName = new ClassName(arguments);
```

<br>

### Example:
```
Person:
    Fields:
        Name
        Age
        Height
    Methods:
        Walk()
        Run()
        Talk(string input)


Objects:
    var john = new Person();
    var mary = new Person();


Setting a field and calling a method:
    john.Name = "John";
    mary.Talk($"Hello {john.Name}!");
```

<br>

### Static modifier:
**Static classes:**  
To use a non-static class you need to create an object of the class. A static class cannot be instantiated, in other words, you cannot use the new keyword to create a variable of the class type. Because they are not instantiatable, you access the members of a static class by using the class name itself. Static classes are used to hold shared variables and methods. Since there will be only one instance of it everything will use that one shared set of variables and methods.

**Static members:**  
You can't access static members from objects. When an object is made anything static is removed from the object so it does not get any of the static things. Static members exist only in the class and are accessed the same way as from a static class.

Example of a static member in a non-static class:
```c#
public class Calculator
{
    public static int Add(int a, int b)
    {
        return a + b;
    }
}

int answer = Calculator.Add(1, 2);

// Since the add method in the calculator class is static
// that means you don't need to create an object to use that method.
```

<br>

### Inheritance:
A relationship between two classes that allows one to inherit code from another. A child class can inherit the existing members from a base class, then the child class can add any members to itself that are specific to the child class.
```c#
modifier class ChildClassName : BaseClassName {}
```

<br>

### Abstract and Override modifiers:
The abstract modifier enables you to create classes and class members that are incomplete and must be implemented in a derived class. Use the abstract modifier in a class declaration to indicate that a class is intended only to be a base class of other classes. An abstract class cannot be instantiated. Members marked as abstract, or included in an abstract class, must be implemented by classes that derive from the abstract class.

Abstract classes may also define abstract methods by adding the keyword abstract before the return type of the method. Abstract methods have no implementation, so the method definition is followed by a semicolon instead of a normal method block. Derived classes of the abstract class must implement all abstract methods.
```c#
public abstract class Animal
{
    public abstract void Speak();
    // Since abstract methods have no implementation there is no curly bracket block.
}

public class Cat : Animal
{     
    public abstract void Speak()
    {
        Console.WriteLine("Meow");
    }
}

public class Dog : Animal
{     
    public abstract void Speak()
    {
        Console.WriteLine("Bark");
    }
}
```

<br>
<br>

### Struct:
1. Within a struct declaration, fields cannot be initialized unless they are declared as const or static.  
2. A struct cannot declare a default constructor (a constructor without parameters).  
3. The struct type is suitable for representing lightweight objects such as Point, Rectangle, and Color.

```c#
public struct Point
{
    public int x, y;

    public Point(int xParam, int yParam)
    {
        x = xParam;
        y = yParam;
    }
}
```
https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method

<br>
<br>

---

<br>
<br>

### Properties:
Explained:
```c#
using System;
public class PlayerInput
{
    private float horizontalData;
    private float verticalData;
    // We don't want other classes changing this data so it is private.
    // However, another class needs to read the data from these variables.
    // But since they are private they are only visable in this class.


    // We could write public methods that allow us to get or set these private variables:
    public float GetHorizontalData()
    {
        return horizontalData;
    }

    public void SetHorizontalData(float hData)
    {
        horizontalData = hData;
    }
}


// And then call them from another class:
public class IDK
{
    float hInput;

    public void Main()
    {
        PlayerInput PIObject = new PlayerInput();
	
	hInput = PIObject.horizontalData;
	// Error: PIObject.horizontalData is private and not accessable outside of PIObject.
        // You cannot get the private data.
	
	PIObject.horizontalData = 3.22f;
	// Error: PIObject.horizontalData is private and not accessable outside of PIObject.
        // You cannot set the private data.

        // Using the public methods to access the private data:
        hInput = PIObject.GetHorizontalData();
        PIObject.SetHorizontalData(3.22f);
	
        Console.WriteLine(hInput);
        Console.WriteLine(PIObject.GetHorizontalData());
    }
}

// But instead you could do it in a much easier way using properties.
```

<br>

Property - A class member that provides access to fields of a class.  
A get property accessor is used to return the value, and a set property accessor is used to assign a new value.

<br>

Example:
```c#
// Create a property:
// propfull + Tab
// prop + Tab


//Get input data
float m_h;
public float H { get { return m_h; } } //Read only
float m_v;
public float V { get { return m_v; } } //Read only 

bool m_inputEnabled = false;
public bool InputEnabled { get { return m_inputEnabled; } set { m_inputEnabled = value; } }


public void GetInputKey()
{
    if (m_inputEnabled)
    {
        m_h = Input.GetAxisRaw("Horizontal");
        m_v = Input.GetAxisRaw("Vertical");
    }
}



// And then from another class:
void Update ()
{
    if (playerMover.isMoving)
    {
        return;
    }

    playerInput.GetInputKey();

    if (playerInput.V == 0)
    {
        if (playerInput.H < 0)
        {
            playerMover.MoveLeft();
        }
        else if (playerInput.H > 0)
        {
            playerMover.MoveRight();
        }
    }
    else if (playerInput.H == 0)
    {
        if (playerInput.V < 0)
        {
            playerMover.MoveBackward();
        }
        else if (playerInput.V > 0)
        {
            playerMover.MoveForward();
        }
    }
}
```

<br>

Useful things you can do with properties but can't if the variables were just public:
```c#
public bool InputEnabled
{
    get { return inputEnabled; }
    set
    {
        inputEnabled = value;
        Debug.Log("Input changed to: " + inputEnabled);
        // Everytime the value is changed its value is printed to the console.
    }
}

public float Health
{
    get { return health; }
    set
    {
        health = value;
	Object.UpdateHPUI(health);
	// When hp is changed the property automatically updates the UI.
    }
}
```

<br>

Initialize an auto-implemented property:
```c#
public string FirstName { get; set; } = "Jane";
```

<br>
<br>

---

<br>
<br>

### Anonymous Function (lambda expression):
https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions

A function definition that is not bound to an identifier and contains only one executable statement.

Lambdas allow you to write quick throw away functions without naming them. They also provide a nice way to write closures.

Anonymous functions are often referred to as lambdas and often are introduced using the keyword lambda.

This anonymous function allows you to create functions from functions:
```python
def add(x):
    return lambda y: x + y
foo = add(5)
foo(1)


def add**(x)**:
    return lambda y: **x** + y
# The x variable in the lambda expression is referencing the parameter x, so x = x.

def add(x):
    return lambda **y**: x + y
# The lamdba requires the parameter y.

def add(x):
    **return lambda y: x + y**
# Add() returns a lambda.

foo = add(5)
# "foo = lambda y: 5 + y"

foo(1)
# "foo = lambda 1: 5 + 1"
>>> 6
```

<br>
<br>

Closure:  
https://stackoverflow.com/a/7464475/9020002  
https://stackoverflow.com/questions/4103750/closure-because-of-what-it-can-do-or-because-it-does  
https://www.google.com/search?q=programming+closure&ie=utf-8&oe=utf-8&client=firefox-b-1-ab

<br>
<br>

---

<br>
<br>

### Attributes:
A declarative tag that is used to convey information to runtime about the behaviors of various elements like classes, methods, structures, enumerators, etc. in your program.

Attributes add metadata to your program. Metadata is information about the types defined in a program.
```c#
// Declaring an attribute:
[attribute(positional_parameters, name_parameter = value, ...)] element;

[HideInInspector] public RoomNavigation roomNavigation;
```

<br>
<br>

---

<br>
<br>

### DateTime:
```c#
using System;

// Create a DateTime:
var dateTime = new DataTime(2015, 1, 1);

// Get current date:
var now = DateTime.Now;
var today = DateTime.Today;

// Access units of DateTime:
Console.WriteLine(now.Hour);
Console.WriteLine(now.Minute);

// Add or subtract units to DateTime:
var tomorrow = now.AddDays(1);
var yesterday = now.AddDays(-1);

// Print DateTimes:
Console.WriteLine(now.ToLongDateString);
Console.WriteLine(now.ToShortDateString);
Console.WriteLine(now.ToLongTimeString);
Console.WriteLine(now.ToShortTimeString);

Console.WriteLine(now.ToString("")); //inside "" shows all the options for printing.
```

<br>

### TimeSpan:
A length of time.
```c#
// Create TimeSpan objects
TimeSpan timeSpan1 = new TimeSpan(1, 2, 3);

TimeSpan timeSpan2 = TimeSpan.From[[AllOtherMethodsHere]]Hours(1); // Same as ^ 1, 0, 0

DateTime start = DateTime.Now;
DateTime end = DateTime.Now.AddMinutes(2);
TimeSpan duration = end - start;


// Access info of TimeSpans with their Properties
Console.WriteLine("Minutes: " + timeSpan1.Minutes);
Console.WriteLine("Total minutes: " + timeSpan1.TotalMinutes);
```



### Jupyter:
D + D = Delete cell  
Ctrl + Enter = Run cell  
Escape + a or b = Insert cell above or below  
Cell -> all outputs -> toggle scrolling  
View -> Toggle header and toolbar on new projects

<br>

### Print float with n decimal places:
```python
print('{:.nf}'.format(variable))
```

<br>
<br>

## datetime and time:
```python
# Get current time and set a time
import datetime

# libr     static class
# datetime.datetime.method()

now = datetime.datetime.now()
freeTimeStart = now.replace(hour = 19, minute = 45)


# Delay execution for n seconds. (seconds can be an int or float)
import time
time.sleep(seconds)
```

<br>
<br>
<br>

## Check user input strings for mispelling:
```python
from difflib import get_close_matches

listName = get_close_matches(input, possibilities, n=3, cutoff=0.6)
```

<br>

Returns a list of the best “good enough” matches. Possibilities is a list of (typically) strings to check for.

Optional argument n (default 3) is the maximum number of close matches to return.

Optional argument cutoff (default 0.6) is a float that cuts off possibilities. Results that are 1 = Extremely similar, so a cutoff of .9 would be very strict.

<br>
<br>
<br>

## GUI:

Correct way to code tkinter:  
http://python-textbok.readthedocs.io/en/latest/Introduction_to_GUI_Programming.html  
http://www.tutorialspoint.com/python/python_gui_programming.htm  
https://dzone.com/articles/python-gui-examples-tkinter-tutorial-like-geeks

<br>

Templates:  
https://github.com/jesusfbes/SimpleGUI/tree/master/src  
https://gist.github.com/ajfigueroa/c2af555630d1db3efb5178ece728b017  
https://github.com/brysontyrrell/MacAdmins-2016-Craft-GUIs-with-Python-and-Tkinter  
https://www.raspberrypi.org/forums/viewtopic.php?t=105749

<br>

```python
from tkinter import *

#Start
window = Tk()

txtBox1Val = StringVar()

def convert_kg():
    gram=float(txtBox1Val.get())*1000
    pound=float(txtBox1Val.get())*2.20462
    ounce=float(txtBox1Val.get())*35.274
    txt1.delete("1.0", END)
    txt1.insert(END,gram)
    txt2.delete("1.0", END)
    txt2.insert(END,pound)
    txt3.delete("1.0", END)
    txt3.insert(END,ounce)


lbl1 = Label(window, text = 'Kg')
lbl1.grid(row = 0, column = 0)

txtBox1 = Entry(window, textvariable = txtBox1Val)
txtBox1.grid(row = 0, column = 1)

btn1 = Button(window, text = 'Convert', command = convert_kg)
btn1.grid(row = 0, column = 2)


txt1 = Text(window, height = 1, width = 20)
txt1.grid(row = 1, column = 0)

txt2 = Text(window, height = 1, width = 20)
txt2.grid(row = 1, column = 1)

txt3 = Text(window, height = 1, width = 20)
txt3.grid(row = 1, column = 2)


window.mainloop()
#End
```
