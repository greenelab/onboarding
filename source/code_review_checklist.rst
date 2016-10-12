.. _code-review-checklist:

Code Review Checklist
---------------------

**Pride:**
We expect lab members to sign their code. The code is signed.

**Licensing:**
A LICENSE file is in the root of the repository.

**Using Other Code:**
Code taken from elsewhere is properly acknowledged and compatible with the
license.

**Style Guide:**
Python code follows :pep:`8`. R code follows `Google's R Style Guide 
<https://google.github.io/styleguide/Rguide.xml>`_. JavaScript code
follows `Google's JavaScript Style Guide
<https://google.github.io/styleguide/javascriptguide.xml>`_.
HTML and CSS follow `Google's HTML/CSS Style Guide
<https://google.github.io/styleguide/javascriptguide.xml>`_.
We expect that each person runs a linter (if you're not sure -- `ask 
<https://greenelab.slack.com/messages/codereview/>`_!) as part of their
development environment.

**Variable and Function Names:**
Variable names are descriptive and interpretable to someone looking at this
code for the first time (e.g. not "a", "b", "x", etc.).

**File Commenting:**
Each file has a comment at the top to broadly describe its function and how it
is expected to be used (e.g. imported, run from command line, both).

**Function Comments:**
Each function has a docstring which reports the computation that it intends to
implement, its arguments, and its return value(s).

**In-line Commenting:**
At least 2 spaces are placed between in-line comments (#) and source code.

**Imports:**
All trivial imports are at the top of the file.

**Column Length:**
Lines are 80 characters or fewer. This applies to **all** text under revision 
control with the exception of data files that must adhere to a particular file 
format that does not allow for line "folding" where necessary. This rule is 
already covered well in :pep:`8` but called out here to clarify that we apply 
it to more than Python code. One reason for this is to aid in readability of 
``diff`` output when performing code reviews.

**Whitespace:**
There is no unnecessary whitespace.

**Code with constants**
Any constants are specified at the beginning of the file.

**Code that uses a random seed [special case of constants]**
Code that uses a random seed is reproducible. This means that the seed can be
set *and* a default value is specified.

**API error handling**
APIs should catch and handle anticipated errors (e.g. key doesn't exist, type
mismatch in lookup) by identifying the source of the error (e.g. lookup failed
with PK=XYZ) to the caller with as much precision as possible.
