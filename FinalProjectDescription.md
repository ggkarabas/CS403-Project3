# DumPy: A Practical Overview

## Introduction to DumPy

DumPy is a programming language inspired by Python, designed to enforce best practices and simplify the process of writing clear, well-documented code. DumPy combines elements of Python’s easy readability with additional constraints that encourage structured programming. The goal is to offer developers a language that is flexible but disciplined, making it easier to maintain code over time.

This guide will cover DumPy’s syntax, key features, and grammar, providing insight into its underlying design philosophy and practical examples of how to use it.

## Getting Started: Writing Your First DumPy Program

The traditional way to begin exploring a new language is with a "Hello, World!" program. In DumPy, it is written like this:

```dumpy
# Prints 'Hello, World!' to the console
echo("Hello, World!")
```

Unlike other languages that require importing core libraries, DumPy provides built-in functions for common tasks like printing to the console. The above example shows how simple it is to get started with DumPy—no setup overhead is needed to begin writing functional code.

## Variables and Constants

DumPy uses `var` for declaring variables and `let` for constants. Constants are immutable, whereas variables can be modified after their initial declaration:

```dumpy
var count = 10
count = 15  # 'var' values are mutable
let maxLimit = 50  # Immutable value
```

DumPy uses type inference, but you can explicitly specify types when you want to add extra clarity or constraint:

```dumpy
let price: Float = 19.99
var productName: String = "DumPy Notebook"
```

### Type Safety

One of DumPy's principles is type safety. Functions require explicit type annotations for parameters and return values, ensuring that the purpose and expected inputs/outputs are clear:

```dumpy
# Function to calculate the product of two integers
func multiply(a: Integer, b: Integer) -> Integer:
    return a * b
```

This constraint not only documents the function’s behavior but also catches potential errors early, reducing debugging time.

## Working with Collections

DumPy includes robust support for working with collections like lists and dictionaries, which can be created and manipulated with simple syntax:

```dumpy
# A list of colors
var colors = ["red", "green", "blue"]
colors[1] = "yellow"  # Replaces 'green' with 'yellow'

# A dictionary of book titles
var books = {
    "1984": "George Orwell",
    "Dune": "Frank Herbert"
}
books["Brave New World"] = "Aldous Huxley"
```

You can also define empty lists and dictionaries with explicit types:

```dumpy
let emptyList: [String] = []
let emptyDict: [String: Integer] = {}
```

## Control Flow

Control flow in DumPy is handled using common structures like `if`, `elif`, and `else`. DumPy’s syntax emphasizes readability:

```dumpy
var score = 82
if score >= 90:
    echo("Excellent!")
elif score >= 70:
    echo("Good effort!")
else:
    echo("Needs improvement.")
```

Loops are also straightforward. DumPy supports `for` loops for iteration and `while` loops for repeating actions while a condition is true:

```dumpy
# Using a for loop to calculate the sum of the first 5 integers
var total = 0
for i in range(5):
    total += i
echo(total)  # Outputs 10

# Halving a number until it falls below 2
var num = 64
while num > 2:
    num /= 2
echo(num)  # Outputs 2
```

## Functions and Procedures

Functions are a core part of DumPy. Defined using the `func` keyword, functions must be documented and include type annotations to define inputs and outputs clearly:

```dumpy
# Function that greets a user
func greetUser(username: String) -> String:
    return "Welcome, " + username
```

Functions can be nested or passed as arguments to other functions, supporting functional programming styles as well.

## Object-Oriented Features

DumPy also allows developers to encapsulate data and behavior using classes:

```dumpy
# Represents a geometric shape
class Shape:
    var sides: Integer

    # Constructor to initialize the number of sides
    func init(sides: Integer):
        self.sides = sides

    # Method to describe the shape
    func description() -> String:
        return "This shape has " + String(self.sides) + " sides."
```

Classes in DumPy make it easy to organize code logically, encouraging reuse and modular development.

## Error Handling and Debugging

One of DumPy's key philosophies is to provide clear, helpful error messages that facilitate quick debugging:

```dumpy
func divide(a: Integer, b: Integer) -> Integer:
    return a / b  # Error: Missing spaces around operator '/'
```

### Example Error Message:
```
Line 2: Syntax error - Missing spaces around operator '/'
```

These error messages are designed to be precise and easy to understand, guiding developers towards effective solutions.

## Formatting Rules

To enforce consistent, readable code, DumPy has strict formatting requirements:

- **Spaces around operators**: Operations like `x + y` must include spaces for clarity.
- **Readable Numbers**: Large numbers should be formatted using underscores.

```dumpy
let population = 1_000_000  # One million
```

## Indentation and Whitespace

DumPy mandates using 4 spaces for indentation. This rule ensures that all code is formatted uniformly, making it easier to read and maintain. Unlike many other languages, inconsistent indentation will result in a syntax error.

## Grammar and Language Structure

The grammar of DumPy defines how statements, expressions, and blocks are structured.

### Program Structure
A DumPy program is composed of a series of statements, functions, and classes, each following strict syntax rules:

```dumpy
program       : (function | class | statement)* NEWLINE
```

### Statements and Expressions
```dumpy
statement     : assignment | if_statement | for_statement | while_statement | expression | echo_statement
assignment    : (NAME | CONSTANT) EQUALS expression
if_statement  : IF SPACE expression COLON INDENT statement DEDENT (elif_statement | else_statement)?
elif_statement: ELIF SPACE expression COLON INDENT statement DEDENT
else_statement: ELSE COLON INDENT statement DEDENT
for_statement : FOR SPACE NAME IN expression COLON INDENT statement DEDENT
while_statement: WHILE SPACE expression COLON INDENT statement DEDENT
expression    : (expression (PLUS | MINUS | TIMES | DIVIDE | MOD | POWER) expression) | ... | BOOLEAN
```

### Function Definitions

Functions in DumPy are defined with clear, strict syntax to ensure consistency across codebases:

```dumpy
function      : (LINECOMMENT | BLOCKCOMMENT) FUNC SPACE NAME LPAREN parameters RPAREN COLON INDENT statement DEDENT
parameters    : (NAME COLON type (COMMA NAME COLON type)*)?
type          : STRING | INTEGER | FLOAT | BOOLEAN | NAME
```

### Classes

Classes contain attributes and methods, each defined in a clear, readable manner:

```dumpy
class         : (LINECOMMENT | BLOCKCOMMENT) CLASS SPACE NAME COLON INDENT (attribute | method)* DEDENT
attribute     : NAME COLON type
method        : function
```

### Tokens and Keywords

DumPy uses several types of tokens to define the components of the language:

- **Keywords**: Reserved words like `if`, `for`, `while`, `func`, `class`, which are essential parts of the language.
- **Literals**: Representations of values such as `NAME`, `CONSTANT`, `NUMBER`, `STRING`, `BOOLEAN`.
- **Comments**: Both single-line (`#`) and block comments (`'''` or `"""`).
- **Operators**: Arithmetic and comparison operators such as `+`, `-`, `*`, `/`, `==`, `!=`, etc.
- **Whitespace Control**: Enforced by tokens such as `INDENT` and `DEDENT` to maintain readability.

## Extensions and Future Directions

### DumPy Linter
Adding a linter for DumPy would provide instant feedback on code quality, helping developers catch style violations before they become an issue.

### DumPy Transpiler to Python
A DumPy-to-Python transpiler could help bridge the adoption gap by converting DumPy code into Python. This would allow DumPy to take advantage of the vast Python ecosystem while retaining its unique features.

### IDE Integration
Creating IDE plugins for DumPy would enable auto-formatting, syntax highlighting, and other conveniences to enhance the coding experience.

## Full Example Program

Below is an example of a complete DumPy program that demonstrates many of the features discussed above:

```dumpy
# Adds two numbers
func add(a: Integer, b: Integer) -> Integer:
    return a + b

# Represents a counter object
class Counter:
    var count: Integer = 0

    # Increases the counter by a specified value
    func increment(by: Integer):
        self.count += by

# Main program logic
let num1 = 8
let num2 = 7
var counter = Counter()

echo("The result of addition is: " + String(add(num1, num2)))  # Outputs 'The result of addition is: 15'
counter.increment(by: 5)
echo("Current counter value: " + String(counter.count))  # Outputs 'Current counter value: 5'
```

# Implementing DumPy as a Programming Language

Creating DumPy as a programming language is achievable, though it requires careful planning and significant development effort. Below is an outline to guide the process.

---

## 1. Define the Grammar (Parser)
- Use a parser generator like [ANTLR] or Python's `ply`.
- Translate DumPy's grammar rules into a formal grammar recognized by your chosen tool.

---

## 2. Implement a Lexer
- Define tokens for:
  - Keywords
  - Operators
  - Literals
  - Other syntactic elements
- Use tools like `ply` or ANTLR to tokenize DumPy source code.

---

## 3. Develop a Compiler or Interpreter
- **Option 1**: Write an interpreter to execute DumPy code directly.
- **Option 2**: Build a compiler that transpiles DumPy into Python or bytecode for a custom virtual machine.
- Start with a simple interpreter using Python for rapid prototyping.

---

## 4. Integrate a Type Checker
- Implement static type checking to enforce DumPy’s type safety principles.
- Use Abstract Syntax Trees (ASTs) to validate:
  - Function signatures
  - Variable types
  - Return values

---

## 5. Build a Standard Library
- Provide built-in functions (`echo`, `range`, etc.) and common data structures (lists, dictionaries).
- Ensure consistency with DumPy's philosophy of simplicity and clarity.

---

## 6. Error Handling
- Create clear, precise error messages for syntax and runtime errors.
- Use descriptive messages to guide developers toward solutions.

This comprehensive guide has introduced the fundamental concepts of DumPy, from variables and collections to control flow, functions, and object-oriented programming. DumPy’s design philosophy prioritizes clear, maintainable code, and this is reflected throughout its grammar and syntax. By enforcing best practices, DumPy helps developers write code that is clean, understandable, and easy to debug.

# Tokens

## Literals
- **NAME**: Variable name for dynamic variables. Enforces snake_case or camelCase but can only use one in a single program.
- **CONSTANT**: Constant name for static variables. Enforces the use of all caps for constants with underscores.
- **NUMBER**: Integer or float. Enforces the use of underscores for large numbers.
  - **INTEGER**: Integer. Enforces the use of underscores for large numbers and no decimal points.
  - **FLOAT**: Float. Enforces the use of underscores for large numbers and can only have one decimal point.
- **STRING**: String. Enforces the use of double quotes or single quotes.
- **BOOLEAN**: Boolean. Enforces the use of `True` or `False`.
- **INDENT**: Indentation. Enforces the use of 4 spaces.
- **DEDENT**: Dedentation. Enforces the use of 4 spaces.
- **LINECOMMENT**: Line comment. Enforces the use of `#` for line comments.
- **BLOCKCOMMENT**: Block comment. Enforces the use of `'''` or `"""` for block comments.
- **SPACE**: Space. Enforces the use of spaces.

## Keywords
- **if**: If statement. Checks if a condition is true.
- **elif**: Else if statement. Checks condition if the previous `if` and `elif` statements are false.
- **else**: Else statement. Executes if all previous `if` and `elif` statements are false.
- **for**: For loop. Loops through a list or iterable.
- **while**: While loop. Loops while a condition is true.
- **break**: Break statement. Breaks out of a loop.
- **continue**: Continue statement. Skips the current iteration of a loop.
- **pass**: Pass statement. Does nothing.
- **True**: True value. Represents true or 1.
- **False**: False value. Represents false or 0.
- **func**: Function definition.
- **None**: Represents no value.
- **return**: Returns a value from a function.
- **in**: Checks if a value is in a list or iterable.
- **and**: Checks if two conditions are true.
- **or**: Checks if one of two conditions is true.
- **not**: Checks if a condition is false.
- **is**: Checks if a value is the same class/object.
- **String**: Class type for strings.
- **Integer**: Class type for integers.
- **Float**: Class type for floats.
- **Boolean**: Class type for booleans.
- **class**: Defines a class.
- **global**: Defines a global variable.
- **print**: Prints a value to the console.

## Characters
- **LPAREN**: `(` Left parenthesis.
- **RPAREN**: `)` Right parenthesis.
- **LBRACE**: `{` Left brace.
- **RBRACE**: `}` Right brace.
- **LBRACKET**: `[` Left bracket.
- **RBRACKET**: `]` Right bracket.
- **COMMA**: `,` Comma.
- **DOT**: `.` Dot.
- **COLON**: `:` Colon.
- **SEMICOLON**: `;` Semicolon.
- **PLUS**: `+` Plus.
- **MINUS**: `-` Minus.
- **TIMES**: `*` Times.
- **DIVIDE**: `/` Divide.
-- **MOD**: `%` Modulus.
- **POWER**: `**` Power.
- **EQUALS**: `=` Equals.
- **EQ**: `==` Equal to.
- **NE**: `!=` Not equal to.
- **LT**: `<` Less than.
- **LE**: `<=` Less than or equal to.
- **GT**: `>` Greater than.
- **GE**: `>=` Greater than or equal to.

## Grammar

### Program
```dumpy
program : (function | class | statement | NEWLINE)*
```

### Statements
```dumpy
statement : assignment | if_statement | for_statement | while_statement | expression | print_statement
assignment : (NAME | CONSTANT) EQUALS (expression | STRING | NUMBER | BOOLEAN)
```

### Control Flow
```dumpy
if_statement : IF SPACE expression COLON INDENT statement DEDENT (elif_statement | else_statement)?
elif_statement : ELIF SPACE expression COLON INDENT statement DEDENT (elif_statement | else_statement)?
else_statement : ELSE COLON INDENT statement DEDENT
```

### Loops
```dumpy
for_statement : FOR SPACE NAME SPACE IN SPACE expression COLON INDENT statement DEDENT
while_statement : WHILE SPACE expression COLON INDENT statement DEDENT
```

### Expressions
```dumpy
expression : (expression (PLUS | MINUS | TIMES | DIVIDE | MOD | POWER) expression) | (expression (EQ | NE | LT | LE | GT | GE) expression) | (expression (AND | OR) expression) | (NOT expression) | (expression IS expression) | (LPAREN expression RPAREN) | (NAME | CONSTANT) | (NUMBER | STRING | BOOLEAN)
```

### Print Statement
```dumpy
print_statement : PRINT SPACE expression
```

### Function Definitions
```dumpy
function : (LINECOMMENT | BLOCKCOMMENT) FUNCTION SPACE NAME LPAREN parameters RPAREN COLON INDENT statement DEDENT
parameters : (NAME COLON SPACE type (COMMA SPACE NAME COLON SPACE type)*)?
type : STRING | INTEGER | FLOAT | BOOLEAN | NAME
```

### Classes
```dumpy
class : (LINECOMMENT | BLOCKCOMMENT) CLASS SPACE NAME COLON INDENT (attribute | method | statement)* DEDENT
attribute : NAME COLON SPACE type
method : FUNCTION SPACE NAME LPAREN parameters RPAREN COLON INDENT statement DEDENT
```

This concludes the detailed overview of DumPy's grammar, syntax, and language structure. The rules and guidelines provided help ensure that code written in DumPy is clean, maintainable, and understandable. As DumPy continues to evolve, new features and extensions will be developed to further enhance the language, while staying true to its core philosophy of simplicity and structured programming.

