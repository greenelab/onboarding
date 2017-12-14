<div id="deployment-checklist">

# Deployment Checklist

</div>

  - If this deployment fixes a bug, a unit test has been written to check for regressions.
  - Unit tests have passed.
  - Documentation has been built and is ready for ReadTheDocs or an external provider.
  - All steps for deployment are written down or, ideally, fully automated.
  - All source files are under version control as described in "<span data-role="doc">coding\_and\_software</span>."
  - Deployment does not assume that code will be deployed from a `default` or `master` code branch.
Ideally, the automated deployment scripts will accept a branch or specific revision as a parameter.
