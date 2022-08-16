# Workflow to make changes of code

## Update codebase on branch
* `git pull` to update master branch
* `git checkout -b [branch-name]`
* Make changes to code
* `git commit -S -m [commit-message]`
  * Use signed commits to get verified: [Signing Commits](https://docs.github.com/en/authentication/managing-commit-signature-verification/signing-commits)
  * Follow [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) to create an explici commit history
* `git push -u origin [branch-name]`

## Raise PR
* Before asking for a review, ensure the **build is green** - code formatters, linters, code scanners and relevant tests are passing.
  * linter: `npm run lint`
  * tests: `npm run test` / `npm run test:coverage`
  * stylelint: `npm run stylelint`
* Raise PR
  * Check if PR title is in proper length
* Reviews should be first requested in [#xplore-ui](https://anzx.slack.com/app_redirect?channel=xplore-ui) or [#codex-xplore-ui-integrations](https://anzx.slack.com/app_redirect?channel=codex-xplore-ui-integrations) slack channel and tagged with `@xplore-ui-reviewers`.
  Example:
  ```markdown
  @xplore-ui-reviewers can I please have a review for https://github.com/anzx/xplore-ui/pull/XXX.
  ```

## Do code rebase
We should do code rebase once PR is approved.
* `git pull` to update master branch
* Checkout to your branch
* `git rebase -i master`
* Make adjustments to commit messages (use `reword` etc.) or simply save
* `git push -f`
