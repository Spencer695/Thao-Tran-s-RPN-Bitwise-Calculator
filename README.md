# RPN Calculator with Bitwise Operations

A C++ expression evaluator for Reverse Polish Notation, supporting both arithmetic
and bitwise operations.

## What it does

Reverse Polish Notation places operators after their operands, so `3 4 +` means
`3 + 4`. This removes the need for parentheses and makes expressions straightforward
to evaluate with a stack: operands are pushed on, and each operator pops the values
it needs and pushes back the result.

## Supported operations

| Type | Operators |
|---|---|
| Arithmetic | `+`  `-`  `*`  `/` |
| Bitwise | `AND`  `OR`  `XOR` |
| Shifts | left shift, right shift |

## Input validation and safety

Several operations have inputs that are invalid or undefined in C++, and each is
checked before the operation runs rather than after it fails:

- **Integer overflow** — arithmetic that would exceed the range of the type is caught
  instead of silently wrapping around.
- **Out-of-range shift amounts** — shifting by a negative amount, or by more bits than
  the type holds, is undefined behavior in C++ and is rejected.
- **Malformed expressions** — operators without enough operands, and division by zero,
  are reported rather than crashing.

## Testing

Expressions and their expected results are stored in a CSV file. An automated test
runner evaluates every expression and compares the output against the expected value,
so the full suite re-runs after any change to the evaluator.

## Building and running

```bash
[your build command, e.g. g++ -std=c++17 -o rpn main.cpp]
[your run command, e.g. ./rpn]
```



