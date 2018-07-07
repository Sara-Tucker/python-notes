# Paths and directories
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

# Delete a directory
os.rmdir('path')

# Delete a file
os.remove('path')

# Rename a file or directory
os.rename('./original.txt', './new.txt')
```

<br>

---

<br>

# Files
#### Automatically open and close a file:
```python
with open('path', 'mode') as f:
    #code
```

#### open('path', 'mode') - Opens a file and returns a file object
```
File modes:
r (default) - Open for reading
a - Open for writing and append to the end of the file
w - Open for writing and clear all existing data
x - Create a new file and open it for writing

(any)+ - Open for reading and writing for (any)
    - Append + to one of the modes above.
b - Binary file (image, video, compressed file)
    - If you open a binary file in a text editor it will look obfuscated.
    - Append b to one of the modes above.
    - Example:
        open('/pics/cat.jpg', 'rb')


.close() - Closes a file
```

<br>

#### Read a file:
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
    for line in f:
        print(line.rstrip())
```

<br>

#### Write to a file:
```python
# .write() - Writes to a file; if the file already exists the argument is appended to the file
f.write('string goes here.\n')

# .writelines() - Writes lines to a file; if the file already exists the argument is appended to the file
text = ["a line of text",
    "another line of text",
    "a third line"]
f.writelines(text)
```

<br>

#### Save variables
```python
import shelve

with shelve.open('./data/') as db:
    if 'password' not in db:
        db['password'] = input('Create a password: ')
    password = db['password']

pass_input = input('Enter password: ')```
```
