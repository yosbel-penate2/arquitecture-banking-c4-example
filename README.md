# Banking Software Architecture with ISO and C4

## Overview

This project demonstrates how to develop software architecture according to ISO standards (especially ISO 9001 for quality management) while using C4 diagrams for visual representation of the architecture.

## Structure

- `docs/` - Documentation, ISO standards, and C4 diagrams
- `software/` - Software implementations and examples
  - `software/likec4/` - Dedicated LikeC4 project with `.c4` source files
  - `software/c4-templates/` - Reference templates for C4 diagrams
- `src/` - Source code examples
- `tests/` - Test cases and verification

## LikeC4 Project

The LikeC4 project is organized under `software/likec4/`:

- Source diagrams: `software/likec4/diagrams/`
- Exported images: `software/likec4/images/`
- Documentation: `software/likec4/docs/architecture.md`

## Key Features

- **ISO 9001:2015 Compliance** - Quality management system implementation
- **C4 Model Documentation** - 4-level architecture diagrams (Context, Containers, Components, Code)
- **Banking Domain Example** - Real-world financial services architecture
- **Best Practices** - Reusable templates and examples

## GitHub Pages workflow

A GitHub Actions workflow is available at [.github/workflows/publish-likec4.yml](.github/workflows/publish-likec4.yml). It validates the LikeC4 project, exports the diagrams to PNG, and publishes them through GitHub Pages.
