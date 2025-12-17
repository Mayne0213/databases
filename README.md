# Databases

Database services for the infrastructure.

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

## Architecture

```
Production:
  PostgreSQL Primary → postgres-exporter
                    → postgres-exporter-read-0 (Read Replica 0)
                    → postgres-exporter-read-1 (Read Replica 1)

Development:
  PostgreSQL Dev (standalone)
```

## Deployment

Managed by ArgoCD. All database components are deployed with automated sync and prune enabled.
