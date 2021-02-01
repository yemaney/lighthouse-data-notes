# Classes

- Allow us to logically group functions in a way that makes them easy to use
- Class is a blueprint for each of its instances
- Instance variable contain data that is unique to each instance
---

```python
class Employee:

    def __init__(self, first, last, pay):
        self.first =first
        self.last = last
        self.pay = pay
        self.email = first+ '.' + last + '@company.com'
```
# Class Methods
---
- The labels inside the `__init__()` backets are all attributes of the class 
---
```python
    def fullname(self):
        return '{} {}'.format(self.first, self.last)
```
---
- The function above is a method of the class
- when it is called it must be followed by paranthesis ()
---
# Class Variables
```python
class Employee:
    # Class variables
    num_of_emps = 0
    raise_amount = 1.04

    def __init__(self, first, last, pay):
        self.first =first
        self.last = last
        self.pay = pay
        self.email = first+ '.' + last + '@company.com'
        # Increase class num of employees by one each time an instance is instaniated
        Employee.num_of_emps += 1

    def apply_raise(Self):
        # instance variable 'raise_amount'
        self.pay = int(self.pay * self.raise_amount) 

# Can check for attribute from class or instance
Employee.raise_amount
instance.raise_amount

# Reassign isntance attribute 
instance.raise_amount = 1.05
```
- Claass variables are shared by all instances of the class 
- Python fist looks for variable in the instance, then checks for the variable in the class
---
# Classmethods
- Regular methods in a class automatically take the isntance as the arguement (`self`)
- Class method takes the class as the first arguement, using the decorator `@classmethod`

```python
    @classmethod
    def set_raise_amount(cls, amount): # cls means class
        cls.raise_amount = amount

# calling the method
# class method already takes the class as an argument, so only amount is required
Employee.set_raise_amount(1.05)

```
- provide multiple ways of creating objects

```python
 def from_string(cls. emp_Str):
        first, last, pay = emp_str.split('-')
        cls(first, last, pay)
        return cls(first, last, pay)
# provide an alternative constructor that parses a stirn sep by '-', and creates an new instance
```
---
# Static Methods
-  unlike regular and class methods, they don't automatically pass an argument
-  behave like normal functions but we include them in the class because they have some kind of logical connection

```python
    @staticmethod
    def is_workday(day):
        if day.weekday() == 5 or day.weekday() 6:
            return False
        return True
```
- appropraite when the function doesn't have to access the instance or the class
---
### Quick review
| Type of method | Example                         | Argument taken |
|----------------|---------------------------------|----------------|
| Regular        | def \_\_init__(self):             | self           |
| Class          | @classmethod def cls_meth(cls): | cls            |
| Static         | @staticmethod def function():   | none           |