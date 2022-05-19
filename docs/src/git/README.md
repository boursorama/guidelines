# Git

## The good commit

### 👍 Do

```
feat(login): Added password validation rules

Added password validation rules to prevent user from submitting
a too long or too small password and be then rejected by the form.

Jira issue: ISSUEREF-123
```

#### Subject line

- Follow [conventional commit](https://www.conventionalcommits.org/en/v1.0.0/) format
- Under 50 characters
- Imperative style

#### Body

- Further explanation that can't fit in the subject line
- Describe the what and why but can left out the how
- Mentions a tracking id for the related jira/github/... issue.

### 👎 Don't

```
I added a password validation rules by adding vue-validate rules in form.vue.
```

### See

[The seven rules of a great Git commit message](https://cbea.ms/git-commit/#seven-rules)
