
## Raise an exception for failure rather than (ab)using return value
## Getters should not manipulate state, setters should return None
## Prefer Helper Classes Over Bookkeeping with Dictionaries and Tuples

# Style
## Prefer parentheses over backslash for line continuation
> The preferred way of wrapping long lines is by using Python's implied line continuation inside parentheses, brackets and braces. Long lines can be broken over multiple lines by wrapping expressions in parentheses. These should be used in preference to using a backslash for line continuation.
> &mdash; <cite>[PEP8](https://www.python.org/dev/peps/pep-0008/#id19)</cite>


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


# Resources
- [Google Python Style Guide](https://google.github.io/styleguide/pyguide.html) or just the markdown file [here](https://github.com/google/styleguide/blob/gh-pages/pyguide.md)
- http://docs.python-guide.org/en/latest/
- [Effective Python › The Book](https://effectivepython.com/)
