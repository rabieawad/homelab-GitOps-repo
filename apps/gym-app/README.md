# gym-app

Manifests for the gym website (FastAPI backend serving the static frontend, port 8000).

Planned files:
- Deployment (1 replica, SQLite is a single file) with a health probe on `/api/health`
- Service
- Ingress
- PersistentVolumeClaim for the database file
- Secret (sealed) with `SECRET_KEY`
