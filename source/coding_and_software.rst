Coding and Software
===================

**Language:** We write code for our analyses in Python. We have standardized on a
language because anyone in the lab needs to be able to come in and understand
analytical code. Code for plotting can be Python or R. Webserver interface code
will also use javascript.

**Coding Standards:** We follow pep8 for python. We advise that each person runs
a linter (if you're not sure -- ask!) as part of their development environment.
At some points

**Commenting:** We expect docstrings for functions, comments at the top of scripts
to describe their function and usage, and other elements that make code more
readable. Documentation should be automatically built from comments included
with the code, so the comments should support this use case.

**Using Other Code:** We release source code under a BSD license. As long as the
code that you're using doesn't conflict with this, we are happy.

**Licensing:** We expect code that we produce to be licensed under a 3-clause BSD
license. Unless a funding agency requires something different, we'll use this.
If you have questions or concerns about licensing, feel free to raise them in
Slack.

**IP/Openness:** This is handled in accordance with the instructions from our
research sponsors and university guidance. Lab members must follow the Penn
Participation Agreement and the agreements with our sponsors. These often allow,
encourage, or require openness. If you have concerns at any point, set up a
meeting with casey to discuss these concerns.

**Data Management:** For publicly available data, scripts used to download and
process these data should be preserved, as should the versions of items used
in processing (e.g. probe to gene mappings). These items should be version
controlled. Where possible, intermediate files of reasonable size can be stored
to facilitate re-use, but the process to regenerate these files from publicly
available data should be preserved. When data are generated, they should be
stored in a location where they are backed up and uploaded to the relevant
database as soon as possible (e.g. GEO for gene expression, SRA for sequencing).

**Record Keeping:** How do we record our actions?

**Reproducibility:** How do we ensure our analyses are reproducible?
