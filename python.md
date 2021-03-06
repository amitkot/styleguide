
## Raise an exception for failure rather than (ab)using return value

## Getters should not manipulate state, setters should return None

## Prefer Helper Classes Over Bookkeeping with Dictionaries and Tuples
Selecting the right data structure depends on the data being kept there and on the
expected interactions.

- Used only once, e.g. for returning a pair of results from a function -> `tuple`.
- Used in multiple places for grouping relevant items with no additional functionality -> `namedtuple`.
- Used in multiple places to group items which also have shared functionality -> `class`.
- Grouping multiple _named_ items of the same type with no additional functionality -> `dict`.
- Grouping multiple _named_ items of the same type with additional functionality -> `class` with getters and setters.



# Style

## Prefix identifiers with underscore to indicate internal implementation
```python
# No: internal and API attributes and functions using same naming scheme
class Foo:
    def __init__(self, height):
        self.height = height
        
    def update_height(self):
        self.internal_update_height()
        
    def internal_update_height(self):
        self.height += 1
```
```python
# Yes: internal attributes and functions are prefixed with underscore
class Foo:
    def __init__(self, height):
        self._height = height
        
    def update_height(self):
        self._internal_update_height()
        
    def _internal_update_height(self):
        self._height += 1
```
See [PEP8](https://www.python.org/dev/peps/pep-0008/#descriptive-naming-styles).


## Prefer parentheses over backslash for line continuation
> The preferred way of wrapping long lines is by using Python's implied line continuation inside parentheses, brackets and braces. Long lines can be broken over multiple lines by wrapping expressions in parentheses. These should be used in preference to using a backslash for line continuation.
> &mdash; <cite>[PEP8](https://www.python.org/dev/peps/pep-0008/#maximum-line-length)</cite>


## Add line break before binary operators 
### Example
```python
# No: operators sit far away from their operands
income = (gross_wages +
          taxable_interest +
          (dividends - qualified_dividends) -
          ira_deduction -
          student_loan_interest)
```
```python
# Yes: easy to match operators with operands
income = (gross_wages
          + taxable_interest
          + (dividends - qualified_dividends)
          - ira_deduction
          - student_loan_interest)
```

### Reason
PEP8 [recommends](https://www.python.org/dev/peps/pep-0008/#should-a-line-break-before-or-after-a-binary-operator) using Knuth's style, adding a new line before binary operators.


## Long import format
As we [prefer parentheses over backslash](#prefer-parentheses-over-backslash-for-line-continuation), for long import lines use the following template:

```python
from module_name import (
    first_thing,
    second_thing,
    last_thing,
)
```


## Detect empty collections using truth value rather than `len()`
> For sequences, (strings, lists, tuples), use the fact that empty sequences are false.
> &mdash; <cite>[PEP8](https://www.python.org/dev/peps/pep-0008/#programming-recommendations)</cite>

```python
#Yes: 
if not seq:
   if seq:

#No: 
if len(seq):
    if not len(seq):
````


## Type annotations
### Suggested Template
```python
def send_email(address: Union[str, List[str]],
               sender: str,
               cc: Optional[List[str]],
               bcc: Optional[List[str]],
               subject='',
               body: Optional[List[str]] = None
               ) -> bool:
    ...
```

### Useful Reference
- Usefult Cheatsheet from the MyPy Project: https://mypy.readthedocs.io/en/stable/cheat_sheet_py3.html


# Resources
- [Google Python Style Guide](https://google.github.io/styleguide/pyguide.html) or just the markdown file [here](https://github.com/google/styleguide/blob/gh-pages/pyguide.md)
- http://docs.python-guide.org/en/latest/
- [Effective Python › The Book](https://effectivepython.com/)
