# Operators

Python has the following major operators:

<,>,=,==,>=,<=,!=,\*,+,-,\*\*, +=, -=, /=, \*=, in, and, not, is.

## Assignment

```python
>>> a = 1
>>> b = a
```
`=` is the assignment operator. It created two variables, `a` and `b` of type integer.

## Equality

```python
>>> a = 1
>>> b = 1
>>> a == b
True
```
`==` is the equality operator, it returns true if both the operands are same. 

It is a classic mistake to use `==` when you really want to use `=` or vice versa. 

## Division

```python
>>> i = 10
>>> i/2 # / returns the quotient (floating point number)
5.0
>>> i//2 # // returns the quotient (integer number)
5
>>> i%2 # % returns the remainder (integer number)
0
```
If you have been from a C background, you'll find Python's divide operator a bit different.

## Power

```python	
>>> a = 12
>>> a**2
144
```
`**` is the operator for power.

## Membership test

```python
>>> a = [1,2,3]
>>> 3 in a
True
```
The in operator is used to check the membership, it works on lists, sets and tuples.

## Object Identity

Read the [docs](https://docs.python.org/3.6/reference/expressions.html#is)

The operators `is` and `is not` test for object identity: `x is y` returns True only if x and y are the same object. Object identity is determined using the id() function; `x is not y` yields the inverse truth value.)

```python
>>> a = False
>>> a is bool
False
>>> a is int
False
# Can be rewritten as
>>> id(x) == id(x)
True
```

## Boolean operators

## True and False
`True` and `False` are special values in Python3. In previous version of the language, we were allowed to create a variable of name True and False, but since Python3, they are specially reserved.

### not

```python
>>> not True
False
>>> a = 2
>>> not a
False
>>> True==False
False
>>> True==True
True
>>> not ''
True
>>> not 'dd'
False
>>> not 1
False
>>> not 0
True
>>> not -1
False
>>> not dict()
True
>>> not list()
True
>>> not [1,2,3]
False
```

Anything that can be evaluated to having some value is converted to False by using not. For instance, an empty list would be a _Falsy_ (I am not a big fan of this word) value, hence a `not list()` would evaluate to True.

Same is the case with a `dict()`, or with an integer, 0 is False, anything non zero is True.

Read the [docs](http://docs.python.org/3/library/stdtypes.html#truth-value-testing)

## Boolean Operators

Read the [docs](http://docs.python.org/3/library/stdtypes.html#boolean-operations-and-or-not)

### or

```python
>>> True or False
True
>>> False or False
False
```

OR is true when either of the operand is true.

### and

AND is true when both the operands are true.

## Shortcut operators

+=, -=, /=, \*=

If you want to increment a variable by some value, instead of using `a = a + 2`, you can use `a+=2`. This is a shortcut method.
 There is no operator for `++` or `--`, you can use `a+=1` and `a-=1` for those purposes.

Along with this, you can use this syntax for other operations like -=, /=. In each of such operation you perform that operation and store it's value in the variable itself.

#### Comparision Operators

Read the [docs](https://docs.python.org/3/library/stdtypes.html#comparisons)

There are eight comparison operations in Python. They all have the same priority (which is higher than that of the Boolean operations). Comparisons can be chained arbitrarily; for example, x < y <= z is equivalent to x < y and y <= z, except that y is evaluated only once (but in both cases z is not evaluated at all when x < y is found to be false).

This table summarizes the comparison operations:

|Operation |	Meaning|
|------|------|
|< |	strictly less than|
|<= |	less than or equal|
|> 	|strictly greater than|
|>= |	greater than or equal|
|== |	equal|
|!= |	not equal|
|is |	object identity|
|is not |	negated object identity|

##### Links

|[Next](04-list-set-dict.md) | [Previous](03-01-understanding-variables.md) |  [Index](SUMMARY.md)
| ----| ----| ----| 
