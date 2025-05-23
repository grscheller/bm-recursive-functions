# Boring Math Library - Recursive functions

The purpose of this project is to explore different ways to efficiently
implement recursive functions in Python.

## Repos and Documentation

### Repositories

- [bm.recursive-functions][1] project on *PyPI*
- [Source code][2] on *GitHub*

### Detailed documentation

- [Detailed API documentation][3] on *GH-Pages*

## Overview

- Recursive functions
  - [Ackermann Function](#ackermanns-function)
  - [Fibonacci Sequences](#fibonacci-sequences)
- CLI applications
  - [Ackermann CGI programs](#ackermann-cli-programs)

This project is part of the [Boring Math][4] **bm.** namespace project.

### Recursive functions

Computable recursive functions can be defined with previously defined or not yet
defined values. Functions defined using previously defined values having
"base cases" are called "primitively recursive functions." Not all
computable functions are primitively recursive.

#### Ackermann's Function

- Function **ackermann_list**(m: int, n: int) -> int
  - is a total computable function that is not primitive recursive
  - becomes numerically intractable after `m=4`
  - see [CLI section](#ackermann-cli-programs) below for a mathematical definition

#### Fibonacci Sequences

- Function **fibonacci**(f0: int=0, f1: int=1) -> Iterator[int]

  - returns a *Fibonacci* sequence iterator where
    - `f(0) = f0` and `f(1) = f1`
    - `f(n) = f(n-1) + f(n-2)`
  - yield defaults to `0, 1, 1, 2, 3, 5, 8, 13, 21, ...`

- Function **rev_fibonacci**(f0: int=0, f1: int=1) -> Iterator[int]

  - returns a *Reverse Fibonacci* sequence iterator where
    - `rf(0) = f0` and `rf(1) = f1`
    - `rf(n) = rf(n-1) - rf(n-2)`
      - `rf(0) = fib(-1) = 1`
      - `rf(1) = fib(-2) = -1`
      - `rf(2) = fib(-3) = 2`
      - `rf(3) = fib(-4) = -3`
      - `rf(4) = fib(-5) = 5`
  - yield defaults to `1, -1, 2, -3, 5, -8, 13, -21, ...`

______________________________________________________________________

## CLI Applications

Implemented in an OS and package build tool independent way via the
project.scripts section of pyproject.toml.

### Ackermann CLI programs

Ackermann, a student of Hilbert, discovered early examples of totally
computable functions that are not primitively recursive.

A [fairly standard][5] definition of the Ackermann function is
recursively defined for `m,n >= 0` by

```
    ackermann(0,n) = n+1
    ackermann(m,0) = ackermann(m-1,1)
    ackermann(m,n) = ackermann(m-1, ackermann(m, n-1))
```

#### CLI program **ackermann_list**

- Given two non-negative integers, evaluates Ackermann's function
- Implements the recursion via a Python array
- **Usage:** `ackerman_list m n`

______________________________________________________________________

[1]: https://pypi.org/project/bm.recursive-functions/
[2]: https://github.com/grscheller/bm-recursive-functions/
[3]: https://grscheller.github.io/boring-math-docs/recursive-functions/
[4]: https://github.com/grscheller/boring-math-docs
[5]: https://mathworld.wolfram.com/AckermannFunction.html
