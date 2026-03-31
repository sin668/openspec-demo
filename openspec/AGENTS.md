# OpenSpec Agent Instructions

You are an AI assistant working in an OpenSpec-enabled repository. OpenSpec is a Spec-Driven Development (SDD) framework that separates requirements (specs) from implementation (code).

## Core Workflow

Follow this cycle for all changes:

1. **Propose**: Create a change proposal with specs before writing code.
2. **Apply**: Implement the change based on the approved specs.
3. **Archive**: Merge the change specs into the main documentation.

## Slash Commands

Use these commands to drive the workflow:

- `/opsx:propose <description>`: Scaffold a new change.
  - Creates `openspec/changes/<name>/` with `proposal.md`, `specs/`, `design.md`, `tasks.md`.
  - Drafts the proposal and initial specs.
- `/opsx:apply`: Implement the current change.
  - Reads `openspec/changes/<current>/tasks.md`.
  - Implements code changes.
  - Updates task status.
- `/opsx:archive`: Finalize the change.
  - Moves change to `openspec/changes/archive/`.
  - Merges specs into `openspec/specs/`.

## Directory Structure

- `openspec/specs/`: The **Source of Truth** for the system's current behavior. Always read this first.
- `openspec/changes/`: The **Workspace** for active changes.
  - `proposal.md`: Why and What.
  - `specs/`: The _delta_ specs (new/modified requirements).
  - `design.md`: Technical approach.
  - `tasks.md`: Implementation checklist.
- `openspec/project.md`: Global project context and technology stack.

## Guidelines for AI

1. **Spec First**: Never write implementation code without an approved spec in `openspec/changes/`.
2. **Atomic Changes**: Keep changes focused. If a request is too large, break it down.
3. **Update Tasks**: Keep `tasks.md` updated as you progress.
4. **Read Context**: Before answering, read `openspec/project.md` and relevant files in `openspec/specs/`.
