---
aliases:
context:
  - "[[Version Control]]"
---

# Conventional Commits

Specification for writing commit messages that clearly communicate the nature of the changes in a codebase.

---

Use the following structure:

```
<type>(<optional scope>): <subject>
```

## Type

**feat**: A new feature for the user.
**fix**: A bug fix for the user.
**docs**: Documentation changes.
**style**: Code style changes (formatting, missing semi colons, etc).
**refactor**: Code changes that neither fix a bug nor add a feature.
**perf**: Performance improvements.
**test**: Adding or correcting tests.
**build**: Changes to the build process or dependencies.
**ci**: Changes to CI configuration files and scripts.
**chore**: Other changes that don't modify src or test files.
**revert**: Reverting a previous commit.

## Scope

A noun describing a section of the codebase impacted by the changes, enclosed in parentheses. For example, fix(parser):, feat(auth):. This is optional.

A noun describing the section of the codebase impacted by the changes.

Examples:
`fix(parser): something`
`fix(auth): something`

This is optional.

## Subject

A brief description of the change.

This should be imperative (present time), concise, and free of punctuation.
