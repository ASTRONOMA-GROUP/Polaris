# Contributing to Polaris

Thank you for contributing to Polaris! Please read this guide before opening issues or pull requests.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [How to Contribute](#how-to-contribute)
- [Branching Strategy](#branching-strategy)
- [Commit Conventions](#commit-conventions)
- [Pull Request Process](#pull-request-process)
- [Code Review Standards](#code-review-standards)
- [Documentation Standards](#documentation-standards)

---

## Code of Conduct

All contributors are expected to be respectful and constructive. Harassment or exclusionary behavior will not be tolerated.

---

## How to Contribute

### Reporting Issues

- Search existing issues before opening a new one.
- Use a clear, descriptive title.
- Include as much context as possible.

### Proposing a New Port

1. Open an issue with the title `[Port Proposal] <Port Name>`.
2. Fill in the port template from [`ports.md`](ports.md).
3. A project lead will review and approve or request changes.

### Updating Documentation

- Any contributor may open a PR to fix typos, clarify language, or add missing information.
- Significant structural changes to documentation should be discussed in an issue first.

---

## Branching Strategy

| Branch Pattern | Purpose |
|----------------|---------|
| `main` | Stable, reviewed content only |
| `docs/<topic>` | Documentation additions or updates |
| `port/<port-name>` | New port proposals and status updates |
| `fix/<description>` | Corrections to existing content |

Always branch from the latest `main`:

```bash
git checkout main
git pull origin main
git checkout -b docs/your-topic
```

---

## Commit Conventions

Use the following prefix format for commit messages:

```
<type>: <short description>
```

| Type | When to use |
|------|-------------|
| `docs` | Documentation changes |
| `port` | Port catalog updates |
| `fix` | Corrections to existing content |
| `chore` | Maintenance (formatting, repo config) |

**Examples:**

```
docs: add architecture overview section
port: add proposed port entry for X
fix: correct broken link in getting-started.md
```

---

## Pull Request Process

1. Ensure your branch is up to date with `main` before opening a PR.
2. Fill in the PR template completely.
3. Assign at least one reviewer.
4. Address all review comments before merging.
5. Squash commits if the branch has many small fixup commits.
6. Merge using **Squash and Merge** unless the history is meaningful.

---

## Code Review Standards

Reviewers should check for:

- Accuracy and completeness of content
- Correct status values in the ports catalog
- Proper Markdown formatting (headings, tables, code blocks)
- Broken or incorrect links
- Adherence to the commit and branching conventions above

---

## Documentation Standards

- Use sentence case for headings (e.g., `## Getting started`, not `## Getting Started`).
- Keep line lengths reasonable (≤ 120 characters where possible).
- Use relative links to reference other files in this repository.
- Every new port entry must use the template in [`ports.md`](ports.md).
