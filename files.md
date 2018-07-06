# Files

## Paths and directories
```
cwd - current working directory (abbreviation, not a keyword)  
./  - the cwd  
../ - the parent folder
```

<br>

#### Absolute and relative paths
```python
#Absolute path - full path name
path_name = 'D:/zPython/currentfolder/subfolder/file.type'

#Relative path - the program’s cwd is inferred as the start of the path
path_name = './file.type'
path_name = './subfolder/file.type'


# Store paths as variables to make reusing easier
file_path = './subfolder/file.type'

# idek:
from pathlib import Path
files_folder = Path('source_data/text_files/')
```

<br>

#### os module
```python
import os

# Return the cwd
os.getcwd()

# Change the cwd
os.chdir('path')

# Create a directory
os.makedirs('path')

# Return a list of all files and directories in a directory
os.listdir('path')

# Check if directory or file exists
os.path.exists('path')

# Return the absolute path of a relative path as a string
os.path.abspath('./relative_path')
```



Binary files are all other file types, such as word processing documents, PDFs, images, spreadsheets, and executable programs. If you open a binary file in Notepad or TextEdit, it will look like scrambled nonsense, like in Figure 8-5.

<br>

---

<br>

### Read a file:
```python
# .read() - Returns the file content as a single string
print(f.read())


# .readlines() - Returns a list of strings, each string is a line in the file
with open('path') as f:

    # Method 1
    for line in f:
        print(line)

    # Method 2
    file_content = f.readlines()
    for line in file_content:
        print(line)
        
        # Remove any whitespace or \n from lines
        print(line.rstrip())
```

#### Save program 'state'
```python
import shelve
user_name = 'Bob'

with shelve.open('path') as f:
    f['user_name'] = user_name
```


```
Create()
GetAttributes()
Move()
```

<br>

### Write to a file:
```c#
//Overwrite with an array of strings:
string[] lines = { "First line", "Second line", "Third line" };
File.WriteAllLines(pathName, lines);
//File.WriteAllText(pathName, string);


//Append new text to an existing file:
using (StreamWriter file = new StreamWriter(pathName, true))
{
    file.WriteLine("Fourth line");
}
```

<br>

### Other:
```c#
// File.Copy()
File.Copy(pathName, @"c:\temp\newtext.txt");


// File.Delete()
File.Delete(pathName);


// File.Exists()
if (File.Exists(pathName))
{
    //
}
```

<br>

### File.Copy()
```c#
File.Copy(pathName, @"c:\temp\newtext.txt");
```

### File.Delete()
```c#
File.Delete(pathName);
```

### File.Exists()
```c#
if (File.Exists(pathName))
{
    //
}
```

### File.ReadAllText()
Read the file as one string.
```c#
string text = File.ReadAllText(pathName);
```

### File.ReadAllLines()
Creates an array where each element is one line of the file.
```c#
string[] lines = File.ReadAllLines(pathName);

foreach (string line in lines)
{
    Console.WriteLine(line);
}
```

### File.WriteAllLines()
```c#
// There's also WriteAllText (string instead of string[])

string[] lines = { "First line", "Second line", "Third line" };
File.WriteAllLines(pathName, lines);
```

### Append new text to an existing file
```c#
using (StreamWriter file = new StreamWriter(pathName, true))
{
    file.WriteLine("Fourth line");
}
```

<br>

### FileInfo:
FileInfo provides instance methods.
```c#
// Instantiate
FileInfo file = new FileInfo(@"c:\temp\myfile.txt");


// .CopyTo()
file.CopyTo(@"c:\temp\text.txt");


// .Delete()
file.Delete();


// .Exists Property
if (file.Exists)
{
    //
}
```

<br>
<br>

---

<br>
<br>

Methods with no examples yet:
```
Delete()
Move()
GetLogicalDrives()
```

<br>

### Directory:
Directory provides static methods.
```c#
// Directory.CreateDirectory()
string directoryName = @"c:\temp\folder1";
Directory.CreateDirectory(directoryName);


// Directory.GetFiles()
string[] files = Directory.GetFiles(directoryName, *.*, SearchOption.AllDirectories); //*.jpg, *.txt, etc
foreach (string file in files)
    Console.WriteLine(file);


// Directory.GetDirectories()
string[] directories = Directory.GetDirectories(directoryName, *.*, SearchOption.AllDirectories);
foreach (string directory in directories)
    Console.WriteLine(directory);


// Directory.Exists()
if (Directory.Exists(directoryName))
{
    //
}
```

<br>

### DirectoryInfo:
DirectoryInfo provides instance methods.
```c#
// Instantiate
DirectoryInfo directory = new DirectoryInfo(@"c:\temp\folder1");


// .GetFiles()
string[] files = directory.GetFiles(*.*, SearchOption.AllDirectories); //*.jpg, *.txt, etc
foreach (string file in files)
    Console.WriteLine(file);


// .GetDirectories()
string[] directories = directory.GetDirectories(*.*, SearchOption.AllDirectories);
foreach (string dir in directories)
    Console.WriteLine(dir);


// .Exists Property
if (directory.Exists)
{
    //
}
```

<br>
<br>
<br>

### Path Class
The Path class provides static methods for working with a string that is a directory or file path.
```c#
Console.WriteLine(Path.GetFileName(pathName));
Console.WriteLine(Path.GetFileNameWithoutExtension(pathName));
Console.WriteLine(Path.GetExtension(pathName));
Console.WriteLine(Path.GetDirectoryName(pathName));
tempPath = Path.GetTempPath(); // - user's temp folder
```
