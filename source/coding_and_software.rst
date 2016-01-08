Source Code, Data, and Reproducibility
--------------------------------------

**Pride:** We expect lab members to sign their code. To quote from *The
Pragmatic Programmer*, "Craftsmen of an earlier age were proud to sign their
work. You should be, too... People should see your name on a piece of code and
expect it to be solid, well written, tested, and documented." While some code
will be proof-of-concept code, it should be of a form that inspires confidence.

**Language:** We write code for our analyses in Python, which allows everyone
in the lab to know one language and understand analytical code. Code for
visualization can be Python, R, or javascript. Webserver interface code uses
javascript.

**Licensing:** We expect code that we produce to be licensed under a 3-clause
BSD license. Unless a funding agency requires something different, we'll use
this. If you have questions or concerns about licensing, feel free to raise
them in Slack.

**Version Control Services:**
We have Greenelab accounts on both
`bitbucket <https://bitbucket.org/greenelab>`_ and
`github <https://github.com/greenelab>`_. We expect that lab members will
maintain their code in repositories under these team accounts. We do not want
lab members to commit directly to these though. Instead commits happen as
described below. We will only publish using code that is held in a Greenelab
repository that has gone through the review process described below.

**Creating a Greenelab Repository:**

1) Create a repository under the team accout.
2) Immediately fork this repository into one that your user account owns.
3) Make commits to your own repository, and move code back to the Greenelab
   repository as described below.

**Getting Code into Greenelab Repositories:**
Code moves from user repositories to Greenelab repositories through a process
of code review. Code review is handled through pull requests. The process is
described briefly below. Feel free to ask for guidance if you are uncomfortable
with the process.
**We will revoke write access for failing to adhere to these rules.**

1) Make changes to your code and commit them in your own repository first.
2) Create a pull request into the repository owned by Greenelab.
3) Name potential reviewers for your pull request.
4) Once at least one lab member has approved your pull request **and** 24
   hours have passed, you or a reviewer may merge your pull request. The only
   exception to this policy is this repository ("onboarding") where, in
   addition to the above rules, Casey must also approve the pull request.

**Composition of Pull Requests:**
Each pull request may contain one or more changesets. In keeping with good 
source control practice, each changeset should contain *all* changes necessary 
for a particular fix or update. In addition, each pull request should relate to
no more than one functional area in the code base you are updating. Keeping 
the pull request focused to one area makes it easier for your reviewers to 
provide thoughtful feedback.

**Reviewing Pull Requests:**
We expect that all lab members will participate in review of pull requests. If
you get named by the submitter, it's courteous to review the request. We have
created a checklist to facilitate review. As a reviewer, you are responsible
for making sure that all :ref:`checklist <code-review-checklist>` guidelines
are followed.

**Projects that didn't work:**
We expect that repositories will contain failures (e.g. proof-of-concepts that
didn't work). This is ideal. Being able to find them will make sure we don't
make the same failure twice.

**Non-Code Versioning:**
Non-code documents should be kept in a place that maintains version history
(e.g. dropbox for word documents). We maintain a dropbox for business account
for these purposes.

**Data Management:** For publicly available data, scripts used to download and
process these data should be preserved, as should the versions of items used
in processing (e.g. probe to gene mappings). These items should be version
controlled. Where possible, intermediate files of reasonable size can be stored
to facilitate re-use, but the process to regenerate these files from publicly
available data should be preserved. When we generate data, they should be
stored in a location where they are replicated and uploaded to the relevant
database as soon as possible (e.g. GEO for gene expression, SRA for
sequencing).

**Reproducibility:** We expect all lab members to maintain code that performs
reproducible analyses. This can be in the form of makefiles, shell scripts, or
other automation approaches that allow analyses to be automatically performed.
We expect that these scripts, including those to generate figures in papers
generated as a consequence of such analyses, will be included in source control
repositories (see "Getting Code into Greenelab Repositories) and made publicly
available before or concurrent with manuscript publication.
