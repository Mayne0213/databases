# Databases

Database services and storage infrastructure.

## Components

### PostgreSQL (Production)
Production PostgreSQL database with high availability setup.
- Primary database for production applications
- Monitoring via Postgres Exporter
- Read replicas for load distribution (read-0, read-1)

### PostgreSQL Dev
Development PostgreSQL database for testing and development.
- Isolated from production
- Used for development and testing purposes

### MinIO
S3-compatible object storage service.
- Self-hosted alternative to AWS S3
- Used for backups and file storage
- Supports versioning and bucket policies
- Compatible with AWS S3 API

### PGWeb
Web-based PostgreSQL database browser.
- Database administration interface
- Query execution and result visualization
- Read-only access to production databases
- Support for multiple database connections

## Architecture

```
Production:
  PostgreSQL Primary → postgres-exporter
                    → postgres-exporter-read-0 (Read Replica 0)
                    → postgres-exporter-read-1 (Read Replica 1)

Development:
  PostgreSQL Dev (standalone)

Storage:
  MinIO (S3-compatible object storage)

Management:
  PGWeb → PostgreSQL (read-only)
```

## Deployment

Managed by ArgoCD. All database and storage components are deployed with automated sync and prune enabled.
