# Databases

SQLite:  
https://docs.python.org/3/library/sqlite3.html  
https://sebastianraschka.com/Articles/2014_sqlite_in_python_tutorial.html

<br>

```python
import sqlite3

def start():
    conn = sqlite3.connect('books.db')
    c = conn.cursor()

    c.execute('CREATE TABLE IF NOT EXISTS book (id INTEGER PRIMARY KEY, title text, author text, year integer, isbn integer)')

    conn.commit()
    conn.close()

# Functions from imported module are automatically called at start of file that is importing
start()


def insert(title, author, year, isbn):
    conn = sqlite3.connect('books.db')
    c = conn.cursor()

    c.execute('INSERT INTO book VALUES (NULL,?,?,?,?)', (title, author, year, isbn))

    conn.commit()
    conn.close()


def view():
    conn = sqlite3.connect('books.db')
    c = conn.cursor()

    c.execute('SELECT * FROM book')
    rows = c.fetchall()

    conn.close()
    return rows


def search(title='', author='', year='', isbn=''):
    conn = sqlite3.connect('books.db')
    c = conn.cursor()

    c.execute('SELECT * FROM book WHERE title=? OR author=? OR year=? OR isbn=?', (title, author, year, isbn))
    rows = c.fetchall()

    conn.close()
    return rows


def delete(id):
    conn = sqlite3.connect('books.db')
    c = conn.cursor()

    c.execute('DELETE FROM books WHERE id=?', (id,))

    conn.commit()
    conn.close()


def update(id, title, author, year, isbn):
    conn = sqlite3.connect('books.db')
    c = conn.cursor()

    c.execute('UPDATE book SET title=?, author=?, year=?, isbn=? WHERE id=?', (title, author, year, isbn, id))

    conn.commit()
    conn.close()


#insert('c', 'd', 3, 4)
print(view())
#print(search('c'))
```

<br>

```python
import sqlite3

def create_table():
    connection = sqlite3.connect('database.db')
    cursor = connection.cursor()

    cursor.execute('CREATE TABLE IF NOT EXISTS store (item TEXT, quantity INTEGER, price REAL)')

    connection.commit()
    connection.close()


def insert(item, quantity, price):
    connection = sqlite3.connect('database.db')
    cursor = connection.cursor()

    cursor.execute('INSERT INTO store VALUES (?,?,?)', (item,quantity,price))

    connection.commit()
    connection.close()


def delete(item):
    connection = sqlite3.connect('database.db')
    cursor = connection.cursor()

    cursor.execute('DELETE FROM store WHERE item=?', (item,))

    connection.commit()
    connection.close()


def update(quantity, price, item):
    connection = sqlite3.connect('database.db')
    cursor = connection.cursor()

    cursor.execute('UPDATE store SET quantity=?, price=? WHERE item=?', (quantity, price, item))

    connection.commit()
    connection.close()


def view():
    connection = sqlite3.connect('database.db')
    cursor = connection.cursor()

    cursor.execute('SELECT * FROM store')
    rows = cursor.fetchall()

    connection.close()
    print(rows)


create_table()
delete('Water')
update(7, 7, 'Coffee')
#insert('Water',3,2)
#insert('Coffee',6,6)
view()
```
