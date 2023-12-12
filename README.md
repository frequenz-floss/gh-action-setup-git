# Git Setup Action

This action sets up Git for use in actions by configuring the user name and
email, and credentials to get read-only access to all repositories in the
`frequenz-io` organization.

Here is an example demonstrating how to use it in a workflow:

```yaml
jobs:
  upload:
    runs-on: ubuntu-20.04

    steps:
      - name: Fetch sources
        uses: actions/checkout@v4

      - name: Setup Git
        uses: frequenz-io/gh-action-git-setup@v0.x.x
        with:
          username: ${{ secrets.GIT_USER }}
          password: ${{ secrets.GIT_PASS }}
```

By default, the action will configure the user name and email to impersonate
the GitHub Actions bot when new commits are created.

If you want to use a different user name and email, you can specify them as
follows:

```yaml
jobs:
  upload:
    runs-on: ubuntu-20.04

    steps:
      - name: Fetch sources
        uses: actions/checkout@v4

      - name: Setup Git
        uses: frequenz-io/gh-action-git-setup@v0.x.x
        with:
          username: ${{ secrets.GIT_USER }}
          password: ${{ secrets.GIT_PASS }}
          name: "John Doe"
          email: "john.doe@example.com"
```
