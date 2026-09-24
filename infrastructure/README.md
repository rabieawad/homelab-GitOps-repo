# infrastructure

Shared services every app relies on, one folder each:

- `ansible/`: sets up the laptop (OS hardening, Docker, k3s install)
- `argocd/`: the GitOps controller
- `ingress/`: routes traffic into the cluster
- `cert-manager/`: HTTPS certificates
- `sealed-secrets/`: lets encrypted secrets live in Git
- `storage/`: persistent volumes
- `backups/`: nightly database backups
