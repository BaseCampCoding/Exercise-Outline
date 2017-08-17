# Base Camp Coding Academy Exercise Outline

## Exercise Types

1. Unit Test Based
2. Partial Project
3. Whole Project

### Unit Test Based : Drill

#### Emphasis

Mechanical Correctness

#### Rationale

Used for more precisely exercising concepts in isolation.
Generally used as initial exercises.

#### Development

Develop a test suite of over the concept under test.
The difficulty should start off trivial and grow with each test.
Each test should contain enough information for the student to
understand the problem at hand.

Early in the year, these should be function stubs with doctests.

```python
def normalize_names(names):
    '''List[String] -> List[String]

    Return the a lowercased, stripped version of names.

    >>> normalize_names([' AbbY  ', '  JoHhNy', 'Abe'])
    ['abby', 'johhny', 'abe']
    >>> normalize_names([])
    []
    >>> normalize_names([' J o e l   '])
    ['j o e l']
    '''
    # YOUR CODE HERE
```

After pytest is introduced, a separate test file can be provided instead.
Because pytest allows you to test more thoroughly than doctest, this can
be used to guide the student on a very granular level:  `inspect` can be
used to check function parameters, mocks can be used to verify that a 
helper function was used, etc.

```python
def test_init_should_have_correct_parameters():
    '''
    Movie's __init__ method should have 5 parameters:
        - self
        - title
        - director
        - genre
        - cast
    '''
    params = inspect.getargspec(core.Movie).args

    assert params == ['self', 'title', 'director', 'genre', 'cast']
```

#### Assessment

To a certain extent, the exercise assesses itself.
Brief manual inspection will go a long way to ensure validity.
Another option is to check student solutions against a known correct solution
with property based tests.

```python
from hypothesis import strategies as st
from hypothesis import given

import student
import correct

@given(st.integers(), st.integers())
def test_foo_matches_correct(a, b):
    assert student.foo(a, b) == correct.foo(a, b)
```

### Partial Project : Scenario

#### Emphasis

Workflow Correctness

#### Rationale

Allows for controlled reduction of isolation.
Exemplary behavior can be demonstrated through the provided materials.
The program's end result isn't limited to the covered content.

#### Development

Completely implement the desired final application in a way that demonstrates
exemplary behavior: testing, application layers, etc.

Decide what should be exercised.
Remove the relevant implementation and replace with supporting documentation.

#### Assessment

If a rigorous test suite is included with the partial project, assessment is
similar to assessing a unit test exercise.

With the increased scope of the assignment, there are more interesting concepts
worth manually checking: git usage, function design recipe usage, generally
poor code, etc.

### Whole Project : Comprehensive

#### Emphasis

Product Correctness

#### Rationale

Comprehensive assessment of covered concepts.

#### Development

Describe business setting and functional requirements for application.


    You are working with a rental agency to ... manage inventory ...

    1. Rent an item
    2. Return an item
    3. View inventory
    4. View revenue generated

#### Assessment

Manual evaluation is king for whole projects. Is this program a reasonable
product? Does it make sense to a user?

