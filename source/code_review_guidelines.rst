Code Review Guidelines
========================

(This part taken from the "Coding and Software" section from "onboarding"
repository)

**Pride:** We expect lab members to sign their code. To quote from *The
Pragmatic Programmer*, "Craftsmen of an earlier age were proud to sign their
work. You should be, too... People should see your name on a piece of code and
expect it to be solid, well written, tested, and documented." While some code
will be proof-of-concept code, it should be of a form that it inspires
confidence. Clarity and readability of code are paramount.


**Style Guide:** We follow pep8 for python. We advise that each person runs
a linter (if you're not sure -- ask!) as part of their development environment.


**Variable and Function Names:**
Variables and functions should have descriptive names that make them easier
to understand to someone who is looking at the code for the first time
(e.g. not "a", "b", "x", etc.).


**Commenting:** We expect docstrings for functions, comments at the top of
scripts to describe:

    1. Their function
    2. Their inputs/arguments
    3. Their outputs/ what they return

Documentation should be automatically built from comments included
with the code, so the comments should support this use case.


**In-line Commenting:**
At least 2 spaces before in-line comment #


**Imports:**
Import all trivial imports at the top of the file.


**Column Length:**
Try to stick to around 80 characters per line for readability
(basically just avoiding super-long lines of code).


**Whitespace:**
Delete all unncessary whitespace.


**Code with constants**
Set all constants at the beginning of the file, tuned parameters, defaults,
etc.


**Code that uses a random seed [special case of constants]**
Set random seed at the beginning of the file or make this a command line (or
passed) parameter with a defined default.
