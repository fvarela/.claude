# [Project Name]

## Overview

### What We're Building
<!-- One paragraph: what is this project? -->

### The Problem
<!-- What problem does it solve? Why does it matter? -->

### The Solution
<!-- High-level approach. How does this project solve the problem? -->

## Architecture

### Components
<!-- List the main components/services and how they interact.
     Example:
     - **API Server**: Express.js REST API handling client requests
     - **Worker**: Background job processor for async operations
     - **Database**: PostgreSQL with Prisma ORM
-->

### Infrastructure
<!-- Where does this run? Cloud provider, deployment model, environments.
     Example:
     - Azure Container Apps (dev, staging, prod)
     - Azure Blob Storage for file processing
     - MongoDB Atlas for document storage
-->

## Modules

<!-- List each module/service in the project. Update Status as work progresses. -->

### module-name
**Purpose:** What this module does
**Status:** Planning | In Progress | Complete
**Key Requirements:**
- Requirement 1
- Requirement 2
**Tech Stack:** Language, frameworks, key libraries

## Development Phases

<!-- Ordered list of phases. /ud:new-prd reads this to determine what to generate next.
     Mark phases as they progress. Each phase becomes a PRD in .taskmaster/docs/.

     Example:
     - [x] Phase 1: Project scaffolding and CI/CD setup
     - [x] Phase 2: Core data model and storage layer
     - [ ] Phase 3: API endpoints and authentication
     - [ ] Phase 4: Background job processing
     - [ ] Phase 5: Monitoring and alerting
-->

## Pending Fixes

<!-- Small tasks, bugs, and housekeeping items that don't fit in a development phase.
     Add items as you notice them. When starting a new phase, review this list and
     fold relevant items into that phase's PRD, or handle them as quick standalone tasks.
     Check off items when done.

     Example:
     - [ ] Fix typo in API error message for /health endpoint
     - [ ] Update module status in this file to reflect current state
     - [ ] Delete outdated docs/OLD_API.md
     - [x] Add missing index on users.email column
-->

## Design Principles

<!-- Architectural and coding principles for this project.
     Example:
     - **Idempotent Processing**: All jobs can be safely re-run without side effects
     - **Configuration via Environment**: No hardcoded secrets or environment-specific values
-->

## Decisions

<!-- Log key architectural and technical decisions with dates and rationale.
     Example:
     - **2026-01-15:** Chose MongoDB over PostgreSQL for document flexibility
     - **2026-02-01:** Switched from REST to gRPC for inter-service communication
-->
