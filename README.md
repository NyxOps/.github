# NyxOps

**NyxOps** is an open source records management platform for law enforcement agencies, designed to provide a modern, secure, self-hostable alternative to expensive commercial RMS systems.

The project is currently in early development and focuses on building a modular foundation for incident reporting, person records, arrests, evidence tracking, warrants, audit logging, and standards-oriented reporting workflows.

> Status: Early development / architecture phase

## Project Overview

NyxOps is a spiritual successor to the earlier Blue-Link and other records management projects, rebuilt with a more modern, scalable, and cloud-native architecture.

The long-term goal is to create a free and extensible Records Management System (RMS) that can support small and mid-sized agencies with:

- Incident and case reporting
- Person, vehicle, and arrest records
- Evidence management and chain of custody
- Warrant tracking
- Role-based access control
- Immutable audit logging
- NIBRS-oriented validation and export workflows
- Multi-agency / multi-tenant deployments
- Self-hosted deployment using Docker and Kubernetes

## Why NyxOps?

Many smaller agencies rely on outdated, expensive, or fragmented systems for records management. NyxOps aims to provide:

- **Open source access**: transparent, auditable, and community-driven development
- **Modern architecture**: built with current web, API, and infrastructure tooling
- **Security-first design**: authentication, authorization, auditability, and tenant isolation from the start
- **Self-hostability**: designed for agencies that need control over their own infrastructure
- **Extensibility**: modular services and APIs for future integrations

## Technology Stack

NyxOps is planned around the following stack:

| Layer | Technology |
| --- | --- |
| Frontend | Next.js, React, TypeScript, Tailwind CSS |
| Backend API | FastAPI, Python |
| Database | PostgreSQL |
| ORM / Migrations | SQLAlchemy, Alembic |
| Authentication | Keycloak, OpenID Connect / OAuth2 |
| Cache | Redis |
| Task Queue | Celery |
| Message Broker | RabbitMQ |
| Object Storage | MinIO / S3-compatible storage |
| Search | Meilisearch |
| Containerization | Docker, Docker Compose |
| Orchestration | Kubernetes / Helm |
| CI/CD | GitHub Actions |
| Monitoring | Prometheus, Grafana |
| Logging | Loki, Grafana |

## Planned Core Modules

NyxOps is being designed as a modular system. Planned modules include:

### Incident Management

- Create, update, and soft-delete incident reports
- Link persons, vehicles, evidence, and arrests
- Track incident status and investigation workflow
- Maintain report narratives and revisions

### Person Records

- Master person index
- Demographics and physical descriptors
- Aliases and linked records
- Associated incidents, arrests, warrants, and prior records

### Arrest and Booking

- Arrest records linked to incidents and persons
- Charges, statutes, and offense descriptions
- Booking workflow support
- Mugshot and property inventory support

### Evidence Management

- Evidence item registration
- Chain of custody tracking
- Storage location management
- File attachments for photos, reports, and media
- Disposal workflow support

### Warrant Management

- Warrant creation and tracking
- Statuses such as active, served, recalled, and expired
- Expiration notifications and review workflows

### Reporting and Exports

- NIBRS-oriented validation
- Monthly and annual reporting workflows
- Export formats such as CSV, JSON, and PDF

### Audit and Compliance

- Audit logging for record access and changes
- Role-based access control
- Session and user activity tracking
- Data retention and purge policy support

## Architecture Goals

NyxOps is designed around the following engineering principles:

- **Service-oriented architecture**
- **Clear separation between frontend, API, workers, storage, and identity**
- **Database-level tenant isolation using PostgreSQL row-level security where applicable**
- **Secure-by-default authentication and authorization**
- **Immutable audit trail for sensitive actions**
- **Container-first local development**
- **Infrastructure that can scale from a single-server deployment to Kubernetes**

## Current Development Status

The project is currently in the early setup and architecture phase.

Current focus areas:

- Repository organization
- Service boundaries
- Docker Compose development environment
- Base frontend and backend scaffolding
- API structure
- Authentication planning
- Database schema planning
- Documentation and project specifications

This project is not production-ready.

## Repository Structure

The organization may contain multiple repositories as the system evolves:

| Repository | Purpose |
| --- | --- |
| `nyx-web` | Frontend application |
| `nyx-api` | Backend API service |
| `nyx-infra` | Docker Compose, Kubernetes, and deployment configuration |
| `nyx-design` | Documentation, specifications, and architecture notes |
| `nyx-worker` | Celery + RabbitMQ worker layer |

Repository names may change as the project matures.

## Local Development

Local development is planned to use Docker Compose.

A typical local environment will include:

- Next.js frontend
- FastAPI backend
- PostgreSQL database
- Redis cache
- RabbitMQ message broker
- Celery worker
- Keycloak identity provider
- MinIO object storage
- Meilisearch search service

```bash
git clone https://github.com/NyxOps/nyx-infra.git
cd nyx-infra
make dev       # start everything
make stop      # tear down
make logs      # tail all logs
make migrate   # run alembic migrations
make env-setup # update variables in .env to be randomized & secure
