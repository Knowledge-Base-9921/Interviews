# Level 1: Basic

## Credits

* [Top 100 Basic Python Interview Questions & Answers for Beginners](https://pynative.com/beginner-python-interview-questions/)

## Questions

### 1. What is Python? Enlist some of its benefits

<details>

<summary>Notes: Click to expand</summary>

* Python is an **open source**, **high-level**, **interpreted**, **general-purpose** programming language.

    | Term | Definition |
    |:-----|:-----------|
    | Open-source | Freely available source code anyone can modify, distribute, or contribute to (via GitHub) fostering community-driven improvements. |
    | High-Level | Abstraction of low-level memory management. z.B., List comprehension for python, no need to specify C like pointers |
    | Interpreted | Runs line-by-line + no compilation step like C/C++/Java |
    | General-Purpose | Versatility in use cases mentioned above: Data Science, ML, DL, Web Development, LLM |

* **Executable Pseudocode**:
    * Python's **indentation-based syntax** reads like pseudocode.
    * It is know for its code-readability with a simple-clear syntax making it easier to learn and use.
    * **No curly-brackets** like C/C++/Java where the code can be read as pseudocode.

* It supports various **programming paradigms**: OOPs, Procedural Programming, Functional Programming

* Benefits/Applications:
    * Easy to learn: Simple Syntax and structure
    * Large Community: Extensive support and resources to learn/use + Open-source.
    * Versatile: Used in Data Science, ML, DL, Web Development
    * Libraries: Vast collection of libaries and pre-built modules for various tasks.
    * Cross-Platform: Can run on different operating systems.

</details>

### 2. What is the difference between an interpreted and a compiled language?

<details>

<summary>Notes: Click to expand</summary>

| Aspect | Interpreted Language | Compiled Language |
|:-------|:---------------------|:------------------|
| Execution Process	| Line-by-line via interpreter at runtime (e.g., Python: python script.py reads/executes sequentially).	| Full translation to machine code/bytecode first via compiler, then runs executable (e.g., C: gcc file.c -o exe). |
| Examples | Python, JavaScript, Ruby. | C, C++, Java (bytecode), Go. |
| Speed | Slower runtime (interpreter overhead per line); great for prototyping. Example: Jupyter cell-by-cell testing. | Faster runtime (pre-translated); ideal for production. Example: C++ binary runs natively. |
| Development Cycle | Instant testing—no build step. Edit print("Hi"), rerun immediately. | Slower: Edit → Compile → Run (errors caught early). Takes seconds/minutes for large projects. |
| Error Detection | Runtime only (e.g., x = undeclared_var crashes mid-script). | Compile-time + runtime (syntax caught before run). |
| Portability | Highly portable (interpreter handles platform diffs). Python script runs anywhere with Python installed. | Executable often platform-specific; Java bytecode more portable via JVM. |
| Use Case | Scripting, web/ML prototyping (your RAG chatbots, SAP GenAI Hub SDK). | Systems/performance apps (SAP HANA core, embedded automotive). |

</details>

<details>

<summary>Scenario: Imagine you have a recipe in a foreign language.</summary>

* **Interpreting**: You have a translator who reads the recipe line by line and tells you what to do immediately.
* **Compiling**: You have someone who translates the entire recipe into your language beforehand. Then, you can follow the translated recipe directly.

</details>

### 3. Is Python case sensitive?

<details>

<summary>Notes: Click to expand</summary>

* Yes, Python is absolutely case-sensitive.
* z.B., ``my_variable``, ``My_Variable``, and ``MY_VARIABLE`` are treated as three distinct variables. 
* Case sensitivity applies to variable names, function names, class names, and other identifiers.

* **Identifiers**
    * in Python are **user-defined names** given to variables, functions, classes, modules, and other objects to reference them in code. 
    * They make programs readable by replacing memory addresses with meaningful names like ``userAge`` or ``calculateTotal``
    * Rules:
        * Start with letter (a-z, A-Z) or underscore _ (not digit).
        * Contain letters, digits (0-9), or underscores only.
        * Case-sensitive: Count ≠ count.
        * Cannot be Python keywords (e.g., if, class, def—check with keyword.iskeyword()).
        * No spaces or special chars (@, #, $).

</details>

### 4. Can you tell us if Python is object-oriented or functional programming?

<details>

<summary>Notes: Click to expand</summary>

* Both.
* Python is a multi-paradigm language.
* OOP: can write classes and objects
* Functional: Can use Lambdas, maps, filter, reduce functins

</details>

### 5. What are loops in Python?

<details>

<summary>Notes: Click to expand</summary>

* Loops in Python: Repeated execution of a code block until a specific condition is met or the range of sequence ends.

| Feature | for Loop | while Loop |
|:--------|:---------|:-----------|
| Use Case | Iterating over a sequence or range | Running until a condition becomes False |
| Termination | Stops after completing the sequence | Stops when the condition evaluates to False |
| Structure | Predefined iterations | Conditional iterations |
| When to use | Fixed iterations known: range, lists, strings, iterables | Unknown iterations, depends on runtime condition |
| Example | Process Customer List | User input validation (search until found) |

* ``range()`` function:
    * **generates** a sequence of numbers and **returns** a range iterable object.
    * Useful for a `for` loop to iterate over.
    * Syntax: `range(start, stop, range)`
        * stop is exclusive

</details>

### 6. What is the difference between `break`, `continue` and `pass` statements ?

<details>

<summary>Notes: Click to expand</summary>

| Statement | What it does | Real-life example | Generic programming example (in words) |
|:----------|:-------------|:------------------|:---------------------------------------|
| ``break`` | Exits the loop completely when a condition is met | Stop scrolling contacts once you find the person you need | Loop through user records; when you find the matching ID, stop the loop and process that single user. |
| ``continue`` | Skips the rest of the current iteration and moves to the next one | Skip reading newsletters and jump to the next email | Loop through transactions; skip those marked as “test data” and process only real transactions. |
| ``pass`` | Does nothing; used as a placeholder to keep the code syntactically correct | Acknowledge a future agenda item but do nothing now | Define handle_error() now but leave it empty, planning to add real logic later. |

</details>

<details>

<summary>Scenario: Order Processing Pipeline</summary>

```python

orders = [
    {"id": 101, "amount": 150, "status": "paid"},
    {"id": 102, "amount": -50, "status": "error"},  # Skip negative amounts
    {"id": 103, "amount": 200, "status": "paid"},
    {"id": 104, "amount": 0, "status": "fraud"},    # CRITICAL: Stop processing
    {"id": 105, "amount": 75, "status": "pending"}  # Future: TODO implement
]

for order in orders:
    print(f"Processing order {order['id']}")
    
    # CONTINUE: Skip invalid data (negative amounts)
    if order['amount'] < 0:
        print(f"  → Skipping invalid amount: {order['amount']}")
        continue
        
    # BREAK: Stop on critical fraud detection
    if order['status'] == 'fraud':
        print(f"  → FRAUD DETECTED! Halting pipeline.")
        break
        
    # PASS: Placeholder for future features (pending orders)
    if order['status'] == 'pending':
        print(f"  → Pending order {order['id']} (TODO: implement workflow)")
        pass  # Will add approval logic later
    
    # Normal processing
    print(f"  → Processed: ${order['amount']}")

print("Pipeline completed.")


```

</details>

### 7. How can you use an ``else`` clause with loops in Python?

<details>

<summary>Notes: Click to expand</summary>

* The `else` clause executes after the loop is finished unless the loop terminates preemptively with a ``break`` statement.

</details>

<details>

<summary>Scenario: Check if a customer order contains invalid items (e.g., expired products).</summary>

```python

# Validate shopping cart - SAP inventory check
order_items = ["milk", "bread", "expired_yogurt", "eggs"]

for item in order_items:
    if "expired" in item:  # Invalid item found
        print(f"REJECT: {item} is expired!")
        break
else:
    # Only runs if NO invalid items (no break)
    print("APPROVE: All items valid ✓")

```

</details>

### 8. What is nested loops? How to use it

<details>

<summary>Notes: Click to expand</summary>

* Loops within loops.
* The inner loop executes completely for each iteration of the outer loop.
* The inner and outer loop can be either `for` and/or `while`.

* Use Cases:
    * Processing multi-dimensional data: matrices, 2-D Lists
    * Real-life situations:
        * Check stock across multiple warehouse locations (outer loop) and within each location, verify multiple product categories (inner loop)

</details>

### 9. Why is indentation significant in Python?

<details>

<summary>Notes: Click to expand</summary>

* Indentation is how Python defines code-blocks.
* Part of the syntax.
* Incorrect indentation will lead to `IndentationError`.

</details>

### 10. What are comments in Python, and why are they important?

<details>

<summary>Notes: Click to expand</summary>

* Lines of code ignored by the Python interpreter.
* Single-line comments: `#`
* Multi-line comments: `"""` or `'''`

* Benefits:
    * Used to explain what the code does -> increase code-readability.
    * Code Debugging.
    * Documentation.

</details>

### 11. What is the purpose of PYTHONSTARTUP, PYTHONCASEOK, and PYTHONHOME environment variables?

<details>

<summary>Notes: Click to expand</summary>

* Environment variables affecting Python''s behaviour.

| Variable | Purpose |
|:---------|:--------|
| ``PYTHONSTARTUP`` | Path to script executed automatically when interactive Python shell starts. Preloads modules, custom functions (e.g., ~/.pythonrc.py with import pandas, numpy). |
| ``PYTHONCASEOK`` | Allows case-insensitive module imports on case-sensitive filesystems (Windows: PYTHONCASEOK=1 imports MyModule.py as mymodule). Rarely used. |
| ``PYTHONHOME`` | Custom prefix for Python installation. Overrides standard library path (e.g., virtual envs, embedded Python: PYTHONHOME=/custom/python). |

</details>

### 12. What are the different data types in Python?

<details>

<summary>Notes: Click to expand</summary>

* Python has several built-in data types. Here are some of the most common ones:

| Category | Built-in Data Type | Description | Example | Mutability |
|:---------|:-------------------|:------------|:--------|:-----------|
| Numeric | `int` | Whole Numbers | -1, 0, 1 | No |
| | `float` | Decimal Number | 3.14 | No |
| | `complex` | Real + Imaginary Numbers | 1+2j | No |
| String | `str` | Textual Data, Characters | "Ryan Gosling" | No |
| Boolean | `bool` | Logical Values | `True`, `False` | No |
| Sequence | `list` | Ordered + Mutable Sequence | [1,``2``,`3.4`] | Yes |
| | `tuple` | Ordered + Immutable Sequence | (1,``2``,`3.4`) | No |
| | `range` | Immutable Number sequence for loops | range(1,10,2) | No |
| Mapping | `dict` | Unorderd Mutable Key:Value pairs | {"1":1, "2":2} | Yes |
| Set | `set` | Unordered + Mutable Unique items | {1,2,3} | Yes |
| | `frozenset` | Immutable set | frozenset([1, 2, 3]) | No |
| Binary | `bytes` | Immutable Byte Sequence | b"Hello" | No |
| | `bytearray` | Mutable Byte Sequence | bytearray(b"Hello") | Yes |
| | `memoryview` | Access Object Memory without copying | memoryview(b"Hello") | No |

</details>


### 14. Explain the difference between mutable and immutable data types. Give examples.

<details>

<summary>Notes: Click to expand</summary>

| Aspect          | Mutable                                            | Immutable                                       |
|:----------------|:---------------------------------------------------|:------------------------------------------------|
| Definition      | Can change contents after creation                 | Cannot change contents after creation           |
| Common Examples | list, dict, set, bytearray                         | int, float, str, tuple, range, frozenset        |
| Modification    | Modifying a mutable object doesn’t create a new object; it changes the existing one in place. | Any operation that seems to modify an immutable object actually creates a new object with the changed value |
| Memory Behavior | Same id() before/after change                      | New id() after modification                     |
| Hashable?       | No (cannot be dict keys)                           | Yes (can be dict keys)                          |
| SAP Use Case    | Dynamic data: Order processing lists, config dicts | Fixed data: API keys, model configs, cache keys |

* `TypeError`:
    * If you try to change the contents of the immutable objects.
    * z.B., _str = "123" and _str[0]="4" -> TypeError

</details>


### 15. How does Python implement dynamic typing?

<details>

<summary>Notes: Click to expand</summary>

* **Dynamic Typing**: Python checks the type of the variable at runtime, not during compilation.
* No need to specify the type of the variable when it is defined.
* Type of a variable can also be changed during the execution of the program, if its assigned a value of a different type.
* While it makes coding easier, it can also lead to ``TypeError`` or other errors.

* Use **type()** to check the type of the variable.
    * **Debugging**: To check unexpected behaviour.
    * **Documentation**: Increase code-readability.
    * **Conditional Object**: Execute different code blocks based on the object type.

</details>

### 16. What is type conversion (casting) in Python and how is it performed?

<details>

<summary>Notes: Click to expand</summary>

* Process of changing the data type of a variable.

| Type Casting Type | Description | Example |
|:------------------|:------------|:--------|
| Explicit | Python does the type casting automatically | a=1 is int, b=2.3 is float, a = a+b becomes float |
| Implicit | Manually by the programmer | ``int(), float(), str(), bool(), list(), tuple(), set()`` |

</details>

### 17. How do you take user input in Python ? Also explain the help() function in Python.

<details>

<summary>Notes: Click to expand</summary>

* ``input()``: Takes user input and returns as string. 
* ``help()``: Gets interactive information about variables / classes / objects. The following information can be derived:
    * Docstring: For Functions, it displays the Multiline strings used for documentation.
    * Signature: For Function/Method, it displays their signature showing the parameters.
    * Description: For Objects, it lists what the object does.
    * Methods/Attributes: For classes/modules, it lists the available methods and attributes.

</details>

### 18. What are strings in Python? How do you concatenate them?

<details>

<summary>Notes: Click to expand</summary>

* Immutable sequences of character used to represent text.
* Single Quotes or Double Quotes used to represent a string.
* `str()` used for type casting.
* Concatenation:
    * `+` operator:
        * Efficient for joining a small number of strings.
        * Inefficient for concatenation in repeated sequence of loops as it keeps on creating new string objects.
    * `.join()` method: Efficient for joining a **large number of strings** from a list/iterable object and in **loops**.

</details>

### 19. What is slicing in Python?

<details>

<summary>Notes: Click to expand</summary>

* Extracts portions of sequences from iterable objects: lists, tuples, strings
* Colon operator with square brackets.

</details>

### 20. How can you reverse a string in Python?

<details>

<summary>Notes: Click to expand</summary>

* Slicing and building a new string: _str[::-1]
* `reversed()` + `join()`: ''.join(reversed(original_str))
* Iteration and building a new string: for loop

</details>

### 21. How to format strings in Python?

<details>

<summary>Notes: Click to expand</summary>

* ``.format()``: Versions < 3.6
* `f-strings`: Versions >= 3.6

```python

_name = "Ryan Gosling"

print("My name is literally: {}".format(_name))
print(f"My name is literally: {_name}")

```

</details>

### 22. What are some useful methods of string in Python?

<details>

<summary>Notes: Click to expand</summary>

| Method name | Description |
|:------------|:------------|
| ``.isdigit()`` | Returns `True` if all the characters of the strings are digits, else `False` |
| `.strip()` | Removes all leading/trailing whitespaces (space, tabs, newline characters) |
| `.startswith()` | Check if a string starts with a specified prefix |
| `.endswith()` | Check if a string ends with a specified prefix |
| `.replace()` | Replace a substring in a string |

</details>

<details>

<summary>Codes: Click to expand</summary>

```python

# .isdigit()

my_string = "12345"
if my_string.isdigit():
    print("The string contains only digits.")
else:
    print("The string does not contain only digits.")
```

```python

# .strip()

text = "  Hello, World!  "
print(text.strip())   # Output: "Hello, World!"

## Removing specific characters
custom_text = "...Hello..."
print(custom_text.strip('.'))  # Output: "Hello"

```

```python

# .startswith(), .endswith()

filename = "example.txt"
print(filename.startswith("ex"))  # Output: True
print(filename.endswith(".txt"))  # Output: True

url = "https://www.example.com"
print(url.startswith("http"))  # Output: True
print(url.endswith(".org"))    # Output: False

```

```python

# .replace()

my_string = "Hello, world!"
new_string = my_string.replace("world", "Python")
print(new_string)  # Output: Hello, Python!

## Optional third argument
my_string = "apple apple apple apple"
new_string = my_string.replace("apple", "banana", 2)  # Replace only the first 2 occurrences
print(new_string)  # Output: banana banana apple apple

```

</details>

### 23. What are functions in Python? Why are they useful?

<details>

<summary>Notes: Click to expand</summary>

* Functions are **blocks of resuable code** designed to perform a specific task.
* Benefits
    * **Modularity**: Breaks down complex code into small, manageable parts
    * **Reusability**: Write the code once and reuse it again multiple times.
    * **Readability**: Make code easier to understand by giving meaningful names to blocks of code.
    * **Maintainability**: Easier to modify and debug code when its organized into functions.
    * **Abstraction**: Hide the implementation details and expose only the interface.

</details>

### 24. What are local and global variables in Python?

<details>

<summary>Notes: Click to expand</summary>

* Scope of a variable: Region of a code where the variable name is visible and where they can be accessed.

|  | Local Variable | Global Variable |
|:-|:---------------|:----------------|
| Declaration | Inside a function | Outside a function |
| Accessibility | Within the function they are declared | Accessible in the entire script |
| Lifetime | Automatic: Created within a function, destroyed once the function finishes running | Static: Exist from the point they are defined until the end of script's execution |

</details>

<details>

<summary>Codes: Click to expand</summary>

```python

global_var = 10  # Global variable

def my_function():
    local_var = 5  # Local variable
    print(global_var)  # Accessing global variable is allowed
    print(local_var)  # Accessing local variable is allowed

my_function()
print(global_var)  # Accessing global variable is allowed
# print(local_var)  # This will give an error: local_var is not defined outside the function

```

</details>

### 25. What is Scope Resolution in Python?

<details>

<summary>Notes: Click to expand</summary>

* Process by which Python determines which variable a name refers to when there are **multiple variables with the same name in different scopes** (local, global)
* Python follows the **LEGB** rule:
    1. **Local**: Inside the current function.
    2. **Enclosing**: In any enclosing function (if the current function is nested).
    3. **Global**: At the top level of the module.
    4. **Built-in**: In Python's built-in namespace (len, print, range).

</details>

<details>

<summary>Codes: Click to expand</summary>

```python

# G: Global scope
x = "GLOBAL"

def outer():           # E: Enclosing scope  
    x = "ENCLOSING"
    
    def inner():       # L: Local scope
        x = "LOCAL"
        print("Local:", x)      # Finds LOCAL (L)
    
    inner()
    print("Enclosing:", x)     # Finds ENCLOSING (E)

outer()
print("Global:", x)        # Finds GLOBAL (G)

print(len("SAP"))          # Finds len (B - built-in)

```

</details>

### 26. What are the types of functions in Python?

<details>

<summary>Notes: Click to expand</summary>

| Function Type | Description |
|:--------------|:------------|
| Built-in | Predefined functions like len(), print(), range() |
| User-defined | Functions created by the user |
| Lambda Functions | Anonymous, single-expression functions |

</details>

### 27. What is the difference between positional and keyword arguments?

<details>

<summary>Notes: Click to expand</summary>

| Argument Type | Description |
|:--------------|:------------|
| Positional | Args passed to a function based on their _position_ in the function call |
| Keyword | Args passed to a function by explicitly specifying their _paramter name_ along with the _value_. They don't follow order, however, these arguments are to be defined after all the positional arguments have been defined. |

* Golden Rule: Positional arguments **ALWAYS BEFORE** keyword arguments

</details>

<details>

<summary>Codes: Click to expand</summary>

```python

def describe_person(name, age):
    print(f"Name: {name}, Age: {age}")

describe_person("Alice", 30)  # Positional arguments
describe_person(age=30, name="Alice")  # Keyword arguments (order doesn't matter)

# You can also mix them
describe_person("Bob", age=25)  # Positional and keyword mixed.

```

</details>

### 28. What is the ``return`` statement used for?

<details>

<summary>Notes: Click to expand</summary>

* The `return` statement is used to **exit a function** and optionally return value(s) to the caller.
* When a `return` statement is encountered by a function, it stops the execution and the specified value (if explictly mentioned, else None) is returned back to where the function is called / caller. 
* If there is no explicit `return` statement or if the `return` statement exists by itself without a value, the function implicitly returns `None`.

</details>

### 29. What is recursion and can you provide a simple recursive function example?

<details>

<summary>Notes: Click to expand</summary>

* Programming technique where a **function calls itself** within its own definition.
* If there is no base case / condition that can stop the recursiveness, it will lead to infinite recursions causing `StackOverflow` error.

</details>

<details>

<summary>Codes: Click to expand</summary>

```python

def factorial(n):
    if n == 0:  # Base case: factorial of 0 is 1
        return 1
    else:
        return n * factorial(n - 1)  # Recursive call

print(factorial(5))  # Output: 120

```

</details>

### 30. What are *args and **kwargs in Python functions?

<details>

<summary>Notes: Click to expand</summary>

* Both allow you to write flexible and reusable functions that can accept **an arbitrary number of positional and keyword arguments** respectively.
* Golden Rule: *args must come **before** **kwargs.
* `args`: treated as a **tuple** containing all additional positional arguments
* `kwargs`: treated as a **dictionary** where the keys are the arg names and the values are the corresponding values passed to the keys.

</details>

<details>

<summary>Codes: Click to expand</summary>

```python

def example_function(*args, **kwargs):
    print("Args:", args)
    print("Kwargs:", kwargs)

example_function(1, 2, 3, name="Alice", age=25)
# Output:
# Args: (1, 2, 3)
# Kwargs: {'name': 'Alice', 'age': 25}

```

</details>

### 31. What are lambda functions? When are they useful? Also explain the `map` ,`filter`, `reduce` functions.

<details>

<summary>Notes: Click to expand</summary>

* **Small + Simple + 1-Line + Anonymous + Single Expression** functions defined using the ``lambda`` keyword.
* Used for:
    * Arguments to higher-order functions like `map()`, `filter()`, ``sorted`, `reduce()`
    * Simple operations for a quick task
    * Data Science / Machine Learning

</details>

<summary>Codes: Click to expand</summary>

```python

# 1. With map() - Transform datasets (SAP data processing)
numbers = [1, 2, 3, 4, 5]
squared = map(lambda x: x**2, numbers)
print(list(squared))  # [1, 4, 9, 16, 25]

# 2. With filter() - Filter valid data (SAP validation)
orders = [101, -50, 203, 0, 315]
valid_orders = filter(lambda x: x > 0, orders)
print(list(valid_orders))  # [101, 203, 315]

# 3. With sorted() - Custom sorting (SAP reports)
students = [("Alice", 85), ("Bob", 92), ("Charlie", 78)]
by_score = sorted(students, key=lambda x: x[1])
print(by_score)  # [('Charlie', 78), ('Alice', 85), ('Bob', 92)]

# 4. With reduce() - Aggregate (SAP totals) 
from functools import reduce
sales = [100, 150, 200, 75]
total = reduce(lambda x, y: x + y, sales)
print(total)  # 525

# 5. Data Science - Quick column operations
sap_metrics = [85.5, 92.1, 78.9]
normalized = list(map(lambda x: (x - 78.9) / (92.1 - 78.9), sap_metrics))
print(normalized)  # [0.45, 0.94, 0.0]

```

</details>

### 32. What are the differences between modules, packages, libraries and frameworkes 

<details>

<summary>Notes: Click to expand</summary>

| Term | Definition | Size | Examples | Usage |
|:-----|:-----------|:-----|:---------|:------|
| Module | Single .py file with functions/classes | Smallest | math.py, os.py, your_utils.py | import math |
| Package | Directory of modules + __init__.py | Multiple modules | numpy/, pandas/, sklearn/ | from numpy import array |
| Library | Collection of packages/modules for reuse (often synonymous with "package" in casual use) | Multiple packages | NumPy (arrays/ML), Pandas (dataframes), Requests (HTTP) | pip install pandas |
| Framework | Full structure dictating app architecture ("inversion of control") | Largest | Django (web), Flask (micro-web), FastAPI (API) | django-admin startproject |

* **Library**: The user controls the flow -> The user calls the library functions when needed.
* **Framework**: Framework controls the user. It calls the user'S code via callbacks/hooks.

**Quick Test**: 
- If I `import X` and call `X.function()`, → **Library** (NumPy, Pandas)
- If I extend `X.Class` and it calls my methods → **Framework** (Django, Flask)

</details>

### 33. What is the purpose of the ``__init__.py`` file in a package? 

<details>

<summary>Notes: Click to expand</summary>

* The `__init__.py` file is required to make Python treat a directory as a package.
* Even if the `__init__.py` is empty,  the presence of this file allows the user to import modules from the directory.

</details>

### 34. What is the difference between a directory and a package ?

<details>

<summary>Notes: Click to expand</summary>

| Aspect | Directory | Package |
|:-------|:----------|:--------|
| Definition | Regular folder on filesystem | Directory +`` __init__.py`` file |
| Importable? | ❌ No | ✅ Yes |
| Contains | Any files (.py, .txt, images, etc.) | Python modules (.py files) + ``__init__.py`` |
| Purpose | Organize project files | Organize importable Python code |

</details>

### 35. What is namespace in Python? Is it similar to Scope Resolution in Python ?

<details>

<summary>Notes: Click to expand</summary>

* Naming System in Python
* Ensures names are unique and avoids naming conflicts.
* Different namespaces can exist at different scopes (global, local, built-in), allowing you to use the same name for different things without ambiguity.
* Think of it like a filing system; different folders (namespaces) can contain files (objects) with the same name without causing confusion.
* Namespace and Scope Resolution are related but distinct concepts

    | Concept          | Definition                                                   | Analogy                                        |
    |:-----------------|:-------------------------------------------------------------|:-----------------------------------------------|
    | Namespace        | Container that maps names → objects (like a dictionary)      | Phone book: 'x': 42, 'print': <function>       |
    | Scope Resolution | Search algorithm (LEGB rule) to find names across namespaces | 911 operator: Which phone book to check first? |

</details>

### 36. What are lists and tuples? When would you use one over the other?

<details>

<summary>Notes: Click to expand</summary>

* Lists: Mutable + Ordered sequences, []
* Tuples: Immutable + Ordered sequences, ()

* Use
    * Lists
        * Collection of items that can be modified afterwards.
    * Tuples
        * Fixed set of data that should not be changed (coordinates, records)
        * Data Integrity
        * Can be used as keys in dictionaries as they are hashable, unlike lists
        * Iteration over a tuple is generally faster than lists as they are immutable.

</details>

### 37. How do you iterate through a list with indices?

<details>

<summary>Notes: Click to expand</summary>

* Using the `enumerate()` function
* This creates a **counter to the iterable** and returns an enumerate object.

</details>

<details>

<summary>Codes: Click to expand</summary>

```python

my_list = ["apple", "banana", "cherry"]

# Unpacking the tuple into index and item
for index, item in enumerate(my_list):
    print(f"Index: {index}, Item: {item}")

```

</details>

### 38. What is list comprehension? Why is it useful? How can it be compared with lambda function and ``for`` loops?

<details>

<summary>Notes: Click to expand</summary>

* Concise and elegant way to create lists from an existing iterable in a single line.

* List comprehensions are the most Pythonic way to build lists from iterables. Lambda with map/filter can do the same, but comprehensions are usually clearer and preferred for list generation.

    | Feature     | List Comprehension                | Lambda + map/filter                                    |
    |:------------|:----------------------------------|:-------------------------------------------------------|
    | Syntax      | [x*x for x in nums]               | list(map(lambda x: x*x, nums))                         |
    | Readability | Usually clearer                   | Can become noisy for non-trivial logic                 |
    | Typical use | Build lists with transform/filter | When a function object is needed (e.g., passed around) |
    | Conditions  | Built-in if support in same line  | Need separate filter or logic inside lambda            |

* List comprehensions are usually faster than for loops:

    | Aspect        | List Comprehension            | For Loop                                        |
    |:--------------|:------------------------------|:------------------------------------------------|
    | Lines of Code | 1 line                        | 3-5 lines                                       |
    | Purpose       | Create new list from iterable | Any iteration (create lists, modify vars, etc.) |
    | Speed         | Faster (optimized bytecode)   | Slower (lookup + append() calls)                |
    | Readability   | Clean for simple transforms   | Better for complex logic                        |

</details>

### 39. Explain the difference between == and is

<details>

<summary>Notes: Click to expand</summary>

* Both are comparison operators but they check different things:
* `==`:
    * Equality Operator
    * Checks if the **values** of the objects are the **same**.
* `is`:
    * Identity Operator
    * Checks if two variables refer to the **same object** in memory.

</details>

<details>

<summary>Codes: Click to expand</summary>

```python

list1 = [1, 2, 3]
list2 = [1, 2, 3]  # list2 has same values as list1, but is a different object

print(list1 == list2)  # Output: True (values are the same)
print(list1 is list2)   # Output: False (different objects in memory)

list3 = list1  # list3 now refers to the same object as list1

print(list1 == list3)  # Output: True (values are the same)
print(list1 is list3)   # Output: True (same object in memory)

a = 5
b = 5 # For small integers, Python often reuses memory locations
print(a == b) # Output: True
print(a is b) # Output: True (often, but not guaranteed)

c = 257
d = 257 # For larger integers, Python typically creates separate objects
print(c == d) # Output: True
print(c is d) # Output: False

string1 = "hello"
string2 = "hello" # String interning can cause them to point to same memory location
print(string1 == string2) # Output: True
print(string1 is string2) # Output: True (often, but not guaranteed)

```

</details>

### 40. What is the difference between del, remove() and pop() on lists?

<details>

<summary>Notes: Click to expand</summary>

* All are used to delete elements from a list but they work differently:

* `del`: 
    * It can remove an element from a **specific index** or a **slice of elements** or the entire list.
    * It does not return the removed value.
    * del[-1] also removes the last element.
* `remove()`:
    * It removes the **first occurence** of a **specifc value** from the list.
    * If the value is not found in the list -> it raises ``ValueError``.
    * It does not return the removed value.
* `pop()`:
    * It removes the **last element** of the list.
    * It **returns** the removed element.

</details>

<details>

<summary>Codes: Click to expand</summary>

```python

my_list = [10, 20, 30, 20, 40]

my_list.remove(20)  # Removes the first 20
print(my_list)  # Output: [10, 30, 20, 40]

del my_list[1]  # Removes the element at index 1 (30)
print(my_list)  # Output: [10, 20, 40]

del my_list[1:3]  # Removes a slice of elements from index 1 up to (but not including) 3
print(my_list)  # Output: [10]

del my_list # Deletes the whole list
# print(my_list) # This will give NameError now since my_list does not exist anymore.

```

</details>

### 41. What is the difference between a Shallow Copy, Deep Copy and Assignment Reference?

<details>

<summary>Notes: Click to expand</summary>

| Aspect         | Assignment Reference        | Shallow Copy                                   | Deep Copy                                         |
| -------------- | --------------------------- | ---------------------------------------------- | ------------------------------------------------- |
| Definition     | Same object (alias)         | New object, references original inner elements | New object, recursively copies ALL inner elements |
| Method         | a = x                       | copy.copy(), x.copy(), x[:]                    | copy.deepcopy()                                   |
| New Object?    | ❌ No (id(a) == id(x))       | ✅ Yes (id(a) != id(x))                         | ✅ Yes                                             |
| Nested Changes | Identical - same memory     | Shared - inner objects linked                  | Independent - fully isolated                      |
| Memory         | None (just pointer)         | Less (shares inners)                           | Most (copies everything)                          |
| SAP Use Case   | Quick alias, config sharing | Surface copy immutable inners                  | Full data isolation                               |

* 1D lists are "safe" with shallow copy because they contain only immutable primitives (ints, strings). 
* 2D lists have mutable lists as elements, causing shared references.

</details>

<details>

<summary>Codes: Click to expand</summary>

```python

## Aliasing

x = [1,2,3]
a = x
print(id(x)) # 2615566877824
print(id(a)) # 2615566877824

```

```python

## Shallow Copy vs Deep Copy for 1D List

### Shallow Copy
x = [1,2,3]
y = [1,2,3]

a = x.copy()
a[0] = 4
print(x) # [1, 2, 3] <- Unchanged
print(a) # [4, 2, 3]

### Deep Copy
b = copy.deepcopy(x)
b[0] = 4
print(y) # [1, 2, 3] <- Unchanged
print(a) # [4, 2, 3]

```

```python

## Shallow Copy vs Deep Copy for 2D List

### Shallow Copy
x = [[1,2,3]]
y = [[1,2,3]]

a = x.copy()
a[0][0] = 4
print(x) # [4, 2, 3]
print(a) # [4, 2, 3]

### Deep Copy
b = copy.deepcopy(y)
b[0][0] = 4
print(y) # [1, 2, 3] <- Unchanged
print(a) # [4, 2, 3]

```

</details>

### 42. What is the difference between list append() and extend()?

<details>

<summary>Notes: Click to expand</summary>

* Both are used to add elements to the list but they differ in how they add the elements.
* `append()`:
    * Adds a **single element** to the end of the list.
    * The element can be of **any type**.
* `extend()`:
    * Can add **multiple elements** to the end of the list.
    * The elements are of **iterable types** (list, tuple, string).

</details>

### 43. How does the ``zip()`` function work?

<details>

<summary>Notes: Click to expand</summary>

* Takes multiple iterables like lists, tuples, strings as input
* Returns an iterator of tuples.

</details>

<details>

<summary>Codes: Click to expand</summary>

```python

names = ["Alice", "Bob", "Charlie"] # type: list
ages = (30, 25,35) # type: tuple

zipped = zip(names, ages)
print(list(zipped))  # Output: [('Alice', 30), ('Bob', 25), ('Charlie', 35)]

# You can also use zip with more than two iterables:
cities = ["New York", "London", "Paris"]
zipped_multiple = zip(names, ages, cities)
print(list(zipped_multiple))  # Output: [('Alice', 30, 'New York'), ('Bob', 25, 'London'), ('Charlie', 35, 'Paris')]

```

</details>

### 44. How to find the intersection of two lists in Python

<details>

<summary>Notes: Click to expand</summary>

1. Convert both the lists to set using `set()`
2. Use the `&` operator
3. Convert the result back to a list using `list()`

</details>

<details>

<summary>Codes: Click to expand</summary>

```python

a = [1,2,3]
b = [2,3,4]

set_a = set(a)
set_b = set(b)

c = list(set_a & set_b)
print(c) # [2,3]

```

</details>

### 45. Give a short overview of all the Python operators.

<details>

<summary>Notes: Click to expand</summary>

| Category   | Operators                | Description                  | Example                |
|:-----------|:-------------------------|:-----------------------------|:-----------------------|
| Arithmetic | + - * / // % **          | Math operations              | 5 + 3 = 8, 10 // 3 = 3 |
| Assignment | = += -= *= /= //= %= **= | Assign/update values         | x = 5, x += 2          |
| Comparison | == != > < >= <=          | Compare values (return bool) | 5 > 3 → True           |
| Logical    | and or not               | Boolean logic                | True and False → False |
| Identity   | is is not                | Same object?                 | x is None              |
| Membership | in not in                | Element exists?              | 'a' in 'apple'         |
| Bitwise    | & \| ^ ~ << >>           | Binary operations            | 5 & 3 = 1              |

</details>

### 46. What are dictionaries in Python? How do you access values and iterate through a dictionary?

<details>

<summary>Notes: Click to expand</summary>

* Dictionaries are unordered collection of key-value pairs.
* Each key must be unique and immutable.
* Values can be of any type.

</details>

<details>

<summary>Codes: Click to expand</summary>

```python

my_dict = {
    "name":"Ryan Gosling",
    "age": 30
}

my_dict["age"] # 30
my_dict.get("age") # 30
my_dict["full_name"] # KeyError
my_dict.get("full_name", "does not exist") # does not exist

```

```python

my_dict = {"a": 1, "b": 2, "c": 3}

## Keys (default)
for key in my_dict:  # This iterates through the keys by default
    print(key, my_dict[key])

## Keys (Explicit)
for key in my_dict.keys():
    print(key, my_dict[key])

## Values (Explicit)
for value in my_dict.values():
    print(value)

## K:V (Items, Explicit)
for key, value in my_dict.items():
    print(key, value)

```

</details>

### 47. How do you merge two dictionaries in Python?

<details>

<summary>Notes: Click to expand</summary>

1. Using the `dict1.update(dict2)` method.
    * Modifies the original dictionary in place.
2. Using the `dict1 | dict2` operator (Python 3.9+).
    * Concise syntax for creating a new merged dictionary.
3. Using the `{**dict1, **dict2}` operator (Python 3.5+).
    * More flexible and good for merging multiple dictionaries.

</details>

<details>

<summary>Codes: Click to expand</summary>

```python

# 1. Using the update() method

dict1 = {"a": 1, "b": 2}
dict2 = {"c": 3, "d": 4, "a": 5}  # "a" key is present in both

dict1.update(dict2)  # dict1 is modified in place
print(dict1)  # Output: {'a': 5, 'b': 2, 'c': 3, 'd': 4}

```

```python

# 2. Using the | operator (Python 3.9+)

dict1 = {"a": 1, "b": 2}
dict2 = {"c": 3, "d": 4, "a": 5}

merged_dict = dict1 | dict2  # Creates a new dictionary

print(merged_dict)  # Output: {'a': 5, 'b': 2, 'c': 3, 'd': 4}
print(dict1) # Output: {'a': 1, 'b': 2} (dict1 is not changed)

```

```python

# 3. Using the ** operator (Python 3.5+)

dict1 = {"a": 1, "b": 2}
dict2 = {"c": 3, "d": 4, "a": 5}

merged_dict = {**dict1, **dict2}  # Creates a new dictionary

print(merged_dict)  # Output: {'a': 5, 'b': 2, 'c': 3, 'd': 4}
print(dict1) # Output: {'a': 1, 'b': 2} (dict1 is not changed)

dict3 = {"e": 6, "f": 7}
merged_multiple = {**dict1, **dict2, **dict3}
print(merged_multiple)  # Output: {'a': 5, 'b': 2, 'c': 3, 'd': 4, 'e': 6, 'f': 7}

```

</details>

### 48. What are sets in Python? What are they typically used for?

<details>

<summary>Notes: Click to expand</summary>

* Sets in Python are unordered collection of unique elements.
* Duplicate values are automatically removed.

* Used for:
    * Removing duplicates.
    * Membership testing: in/not in
    * Set Operations: Union (|), intersection (&), difference (-)

</details>

<details>

<summary>Codes: Click to expand</summary>

```python

my_set = {1, 2, 2, 3, 4, 4, 5}  # Duplicates are removed
print(my_set)  # Output: {1, 2, 3, 4, 5}

my_list = [1,2,2,3,4,4,5]
unique_list = list(set(my_list)) #remove duplicates from a list
print(unique_list) # Output: [1, 2, 3, 4, 5]

set1 = {1, 2, 3}
set2 = {3, 4, 5}

print(set1 | set2)  # Union: {1, 2, 3, 4, 5}
print(set1 & set2)  # Intersection: {3}
print(set1 - set2)  # Difference: {1, 2}

```

</details>

### 49. What is the difference between ``//`` and ``/`` in Python?

<details>

<summary>Notes: Click to expand</summary>

* `/`: Standard Division, returns float
* `//`: Floor Division, returns int

</details>

### 50. What is exception handling in Python? Describe the `try-except` blockk,  `finally` clause and `else` clause.

<details>

<summary>Notes: Click to expand</summary>

* Mechanism to deal with errors/exceptions that occur during the execution of a program.
* Gracefully manage theese exceptions + prevents the program from crashing + recovery handle

* ``try-except`` block:
    *  Put the code that can cause the exception in the try block.
    * Except block handles the exception if occured.

* `finally` clause:
    * Optional part of the `try-except` block.
    * Code within this clause **always executes**, regardless of whether an exception was raised or not.
    * Used for:
        * Cleanup tasks (closing files, releasing resources)
        * Ensuring certain actions are always performed.

* `else` clause:
    * Optional part of the `try-except` block.
    * Code within this clause executes **only when** there are **no exceptions** in the try block.

</details>

<details>

<summary>Codes: Click to expand</summary>

```python

# try-except

try:
    result = 10 / 0  # This will raise a ZeroDivisionError
    print(result) # This will not be executed
except ZeroDivisionError:
    print("Cannot divide by zero!")  # Handle the error
except TypeError: # you can add multiple except blocks
    print("Type error occurred")
except Exception as e: # generic exception block to catch any type of error. Should be used with caution.
    print(f"An error occurred: {e}")

print("Program continues...")  # The program doesn't crash

```

```python

# finally clause

try:
    f = open("my_file.txt", "r")
    #... process the file...
except FileNotFoundError:
    print("File not found.")
finally:
    if 'f' in locals() and not f.closed: # check if f is defined and file is not closed
        f.close()  # Close the file, even if there was an error
    print("File operation complete.")

```

```python

# else clause

try:
    file = open("sap_config.txt", "r")      # Risky operation
except FileNotFoundError:
    print("Config file missing!")
else:
    # Runs ONLY if no exception
    data = file.read().strip()
    print(f"Processed {len(data)} chars")
finally:
    # ALWAYS runs (cleanup)
    file.close()
    print("File closed ✓")

```

</details>

### 51. What are some common built-in exceptions in Python?

<details>

<summary>Notes: Click to expand</summary>

| Built in Exception | Description |
|:-------------------|:------------|
| ZeroDivisionError | Raised when dividing by zero. |
| TypeError | Raised when an operation is performed on incompatible types. | 
| ValueError | Raised when a function receives an argument of the correct type but an inappropriate value. |
| FileNotFoundError | Raised when a file or directory is1 not found. | 
| IndexError | Raised when trying to access an index that is out of range for a sequence (like a list). |
| KeyError | Raised when trying to access a key that does not exist in a dictionary. |
| IOError | Raised when an input/output operation fails (e.g., reading or writing a file). |
| ImportError | Raised when a module cannot be imported. |
| NameError | Raised when you try to use a variable that has not been defined. |

</details>

### 52. How can you optimize nested loops for performance?

<details>

<summary>Notes: Click to expand</summary>

* List Comprehensions if possible.
* Built-in functions like `map, filter, reduce, sum, any` if possible.
* Cache repeated calculations outside the loop.

</details>

### 53. What are some common errors with loops in Python?

<details>

<summary>Notes: Click to expand</summary>

* **Infinite Loops**: no based conditions in while loops.
* **Index Errors**: Accessing out-of-range indices in sequences.
* **Logic Errors**: Misplaced conditions or incorrect loop termination logic.
* **Unintended breaks**: Accidental usage of `break` and/or `continue` incorrectly.

</details>

### 54. When can infinite loops be useful in Python ? How to break an infinite loop ?

<details>

<summary>Notes: Click to expand</summary>

* Use `while True` for infinite loops.

* Uses:
    * Servers: Listens to incoming requests continuously.
    * Polling: Repeatedly checking for certain conditions or events.
    * Interactive Systems: Waiting for user input until explicitly terminated.

* To break the infinite loop:
    * Ensure the loop condition becomes ``False`` at some point.
    * Use **debugging** or print statements to check the loop’s progress.
    * Use ``break`` statements where applicable.

</details>

### 55. How to loop backwards in Python?

<details>

<summary>Notes: Click to expand</summary>

1. Use `reversed(iterable like range, list)`
2. Use `range(start, stop, -1)`

</details>

<details>

<summary>Codes: Click to expand</summary>

```python

for i in reversed(range(5)):
    print(i)  # Outputs: 4, 3, 2, 1, 0

```

```python

for i in range(4, -1, -1):
    print(i)  # Outputs: 4, 3, 2, 1, 0

```

</details>

### 56. What is a generator loop? How is it different from a normal loop and an iterator ? Explain `yield`, `next` and `iter` ?

<details>

<summary>Notes: Click to expand</summary>

* The real difference lies in the memory:
    * Iterator -> lowest
    * Generator -> Less than Loops
    * Loops -> Maximum memory

* Iterator:
    * Access items in a sequence one at a time.
    * It does not load the entire data at once.
    * Lazy Evaluation: Gives one value when asked saving memory.
    * Object with __iter__() and __next__() methods.
    * Foundation - for loops and generators use this protocol.
* Generator:
    * Another way of creating iterators but simple.
    * Generator function uses a generator function or generator expressions to **yield values one at a time**.
    * Uses the `yield` keyword, optionally using `next` keyword.
    * This allows for efficient memory usage, particularly with large or infinite datasets, because the entire sequence is not stored in memory simultaneously (**lazy evaluation**). 
* Loop:
    * Traditional for/while loops that process items completely.
    * Builds full lists in memory ([x**2 for x in range(1000)]).
    * Fast for small data, slow for millions of items.

</details>

<details>

<summary>Codes: Click to expand</summary>

```python

# 1. Generator Function using yield

def count_up_to(max_value):
    current = 1
    while current <= max_value:
        yield current  # Pauses the function and yields a value
        current += 1

# Using the generator function
counter = count_up_to(5)
for number in counter:
    print(number)

# Using next() with a generator function object
print(next(my_generator)) # Output: 1 
print(next(my_generator)) # Output: 2
print(next(my_generator)) # Output: 3

```

```python

# 2. Generator Expression

squares = (x * x for x in range(1, 6))

# Using the generator expression
for num in squares:
    print(num)

# Using next() with a generator expression
print(next(squares_gen)) # Output: 0
print(next(squares_gen)) # Output: 1

```

```python

# 3. Iterator

l = iter(['Geeks', 'For', 'Geeks'])
print(next(l))
print(next(l))
print(next(l))

```

```python

# 4. Memory Difference between the three

import sys

# Normal loop → 40MB!
full_list = [x for x in range(1000000)]
print("List:", sys.getsizeof(full_list), "bytes")  # ~40MB

# Iterator → 48 bytes!
it = iter(range(1000000))
print("Iterator:", sys.getsizeof(it), "bytes")  # 48 bytes

# Generator → 120 bytes!
def gen():
    for i in range(1000000): yield i
g = gen()
print("Generator:", sys.getsizeof(g), "bytes")  # 120 bytes

```

</details>

