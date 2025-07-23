# 📘 Python OOP from Scratch — Beginner to Pro (Part 23–29)

Welcome to this beginner-friendly OOP (Object-Oriented Programming) guide in Python. This is ideal for anyone just starting their journey into object-oriented design, or those looking to understand the core building blocks of Python classes, objects, inheritance, encapsulation, and more.

We’ll cover everything step by step with relatable analogies, simple examples, and full code walkthroughs. Every part includes a **mini project** and the **GitHub repo** is referenced for complete code.

[Python Mastery Part 1](https://github.com/Gauri2882/python-mastery-01)

[Python Mastery Part 2](https://github.com/Gauri2882/python-mastery-02)

[Python Mastery Part 3](https://github.com/Gauri2882/python-mastery-03)

---

## 📂 Part 23: Classes, Constructors, and Encapsulation

### 💡 Real-life Analogy
Think of a **Book** as an object. Each book has a `title`, `author`, and some functionality (like showing details). You create books with different data but share the same template.

### 🧠 Theory
- A **class** is a blueprint.
- A **constructor** (`__init__`) initializes object data.
- **Encapsulation** hides internal details — by using `private` or `protected` members.

### 🧪 Simple Code Example
```python
class Book:
    def __init__(self, title, author):
        self.title = title
        self.author = author
    
    def show_details(self):
        print(f"📖 {self.title} by {self.author}")

book1 = Book("1984", "George Orwell")
 # Output: 1984 by George Orwell
```

### 🧩 Mini Project: Library Management System

```python
class Library:
    def __init__(self):
        self.books = []

    def add_book(self, book):
        self.books.append(book)
        print(f"Added '{book.title}' by {book.author}")

    def show_books(self):
        print("\nLibrary collection:")
        for book in self.books:
            book.show_details()

library = Library()
library.add_book(Book("1984", "George Orwell"))
library.add_book(Book("To Kill a Mockingbird", "Harper Lee"))
library.show_books()
```


## 🧬 Part 24: Inheritance and Method Overriding

### 🐾 Real-life Analogy

A **Dog** is an **Animal**, but it barks instead of making generic animal sounds.

### 🧠 Theory

* **Inheritance** allows a class to reuse features from a base class.
* **Method Overriding** changes a method’s behavior in a child class.

### 🧪 Simple Example

```python
class Animal:
    def sound(self):
        print("Animal sound")

class Dog(Animal):
    def sound(self):
        print("Dog barks")

dog = Dog()
dog.sound()  # Output: Dog barks
```

### 🧩 Mini Project: Employee Management System

```python
class Employee:
    def __init__(self, name, salary):
        self.name = name
        self.salary = salary

    def bonus(self):
        return 0

    def show_details(self):
        print(f"{self.name} earns {self.salary} with bonus {self.bonus()}")

class Manager(Employee):
    def bonus(self):
        return self.salary * 0.1  # 10%

class Developer(Employee):
    def bonus(self):
        return self.salary * 0.05  # 5%

mgr = Manager("Alice", 100000)
dev = Developer("Bob", 80000)
mgr.show_details()
dev.show_details()
```

---

## 🌀 Part 25: Polymorphism and Duck Typing

### 🦆 Real-life Analogy

Different animals can make sounds — whether it's a cat, dog, or duck. All you care is that `make_sound()` exists.

### 🧠 Theory

* **Polymorphism** means different classes respond to the same method call.
* **Duck Typing** in Python: "If it quacks like a duck..."

### 🧪 Simple Example

```python
class Dog:
    def make_sound(self):
        print("Bark")

class Cat:
    def make_sound(self):
        print("Meow")

for animal in [Dog(), Cat()]:
    animal.make_sound()
```

### 🧩 Mini Project: Animal Sound Simulator

```python
class Animal:
    def make_sound(self):
        print("Animal sound")

class Dog(Animal):
    def make_sound(self):
        print("The dog barks")

class Cat(Animal):
    def make_sound(self):
        print("The cat meows")

class Duck(Animal):
    def make_sound(self):
        print("The duck quacks")

class AnimalSoundSimulator:
    def __init__(self):
        self.animals = []

    def add_animal(self, animal):
        if isinstance(animal, Animal):
            self.animals.append(animal)
            print(f"{animal.__class__.__name__} added to simulator")

    def make_all_sounds(self):
        for animal in self.animals:
            animal.make_sound()

sim = AnimalSoundSimulator()
sim.add_animal(Dog())
sim.add_animal(Cat())
sim.add_animal(Duck())
sim.make_all_sounds()
```

---

## 🔐 Part 26: Encapsulation — Access Modifiers and Validation

### 🧳 Real-life Analogy

You don’t share your ATM PIN. Only you can access and change it securely.

### 🧠 Theory

* `__var` = Private
* `_var` = Protected
* Use **getters/setters** to access internal data

### 🧪 Simple Example

```python
class User:
    def __init__(self, username):
        self.username = username
        self.__password = None

    def set_password(self, password):
        if len(password) >= 8:
            self.__password = password
            print("Password set successfully")
        else:
            print("Password too short")

    def get_password(self):
        return "*" * len(self.__password)
```

### 🧩 Mini Project: Secure User Profile App

```python
class UserProfile:
    def __init__(self, username, email, password):
        self.username = username
        self._email = email
        self.__password = None
        self.set_password(password)

    def get_email(self):
        return self._email

    def set_email(self, new_email):
        if "@" in new_email:
            self._email = new_email
            print("Email updated successfully")

    def set_password(self, new_password):
        if len(new_password) >= 8:
            self.__password = new_password
            print("Password updated successfully")

    def show_profile(self):
        print(f"Username: {self.username}")
        print(f"Email: {self._email}")
        print(f"Password: {'*' * len(self.__password)}")
```

---

## ⚙️ Part 27: Static Methods vs Class Methods

### 🧠 Theory

* `@staticmethod` doesn’t take `self` or `cls`
* `@classmethod` takes `cls` and can modify class variables

### 🧪 Simple Example

```python
class Calculator:
    base_value = 100

    @staticmethod
    def add(a, b):
        return a + b

    @classmethod
    def multiply_base(cls, multiplier):
        return cls.base_value * multiplier

print(Calculator.add(10, 20))          # Output: 30
print(Calculator.multiply_base(2))     # Output: 200
```

### 🧩 Mini Project: Inventory Management System

```python
class Inventory:
    total_items = 0

    def __init__(self, product_name, price, quantity):
        self.product_name = product_name
        self.price = price
        self.quantity = quantity
        Inventory.total_items += quantity

    def show_product_details(self):
        print(f"Product: {self.product_name}, Price: {self.price}, Quantity: {self.quantity}")

    def sell_product(self, amount):
        if amount <= self.quantity:
            self.quantity -= amount
            Inventory.total_items -= amount
            print(f"Sold {amount} of {self.product_name}")

    @staticmethod
    def calculate_discount(price, discount):
        return price * (1 - discount/100)

    @classmethod
    def total_items_report(cls):
        print(f"Total items in inventory: {cls.total_items}")
```

---

## 🏧 Part 28: Final Project — Mini ATM System

```python
class BankAccount:
    def __init__(self, account_number, pin, balance=0):
        self.account_number = account_number
        self.__pin = pin
        self.__balance = balance

    def validate_pin(self, entered_pin):
        return entered_pin == self.__pin

    def check_balance(self):
        print(f"Balance: ₹{self.__balance}")

    def deposit(self, amount):
        if amount > 0:
            self.__balance += amount
            print(f"Deposited ₹{amount}. New balance: ₹{self.__balance}")

    def withdraw(self, amount):
        if amount > self.__balance:
            print("Insufficient funds")
        elif amount > 0:
            self.__balance -= amount
            print(f"Withdrew ₹{amount}. New balance: ₹{self.__balance}")

    def change_pin(self, old_pin, new_pin):
        if self.validate_pin(old_pin) and len(new_pin) == 4:
            self.__pin = new_pin
            print("PIN updated successfully")
```

## ✅ Part 29: Summary and Wrap-up

### 🔁 Recap

* Classes & Constructors
* Inheritance & Overriding
* Polymorphism & Duck Typing
* Static vs Class Methods

### 💭 Final Words

Understanding these principles will help you write scalable, reusable, and clean Python code. Keep building mini projects and level up!

Happy Coding! 💻


