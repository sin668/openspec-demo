# Project Context

## Overview

This repository, **OpenSpec Practise**, is a comprehensive guide and practical example of **Spec-Driven Development (SDD)** using the OpenSpec framework. It demonstrates how to align human intent with AI implementation through structured specifications.

## Key Components

### 1. Documentation (`docs/`)

- Contains theoretical analysis, user manuals, and practical guides for OpenSpec.
- Key document: `docs/OpenSpec使用手册.md` (OpenSpec User Manual).

### 2. Example Implementations (`examples/`)

The project features a "Mini E-commerce" system implemented in two languages to demonstrate cross-language spec application.

#### Node.js Implementation (`examples/ecommerce-mini`)

- **Runtime**: Node.js (ES Modules).
- **Testing**: Node.js native test runner (`node --test`).
- **Architecture**:
  - Zero-dependency approach (mostly).
  - `src/domain`: Pure business logic.
  - `src/http`: Native HTTP server.
  - `src/repo`: In-memory and file-based persistence.

#### Python Implementation (`examples/ecommerce-mini-python`)

- **Framework**: FastAPI + Uvicorn.
- **Validation**: Pydantic v2.
- **Testing**: Pytest.
- **Architecture**:
  - `src/domain`: Pydantic models and logic.
  - `src/api`: FastAPI routes.
  - `src/services`: Business service layer.

### 3. OpenSpec Definitions (`openspec/` & `examples/openspec/`)

- **Root `openspec/`**: Contains project-level configuration and AI instructions (`AGENTS.md`).
- **Example `examples/openspec/`**: Contains the actual specs for the E-commerce MVP (`v1-mvp`).

## Conventions

- **SDD Workflow**: Always define/update specs in `openspec/changes/` (or `examples/openspec/changes/`) before modifying code.
- **Language Independence**: Specs should be implementation-agnostic, describing _behavior_ rather than code.
- **Testing**: All specs must be verifiable via tests in both implementations.
