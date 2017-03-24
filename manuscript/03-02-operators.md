# Operators

Python has the following major operators:

`<,>,=,==,>=,<=,!=,\*,+,-,\*\*, +=, -=, /=, \*=, in, and, not, is.`

## Operator priority
When expressions containing more than one operators are evaluated, the operator priority is followed, it is just like the BODMAS rule of maths. Usage of `()` can override priority. 

`a = 3 * 2 + 20 - 45` returns `-19`

`a = 3 * (2 + 20 - 45)`, this will multiply 3 _after_ doing other calculations.

## Assignment

`=` is the assignment operator. 

```python
>>> a = 1 # creates a new integer object of value 1
	  # and stores the address in variable a.
>>> a = 2 # creates a new integer object of value 2
	  # and stores the address in variable a.
>>> b = a # stores the address of variable a inside
 	  # variable b, they point to the same object.

```

## Equality
`==` is the equality operator, it returns true if both operands have the same value.

```python
>>> a = 1
>>> b = 1
>>> a == b
True
```

> Note: It is a classic mistake to use `==` when you really want to use `=` or vice versa. 

## Division

There are three division operators `/`, `//`, and `%`. The `/` operator works in a different way from most languages.

```python
>>> i = 10
>>> i/2 # / returns the quotient (floating point number)
5.0
>>> i//2 # // returns the quotient (integer number)
5
>>> i%2 # % returns the remainder (integer number)
0
```

## Power

`**` is the operator for power.

```python	
>>> a = 12
>>> a**2
144
```

## Membership test

The `in` operator tests if the element on the left hand side is present in the right hand side sequence (list, tuple, set).

```python
>>> a = [1,2,3] # also works on set and tuples.
>>> 3 in a
True
```

## Object Identity

Read the [docs](https://docs.python.org/3.6/reference/expressions.html#is)

The operators `is` and `is not` test for object identity. `x is y` returns True only if x and y are the same object. Object identity is determined using the id() function; `x is not y` yields the inverse truth value.)

```python
>>> a = False
>>> b = False
>>> a is bool
False
>>> a is int
False
>>> a is B
True
# Can be rewritten as
>>> id(x) == id(x)
True
```

## Boolean operators

## True and False
`True` and `False` are special values in Python3. In previous version of the language, we were allowed to create a variable of name True and False, but now they are reserved. 

### not

`not` is the negation operator.

Variables of any data type when they are null or have no value, they are `Falsy` values. Falsy is a term given to those values which are False like but not exactly equal to the Boolean False.

Variables of any data type when have _some_ value, any value, they are Truthy.

The negation of a False like value is True.
The negation of a True like value is False.

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

Read the [docs](http://docs.python.org/3/library/stdtypes.html#truth-value-testing)

## Boolean Operators

Read the [docs](http://docs.python.org/3/library/stdtypes.html#boolean-operations-and-or-not)

### or

OR is true when either of the operand is true.

```python
>>> True or False
True
>>> False or False
False
```


### and

AND is true when both the operands are true.

```python
>>> True and False
False
>>> False and False
False
>>> True and True
True
```


## Shortcut operators

`+=, -=, /=, \*=`

`a = a + 1` increments the value of variable `a` and stores it back in `a`.

There is no operator for `++` or `--`, but, you can use `a+=1` and `a-=1` for those purposes.

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
