# Python Notes

Python is a dynamicly typed, though fast general purpose programming language. Python is commonly used in the areas of Data Analysis, Machine Learning, Web Development, Scripting, Automation.

The things that makes Python standout from other languages are that relative readability over perl, cross-platform compatibitily, support for procedural, object-oriented, and functional programming.

### Virtual Env

In Python development, it's traditional to create a virtual environment to install pip packages into for each app you're working on instead of installing everything globabally which would lead to dll hell.  The below commands will create a brand new virtual env and subsequently activate it.  

```bash
python -m venv .env
source .env/bin/activate
# For window use this instead :)
# .\.env\Scripts\activate
```

### How to Run a Simple Hello World

(hello.py)
```python
def main(msg):
  print(msg)

main("Hello World!")
```

To run the program, issue this terminal command `python hello.py`.

### How to Manage Dependencies

Python uses a package manager called pip to manage dependencies. To install a package, simply type `pip install package-name`.

A `requirements.txt` file is typically used in Python projects to list all pip dependencies and their desired version.

(requirements.txt)
```
numpy==1.21.0
pandas==1.3.0
matplotlib==3.4.2
```

To install all dependencies listed in the `requirements.txt` file, use:

```
pip install -r requirements.txt
```


### How to debug on the Command Line

Python provides a built-in debugger called pdb. To use it, import the module and call pdb.set_trace() where you want to start debugging. For example:

```python
import pdb

def buggy_function():
    pdb.set_trace()
    # Some buggy code here

buggy_function()
```

When you run this code, the program will stop at the point where pdb.set_trace() is called. You can then inspect variables, step through the code, etc.

#### PDB Commands

- n(ext): Execute the next line within the current function. If the next line is a function call, it will not step into that function, but instead step over it.
- s(tep): Similar to `next`, but will step into a function call. This allows you to debug the internals of functions.
- c(ontinue): Continue execution until a breakpoint is encountered.
- l(ist): Display the portion of the source code where you currently are. Useful for reminding yourself of the code context.
- p(rint) [expression]: Evaluate the expression and print its value. This is useful to inspect variable or object values.
- pp [expression]: Pretty-prints the value of the expression.
- b(reak) [([filename:]lineno | function) [, condition]]: Set a new breakpoint. If a filename and line number are given, break there. If a function is specified, break at the first executable line within that function. If a condition is specified, set a conditional breakpoint.
- clear [([filename:]lineno | bpnumber [bpnumber …])]: With a line number argument, clear all the breakpoints at this line. With a breakpoint number, clear that breakpoint. If no argument is given, clear all breaks.
- a(rgs): Print the argument list of the current function.
- j(ump) lineno: Set the next line that will be executed. Only available in the bottom-most frame. This lets you skip part of your code.
- q(uit): Quit the debugger and exit.

#### Tips for inspecting objects

```
mystery_object = "pretend you don't know what this object is"

# Get type
type(mystery_object)

# Get attributes and methods
dir(mystery_object)

# Print the documentation on the object
help(mystery_object)

# Get the length
len(outputs)
```

### Classes and Testing

Here's a simple hello world script with a class along with a separte test file.

(calculator.py)
```
class Calculator:
    def add(self, a, b):
        return a + b

    def subtract(self, a, b):
        return a - b

    def multiply(self, a, b):
        return a * b

    def divide(self, a, b):
        if b != 0:
            return a / b
        else:
            raise ValueError("Cannot divide by zero!")
```

(test_calculator.py)
```
import unittest
from calculator import Calculator

class TestCalculator(unittest.TestCase):
    def setUp(self):
        self.calculator = Calculator()

    def test_add(self):
        self.assertEqual(self.calculator.add(5, 7), 12)

    def test_subtract(self):
        self.assertEqual(self.calculator.subtract(10, 5), 5)

    def test_multiply(self):
        self.assertEqual(self.calculator.multiply(3, 7), 21)

    def test_divide(self):
        self.assertEqual(self.calculator.divide(10, 2), 5)

    def test_divide_by_zero(self):
        with self.assertRaises(ValueError):
            self.calculator.divide(10, 0)

if __name__ == '__main__':
    unittest.main()
```

To test, you can run `python test_calculator.py` but I'll need to research more elaborate testing frameworks in the next section.  
