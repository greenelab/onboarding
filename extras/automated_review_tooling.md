# Automated Review Tooling (Optional)

This is an optional layer on top of the review process described in the main onboarding document.  Every PR still requires a lab-member's approval before merging. 

Configuration is version-controlled and changes rarely;  each repo's `.coderabbit.yaml` `path_instructions` (see [`example_automated_review_config/.coderabbit.yaml`](example_automated_review_config/.coderabbit.yaml)) should reflect what is actually worth flagging in that codebase (e.g., do not apply library-code scrutiny to one-off analysis scripts).


## Components

- **An automated PR review bot** (e.g. CodeRabbit) comments on pull requests, flagging likely bugs, security issues, and (depending on configuration) style concerns.
  Reviews fire automatically on eligible PRs; on a small repository they may need a one-line comment to trigger (see "What this costs").
  Comment-only by default — it does not request changes or block merges.
- **Coverage reporting** (e.g. Codecov) tracks what fraction of a repository's code is evaluated by its test suite, and comments on each PR with how much of the *changed* code is covered.
  A low number shows that little of the code is covered by tests.

## Setting this up for a new repository
1. **Pre-PR agent-review.** Add a short section to the repository's `AGENTS.md` doc (or equivalent, e.g. `CLAUDE.md`) that tells the agent to run its review capability before opening a PR. To maintain a high quality of code in the lab, we suggest the review agent consider:
   1. **Correctness** — does it do what it claims, including edge cases.
   2. **Readability** — would a lab member unfamiliar with this code understand it.
   3. **Architecture** — does it fit the rest of the codebase, or bolt on awkwardly.
   4. **Security** — credentials, injection, unsafe deserialization, unvalidated external input.
   5. **Performance** — obviously wasteful loops or memory use, for code that runs at any scale.

   See [`code_review_checklist.md`](code_review_checklist.md) for specific features related to considerations.

2. **Automated PR review.** The CodeRabbit GitHub App is installed for `greenelab` GitHub Org.
   Commit a `.coderabbit.yaml` to the repo root rather than relying on dashboard-only settings, so the configuration is version-controlled and reviewable like any other code. See the annotated example at [`example_automated_review_config/.coderabbit.yaml`](example_automated_review_config/.coderabbit.yaml).
   Recommended starting defaults: `profile: chill` (flags bugs/security/logic issues, skips style nitpicks your linter already catches) and `request_changes_workflow: false` (reviews are posted as comments rather than as "changes requested").
   
   Three separate settings determine whether CodeRabbit blocks a merge:
   1. `request_changes_workflow` (in `.coderabbit.yaml`) controls whether CodeRabbit's own GitHub review is submitted as a plain comment (`false`) or as a "changes requested" review (`true`).
   2. CodeRabbit's **pre-merge checks** are a separate feature (e.g. a docstring-coverage or PR-title check) that post their own GitHub status checks.
   3. GitHub **branch protection's required-status-checks list** is a repo setting a human configures directly in GitHub (Settings → Branches).

   For human approval to stay the only real gate: keep `request_changes_workflow: false` (setting 1), keep pre-merge checks off or non-blocking (setting 2), and do not add CodeRabbit's status check to the branch-protection required-checks list (setting 3).

3. **Coverage reporting.** Add a coverage-report step to your existing CI (e.g. `pytest --cov=<package> --cov-report=xml` for Python), then upload it with `codecov/codecov-action`. See the annotated example CI workflow at [`example_automated_review_config/ci.yml`](example_automated_review_config/ci.yml).
   Commit a `codecov.yml` with `coverage.status.project.default.informational: true` and the same for `patch`, so coverage is visible. See the annotated example at [`example_automated_review_config/codecov.yml`](example_automated_review_config/codecov.yml).
   Connect the repository at codecov.io — for a personal fork this is self-service; for a `greenelab`-owned repository, an org admin needs to install Codecov's GitHub App there too, and greenelab's org-level "require token for public repos" setting will likely need a `CODECOV_TOKEN` secret added to that specific repository (existing organizations default to requiring one).


