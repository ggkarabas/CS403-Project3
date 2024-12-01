# DumPy: Enforcing Good Programming Practices

## Introduction

DumPy is a Python-inspired programming language designed to enforce good programming practices through strict grammar rules. It aims to improve code readability and maintainability by requiring clear documentation, consistent formatting, and type-safe constructs. The language targets developers who value disciplined coding without sacrificing the flexibility of Python.

## Key Features

- **Type Hinting**:
  - Functions and classes must use type hints for parameters and return types.
  - Variables remain dynamically typed but require explicit hints in function/class contexts.

- **Naming Conventions**:
  - Variable names must follow either `snake_case` or `camelCase`, but not both in a single program.
  - Constants must use `ALL_CAPS` with underscores.

- **Mandatory Comments**:
  - Every function and class definition must be preceded by a single-line or block comment describing its purpose.
  - The first comment encountered before the definition is associated with it.

- **Enforced Formatting**:
  - Large numbers must use underscores for readability (e.g., `1_000_000`).
  - Operators must have spaces between operands (e.g., `a + b` instead of `a+b`).

- **Indentation**:
  - The language strictly uses 4 spaces for indentation, rejecting tabs or inconsistent spacing.

- **Error Handling**:
  - DumPy provides detailed error messages for rule violations, helping developers correct issues easily.

## Tokens

The token definitions remain largely the same but are refined to account for edge cases and compliance:

### Updated Literals

- `NAME`         | Variable names for dynamic variables (`snake_case` or `camelCase`)
- `CONSTANT`     | Constant names, enforcing `ALL_CAPS` with underscores
- `NUMBER`       | Enforces underscores for large numbers
- `STRING`       | Double or single-quoted strings
- `BOOLEAN`      | `True` or `False`
- `LINECOMMENT`  | Single-line comments starting with `#`
- `BLOCKCOMMENT` | Multi-line comments enclosed in `'''` or `"""`

### Keywords

`if`, `elif`, `else`, `for`, `while`, `func`, `class`, etc.

### Operators

- `PLUS`         | `+`
- `MINUS`        | `-`
- `TIMES`        | `*`
- `DIVIDE`       | `/`
- `MOD`          | `%`
- `POWER`        | `**`
- `EQUALS`       | `=`
- `EQ`, `NE`, `LT`, `LE`, `GT`, `GE` | Comparison operators

### Formatting

- `INDENT`       | Enforces 4 spaces
- `DEDENT`       | Enforces 4 spaces
- `SPACE`        | Enforces spaces between operators

## Grammar

### Program Structure

