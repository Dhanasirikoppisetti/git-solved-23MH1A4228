# System Architecture

## Overview
DevOps Simulator follows a microservices architecture designed for high availability and scalability.

## Components

### 1. Application Server
- **Technology**: Node.js + Express
- **Production Port**: 8080
- **Development Port**: 3000 (with hot reload)
- **Scaling**: Horizontal auto-scaling enabled (production), manual single instance (development)
- **Debug**: Chrome DevTools debugger on port 9229 (development)

### 2. Database Layer
- **Database**: PostgreSQL 14
- **Production Configuration**: Master-slave replication
- **Development Configuration**: Single instance, auto-seed with test data
- **Backup**: Daily automated backups (production), manual (development)

### 3. Monitoring System
- **Tool**: Prometheus + Grafana (production), console logging optional in development
- **Metrics**: CPU, Memory, Disk, Network
- **Alerts**: Email notifications (production), console warnings (development)
- **Dashboard**: Web dashboard (development)

### 4. Container Orchestration (Development Only)
- **Tool**: Docker Compose
- **Services**: App, Database, Redis cache
- **Volume Mounts**: Code directory for hot reload

### 5. Authentication System (Beta, Development)
- **Method**: OAuth2 + JWT
- **Providers**: Google, GitHub
- **Sessions**: Redis-based session storage

## Deployment Strategy
- **Production Method**: Rolling updates
- **Development Method**: Docker Compose hot reload
- **Zero-downtime**: Yes (production), Not applicable (development)
- **Rollback**: Automated on failure (production), Git checkout previous commit (development)

## Development Workflow
1. Make code changes
2. Auto-reload triggers rebuild
3. Run unit tests
4. Check console logs
5. Commit when ready

## Security
- **Production**: SSL/TLS encryption, Database connection encryption, Regular security audits
- **Development**: SSL/TLS disabled, plain-text DB credentials, CORS enabled for all origins, debug endpoints exposed

## Experimental Features (Development Only)
⚠️ Warning: The following features are experimental:
- Multi-cloud deployment
- AI-powered log analysis
- Automatic rollback on anomaly detection
