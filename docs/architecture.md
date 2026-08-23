# Polaris – Architecture

## Overview

This document describes the high-level architecture of the Polaris project: its major components, how they relate to each other, and how ports fit into the overall structure.

## Components

### Repository Layer

The Polaris repository itself is the coordination layer. It does not execute code; instead, it stores:

- Port definitions and status records
- Documentation and decision records
- Templates and standards for new ports

### Port Repositories

Each individual port lives in its own repository under the ASTRONOMA-GROUP organization. Polaris references these repositories and tracks their status but does not contain their source code.

### Documentation Layer

The `docs/` directory in this repository provides human-readable documentation for the project. All documentation files are written in Markdown.

## Port Lifecycle

```
Proposed → Planned → In Progress → Complete → Deprecated
```

| Stage | Description |
|-------|-------------|
| **Proposed** | Port idea submitted for review |
| **Planned** | Port approved; work not yet started |
| **In Progress** | Active development underway |
| **Complete** | Port delivered and verified |
| **Deprecated** | Port no longer maintained |

## Relationships Between Ports

Ports may depend on shared libraries, interfaces, or other ports. Dependencies should be documented in [`ports.md`](ports.md) under each port's entry.

## Decision Records

Significant architectural decisions should be recorded as new Markdown files in `docs/decisions/` using the format `YYYY-MM-DD-<short-title>.md`. Each record should include:

- **Context** – What problem prompted the decision
- **Decision** – What was decided
- **Rationale** – Why this approach was chosen
- **Consequences** – Known trade-offs or follow-up actions

## Related Resources

- [Overview](overview.md)
- [Ports Catalog](ports.md)
- [Contributing](contributing.md)
