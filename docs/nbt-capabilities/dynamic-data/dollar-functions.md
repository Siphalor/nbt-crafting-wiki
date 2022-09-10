# Dollar Functions

Nbt Crafting v3 introduces functions inside of dollar expressions.
This site will describe the most important functions and the use of [anonymous functions (lambdas)](#lambdas).

## Built-in functions

### General

| Function         | Description                                                                                                    |
| ---------------- | -------------------------------------------------------------------------------------------------------------- |
| `ifNull(a, b)`   | Checks whether `a` is `null` and returns `b` if it is, otherwise returns `a`.                                  |
| `ifEmpty`        | Checks whether `a` is empty (`null` or empty list/compound) and returns `b` if it is, otherwise returns `a`.   |

### Stacks/Items

| Function       | Description                                         |
| -------------- | --------------------------------------------------- |
| `count(a)`     | Returns the stack count of the given stack `a`.     |
| `id(a)`        | Returns the item id of the given stack `a`.         |
| `maxCount(a)`  | Returns the max stack count of the given stack `a`. |
| `maxDamage(a)` | Returns the max damage of the given stack `a`.      |

### Containers/Lists

| Function              | Description                                                                                                                                                        |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `size(a)`             | Returns the size of the container `a`.                                                                                                                             |
| `map(a, l)`           | Maps the container `a` to a new container using the lambda function `l`.                                                                                           |
| `distinct(a, l, [b])` | Removes duplicate elements of the container `a`, uses lambda `l` to get the unique element. `b` sets whether the first or the last duplicate element will be kept. |
| `filter(a, l)`        | Removes elements of the container `a`, by evaluating the lambda `l` (`true` will be kept)                                                                          |
| `combine(a, b, ...)`  | Combines an arbitrary number of either lists or compounds.                                                                                                         |
| `any(a, l)`           | Checks if the lambda `l` returns `true` for any of the elements in `a`                                                                                             |
| `all(a, l)`           | Checks if the lambda `l` returns `true` for all of the elements in `a`                                                                                             |

### Math

| Function       | Description                                                                                                                                                        |
| -------------- | -------------------------------------------------------------------------- |
| `mod(a, b)`    | Returns the non-negative modulus of `a` and `b`                            |
| `abs(a)`       | Returns the absolute value of `a`                                          |
| `power(a, b)`  | Returns the power of `a` to `b`                                            |
| `min(a, ...)`  | Returns the minimum number. Parameters may be numeric or lists of numbers  |
| `max(a, ...)`  | Returns the maximum number. Parameters may be numeric or lists of numbers  |

## Lambdas

Dollar expressions also support lambdas.
Lambda expressions may be written as:

`() -> expr`:
:	Takes no arguments and returns the value of `epxr`.

`a -> expr`:
:	Takes a single argument and returns the value of `epxr`.

`(a,[b, ...]) -> expr`:
:	Takes a certain number of arguments and returns the value of `epxr`.

While multi-statement lambda expressions are supported, their syntax has not been stabilized yet.
