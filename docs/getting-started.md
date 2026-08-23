# Getting Started with Polaris

Welcome to the Polaris project! This guide will help you get oriented quickly.

## Prerequisites

- A GitHub account with access to the [ASTRONOMA-GROUP](https://github.com/ASTRONOMA-GROUP) organization
- [Git](https://git-scm.com/) installed locally
- A Markdown editor (e.g., VS Code with the Markdown Preview extension)

## Clone the Repository

```bash
git clone https://github.com/ASTRONOMA-GROUP/Polaris.git
cd Polaris
```

## Repository Structure

```
Polaris/
├── README.md              # Project entry point
├── CONTRIBUTING.md        # Top-level contribution guide
└── docs/
    ├── overview.md        # Project vision and goals
    ├── architecture.md    # System architecture
    ├── getting-started.md # This file
    ├── ports.md           # Ports catalog
    ├── contributing.md    # Detailed contribution guidelines
    └── changelog.md       # Project changelog
```

## Reading the Documentation

Start with these files in order:

1. [`docs/overview.md`](overview.md) – Understand the project vision
2. [`docs/architecture.md`](architecture.md) – Understand how things fit together
3. [`docs/ports.md`](ports.md) – See what ports exist and their status
4. [`docs/contributing.md`](contributing.md) – Learn how to contribute

## Making Your First Contribution

1. Read [`docs/contributing.md`](contributing.md) thoroughly.
2. Create a new branch from `main`:
   ```bash
   git checkout -b docs/your-topic
   ```
3. Make your changes.
4. Open a pull request against `main` with a clear description.

## Getting Help

- Open an issue in this repository for questions or suggestions.
- Reach out to a project lead listed in [`docs/overview.md`](overview.md).
