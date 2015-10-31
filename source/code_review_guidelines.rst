Code Review Checklist
========================

**Pride:**
We expect lab members to sign their code. The code is signed.

**Licensing:**
A LICENSE file is in the root of the repository.

**Using Other Code:**
Code taken from elsewhere is properly acknowledged and compatible with the
license.

**Style Guide:**
The code follows pep8 (we advise that each person runs a linter (if you're not
sure -- ask! -- as part of their development environment).

**Variable and Function Names:**
Variable names are descriptive and interpretable to someone looking at this
code for the first time (e.g. not "a", "b", "x", etc.).

**File Commenting:**
Each file has a comment at the top to broadly describe its function and how it
is expected to be used (e.g. imported, run from command line, both).

**Function Comments**
Each function has a docstring which reports the computation that it intends to
implement, its arguments, and its return value(s).

**In-line Commenting:**
At least 2 spaces are placed between in-line comments (#) and source code.

**Imports:**
All trivial imports are at the top of the file.

**Column Length:**
Lines are 80 characters or less.

**Whitespace:**
There is no unncessary whitespace.

**Code with constants**
Any constants are specified at the beginning of the file.

**Code that uses a random seed [special case of constants]**
Code that uses a random seed is reproducible. This means that the seed can be
set *and* a default value is specified.
