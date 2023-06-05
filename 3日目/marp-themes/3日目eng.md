---
marp: true
theme: test
class:
  - slide
---

<!-- paginate: true -->

# AI Study Group 3rd Session

---

## Table of Contents

* What is Python?
* Data Types
* Objects
* Everything is an Object
* Magic Methods

---

## What is Python?

It is one of the programming languages. AI development is mostly done using Python. The reasons for this are:

* Abundance of libraries
* Relatively simple syntax with low learning cost
* Naturally high readability
* Ability to write functions in C language and execute them, enabling the use of high-performance code even in interpreted languages by writing multi-dimensional array objects (ndarray) and numerical computation functions in C language

These are some of the reasons.

---

## Data Types

Similar to C language, Python also has the concept of data types for variables. However, it would be more accurate to say "int object" rather than "int type" in Python. To be even more precise, in Python, everything is an object, and variables store pointers to those objects. However, understanding this requires knowledge about objects, which I will explain later.

---

## Numeric Types

* Integer type (int): Represents whole numbers.
```python
num = 10
```
* Floating-point type (float): Represents numbers with decimal points.
```python
num = 3.14
```

* Complex type (complex): Represents complex numbers consisting of a real part and an imaginary part.
```python
num = 2 + 3j
```

---

## String and Boolean Types

* String type (str): Represents characters or text (strings).
```python
text = "Hello, World!"
```

* Boolean type (bool): Represents true (True) or false (False).
```python
is_true = True
is_false = False
```

---

## Sequence Types

* List type (list): Represents an ordered collection of elements. The elements can have different data types. It is similar to an array, but thinking of it as an array is not entirely incorrect.

```python
my_list = [1, 2, 3, "apple", "banana",True]
```
* Tuple type (tuple): Represents an ordered collection of elements, but once defined, it cannot be modified.
```python
my_list = [1, 2, 3, "apple", "banana",True]
```
Both can be accessed by specifying an index number. For example, `my_list[3]` will retrieve the string `"apple"`.


---


## Dictionary Type

* Dictionary type (dict): Stores data in key-value pairs.
```python
my_dict = {"name": "John", "age": 30, "city": "Tokyo"}
```

To access the values, you specify the key. For example, `my_dict['name']` will retrieve `"John"`.

---

## Program and Main Memory

This is a somewhat general discussion about the relationship between a program and main memory.

The CPU cannot execute a program unless the source code is brought into main memory. So, when executing a program, the source code must be in the main memory.

As a side note, the main memory is divided into the following regions:

* Static region (stores global variables and is released when the program ends)
* Heap region (a region where memory can be dynamically allocated and deallocated; objects (instances) are stored here)
* Stack region (stores functions, including the main function, and local variables)

---

## Classes and Objects

There are often situations where you want to group variables and functions together. Generally, "things" have multiple attributes, and you cannot assign a specific "thing" to a single variable. Classes and objects are essential concepts, especially in machine learning (PyTorch), so it's important to understand them well. Although it may be a common explanation, I will provide an intuitive explanation using a daily-life example.

For example, information about a person includes not only their "name" but also other attributes, such as:

* Name, age, gender, skills, etc.

Now, let's consider storing the information about a person in variables.


---

## Classes and Objects

```python
person1_name = "Suzuki"
person1_age = 22
person1_gender = "male"
```
Now, let's say it's the person's birthday and we need to update their `person1_age`.
```python
def birthday(age):
    return age + 1
person1_age = birthday(person1_age)
```
This might work fine if there's only one person, but it's not a good approach when there are multiple people.

---



## Classes and Objects

When dealing with information about a person (and related functions), it becomes desirable to consolidate and centrally manage that information. That's where the concept of classes and objects comes into play.
```python
class MyClass:
    def __init__(self, name, age, gender):               # Constructor
        self.name = name
        self.age = age
        self.gender = gender
    def birthday(self):
        self.age = self.age + 1

person = MyClass("Suzuki", 22, "male")               # Creating an instance of the class
person.birthday()                                   # Incrementing age due to birthday
```

The diagram is shown on the next page.

---

## Classes and Objects

A class is a blueprint for objects, and an object is an instance (i.e., a representation stored in main memory to execute a program) created based on a class.

---

## Objects

Objects are commonly referred to as instances. The functions within an object (in the previous example, `birthday`) are called methods, and the variables within an object (in the previous example, `self.name`, `self.age`, `self.gender`) are called properties. When referring to both methods and properties together, they are referred to as attributes.

To access (modify or reference) a method, you use the dot notation.
```python
# Omitted code
person = MyClass("Suzuki", 22, "male")               # Creating an instance of the class
person.name = "Suzuki"                               # Modifying a property
person.birthday()                                   # Incrementing age due to birthday
```

---

## Everything is an Object?

In fact, in Python, everything is an object. You can determine the class from which an object is created using the `type()` function. Let's try it out.

For example, `1` is an object of the `int` class, and objects of the `int` class have the `__add__()` method. Methods surrounded by `__` are special methods that are executed when operators (such as `+`) or built-in functions are applied to objects.

Applying the `+` operator to the `1` object of the `int` class is equivalent to calling `1 .__add__(2)`. Let's experiment.
```python
print(1 + 2)
print(1 .__add__(2))  # Note: Add a space after 1 to avoid a syntax error
```

---

## Everything is an Object

Now you understand that everything is an object in Python. Operators (comparison operators, arithmetic operators), built-in functions, and even the behavior of for loops are implemented using special methods (called magic methods) defined with the `__` notation. Therefore, I (personally) believe that understanding objects is the essence of Python.

So, what does a variable store? Actually, objects are assigned unique IDs. Variables in Python correspond to storing these IDs. This is why you can store anything in a variable without explicitly declaring its type, unlike in the C language.

---

## More Advanced Content

For example, the behavior of a for loop can be achieved by applying the magic methods `__iter__()` and `__next__()` to iterators and iterable objects.

Try searching for `object.__` using `ctrl+f` on the [official website](https://docs.python.org/3/reference/datamodel.html). You will see that a wide range of magic methods are defined. On the next page, I will provide examples of these methods with simplified explanations.

---

## Magic Methods

| Magic Method | Corresponding Usage | Function |
|--------------|--------------------|----------|
| `__str__` | `print(object)` | Converts the object to a string (`1` becomes `'1'`, for example) |
| `__lt__` | `x < y` is equivalent to `x.__lt__(y)` | Called when comparing `x` and `y` with `<` |
| `__iter__` | When using a for loop | Returns an iterator; an object with `__iter__()` implemented is called an iterable |
| `__next__` | When using a for loop | Returns the next item; used when iterating with a for loop |

---

## Magic Methods

| Magic Method | Corresponding Usage | Function |
|--------------|--------------------|----------|
| `__getitem__` | `object[index_num]` | Function called when accessing a value with an index number in an array |
| `__call__` | `object()` | Function called when applying the function call operator `()` to an object |

If you read books like [this one](https://www.oreilly.co.jp/books/9784873118178/), you can gain a better understanding. However, I haven't read it yet, so there's a possibility that even I haven't grasped the essence completely.

---

## Next Preview

In this lesson, you learned about variables and objects. In the next lesson, we will focus on syntax and expressions.

---




