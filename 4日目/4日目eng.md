---
marp: true
theme: test
class:
  - slide
---

<!-- paginate: true -->

# AI研究会第4回

---

## 目次

* 構造化プログラミング
* 制御構文


---

## Background of Structured Programming
Assembler language and early versions of FORTRAN and COBOL often resulted in unclear program structures due to the excessive use of goto statements, as depicted in the diagram.


---

## What is Structured Programming?
In 1968, Dijkstra argued that by layering basic structures (blocks) of sequence, iteration, and selection and executing them sequentially from top to bottom, it is possible to write easily understandable programs. This concept had a significant impact on subsequent programming languages. Structured programming refers to the programming paradigm where blocks are stacked on top of each other, flowing from top to bottom, as depicted in the diagram. Flowcharts are visual representations of this flow.

---

## Types of Blocks
In Python, blocks are also referred to as control structures, and the following are some examples:
* if block (if statement)
* for block (for loop)
* while block (while loop)
* with block (with statement)
* exception handling (try and except)


---

## Blocks in Python
In Python, blocks are represented by indentation (whitespace created by pressing the Tab key), whereas in C language, blocks are enclosed within curly braces `{}`. Here's an example:
```c
int score = 80;
if ( 60 < score )
{
    print("Passed the course.");
}
else
{
    print("Failed to pass the course.");
}
```

This is how the above code would be represented in Python, 

---

## Blocks in Python

```python
score = 80
if 60 < score:
    print("Passed the course.")
else:
    print("Failed to pass the course.")
```



Unlike C, which uses curly braces `{}` to enclose blocks, Python represents blocks using indentation (pressing the Tab key inserts whitespace).

---

## if

It is a syntax used for conditional branching. It is written as follows:

```python
if condition1:
    # Code block to be executed when condition1 is true
elif condition2: # "elif" can be used multiple times; it can also be omitted
    # Code block to be executed when condition1 is false and condition2 is true
else: # "else" is optional
    # Code block to be executed when neither condition1 nor condition2 is true
```

For example, it can be written as follows: (`else if` and `else` can be omitted.)
```python
num = 12
if num > 10:
    print("BIG")
    print("BIG")
    print("BIG")
```
---

## while

It will loop as long as the condition is satisfied. It can be written as follows:

```python
while condition:
    # Code to be executed when the condition is satisfied
```

For example, it can be written as follows:
```python
n = 0
while n < 10:
    print(n)
    n += 1
```

---

## for loop

Similar to "while," "for" also means "for the duration of." The "for" loop repeats the process for each element in a list, tuple, dictionary keys, characters in a string, or lines in a file. It can be written as follows:
```python
for variable_name in iterable_object:
    # Code block to be executed
```
For example, it can be written as:
```python
for n in [1, 2, 3]:          # List
    print(n)                 #=> 1, 2, 3

for n in (1, 2, 3):          # Tuple
    print(n)                 #=> 1, 2, 3
```

---

## break、continue

If you want to exit the loop prematurely in a "for" or "while" loop, you can use "break." Here are examples of how to use it:
```python
for n in range(10): # To iterate 10 times from 0 to 9, you can use range(10).
    if n == 5:
        break
    print(n)                 # 0, 1, 2, 3, 4

```
If you want to skip the current iteration and move to the next iteration in a "for" or "while" loop, you can use "continue." Here are examples of how to use it:
```python
for n in range(10):
    if n == 5:
        continue
    print(n)                 # 0, 1, 2, 3, 4, 6, 7, 8, 9
```

---

## Exception Handling

Usually, when an error occurs, the program stops executing at that point. However, if you want to handle the error and continue execution, you can use exception handling. It can be written as follows:
```python
try:
    # Code that might raise an error
except Error1:
    # Code to handle Error1
else:
    # Code to execute if no error occurs
```


---

## 例外処理

```python
string = 'ABC'
try:
    c = string[5]                    # There is no 5th character, so IndexError exception occurs
except IOError:
    print('IOError')              # This block executes if IOError exception occurs
except IndexError:
    print('IndexError')           # This block executes if IndexError exception occurs
except:
    print('Unknown')              # This block executes for any other exception
else:
    print('Other')                # This block executes if no exception occurs
finally:
    print('Finally')              # This block always executes

```

---

## with Statement

By using the "with" statement, the cleanup process of an object is automatically called when the "with" block is exited. It is often used when working with text files or other file operations. Examples are shown below:
```python
# Without using "with" statement
f = open("test.txt")
print(f.read())
f.close()

# Using "with" statement - Method 1
with open("test.txt") as f:
    print(f.read())

```

---

