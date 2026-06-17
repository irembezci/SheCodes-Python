
# PYTHON OOP (Object-Oriented Programming) HOMEWORKS

---

## 1. User Class (full_name method)

```python
class User:
    def __init__(self, first_name, last_name):
        self.first_name = first_name
        self.last_name = last_name

    def full_name(self):
        return f"{self.first_name} {self.last_name}"

user1 = User("Emma", "Johnson")
user2 = User("Liam", "Smith")

print(user1.full_name())
print(user2.full_name())

user1.first_name = "Olivia"
print(user1.full_name())
print(user2.full_name())
```

---

## 2. Dog Class (casual_name based on age)

```python
class Dog:
    def __init__(self, name, age=0):
        self.name = name
        self.age = age

    def casual_name(self):
        if self.age < 2:
            return "puppy"
        elif self.age < 10:
            return "grown up dog"
        else:
            return "old dog"

    def greet(self):
        return f"Hello, I'm a {self.casual_name()} named {self.name}"

snoopy = Dog("Snoopy")
print(snoopy.greet())
```

---

## 3. User Class (century based on birth year)

```python
class User:
    def __init__(self, name, birth_year):
        self.name = name
        self.birth_year = birth_year

    def welcome(self):
        if self.birth_year < 2000:
            return f"Welcome {self.name}, you were born during the 20th century"
        else:
            return f"Welcome {self.name}, you were born during the 21st century"

user1 = User("Ahmet", 1985)
user2 = User("Zeynep", 2005)

print(user1.welcome())
print(user2.welcome())
```

---

## 4. FrenchUser and SpanishUser (Inheritance)

**user.py**
```python
class User:
    def __init__(self, name):
        self.name = name

    def greet(self):
        print(f"Welcome - {self.name}")
```

**french_user.py**
```python
from user import User

class FrenchUser(User):
    def greet(self):
        print(f"Bonjour - {self.name}")
```

**spanish_user.py**
```python
from user import User

class SpanishUser(User):
    def greet(self):
        print(f"Hola! - {self.name}")
```

**main.py**
```python
from french_user import FrenchUser
from spanish_user import SpanishUser

pierre = FrenchUser("Pierre")
luis = SpanishUser("Luis")

pierre.greet()
luis.greet()
```

---

## 5. Weather Class

```python
class Weather:
    def __init__(self, city):
        self.city = city
        self.temperature = None
        self.condition = None

    def set_weather(self, temperature, condition):
        self.temperature = temperature
        self.condition = condition

    def display_weather(self):
        print(f"Weather in {self.city}: {self.temperature}°C, {self.condition}")

paris = Weather("Paris")
paris.set_weather(27, "sunny")
paris.display_weather()
```

---

# FILE HANDLING HOMEWORKS

---

## 6. Reading and Printing TODO.txt

```python
%%writefile TODO.txt
Have breakfast
Study Python
Walk the dog
Do laundry
Reply to emails
```

```python
with open('TODO.txt', 'r') as file:
    tasks = file.readlines()

print("My todo list:")
for task in tasks:
    print(f"- {task.strip()}")
```

---

## 7. Reading cities.txt

```python
with open('cities.txt', 'r') as file:
    cities = file.readlines()

for city in cities:
    print(f"I want to visit {city.strip()}")
```

---

## 8. Reading CSV (temperatures.csv)

```python
import csv

with open('temperatures.csv', 'r') as file:
    csvFile = csv.reader(file)
    next(csvFile)
    for row in csvFile:
        print(f"It is {row[2]} and {row[1]}°C in {row[0]}")
```

---

## 9. Appending to CSV

```python
import csv

with open('temperatures.csv', 'a', newline='') as file:
    writer = csv.writer(file)
    writer.writerow(['Berlin', '10', 'foggy'])
    writer.writerow(['Rome', '32', 'sunny'])
```

---

## 10. Reading Customer CSV

```python
import csv

try:
    with open('customers.csv', 'r') as file:
        csvFile = csv.reader(file)
        next(csvFile)
        for row in csvFile:
            print(f"Customer #{row[0]}, {row[1]} {row[2]}, {row[3]}")
except FileNotFoundError:
    print("Error: customers.csv file not found!")
except Exception as e:
    print(f"Error: {e}")
```

---

# EXCEPTION HANDLING HOMEWORKS

---

## 11. try/except Examples

```python
try:
    file = open('cities.txt', 'r')
    content = file.read()
except FileNotFoundError:
    print("cannot find the file")

try:
    12 / 0
except ZeroDivisionError:
    print('cannot divide number by 0')

try:
    a + b
except Exception:
    print('something went wrong')

print("hello world")
```

---

## 12. CSV with Exception Handling

```python
import csv

try:
    with open('cities.csv', 'r') as file:
        csvFile = csv.reader(file)
        for row in csvFile:
            print(f"It is {row[1]} in {row[0]}.")
except FileNotFoundError:
    print("Error: cities.csv cannot found")
except Exception as e:
    print(f"Error: {e}")
```
```
