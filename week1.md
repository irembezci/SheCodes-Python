# WEEK 1 – PYTHON OOP (Object-Oriented Programming) HOMEWORKS

## 1. User Class (full_name method)

We created a `User` class that stores a first name and a last name. The `full_name()` method combines them into a full name.  
This helps us understand how to define a class, use the `__init__()` method to initialize attributes, create methods, and modify object properties.

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

## 2. Dog Class (casual_name based on age)

We built a `Dog` class that assigns a casual name like "puppy", "grown up dog", or "old dog" based on the dog's age. The `greet()` method calls `casual_name()` inside it.  
This teaches us how to use default parameters (`age=0`), call one method from another, and apply conditional logic (`if/elif/else`) inside a class.

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

## 3. User Class (century based on birth year)

We created a `User` class that determines whether a user was born in the 20th or 21st century based on their birth year.  
This helps us practice using `if/else` logic inside a method and accessing object attributes from within methods.

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

## 4. FrenchUser and SpanishUser (Inheritance)

We created `FrenchUser` and `SpanishUser` classes that inherit from `User`. Each one overrides the `greet()` method to say hello in French and Spanish.  
This helps us understand inheritance (parent-child classes), method overriding, and modular programming with `import`.

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

-

## 5. Weather Class

We built a `Weather` class that stores a city name and initially sets temperature and condition to `None`. We used methods to set and display weather data.  
This teaches us how to use `None` as a placeholder, assign values later, and modify object state through methods.

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
```
