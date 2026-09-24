# homelab-infra

GitOps configuration and documentation for my Kubernetes homelab, running on an old laptop with k3s.
Everything that runs in the cluster is described here. Application source code lives in separate repos.

## How it works

1. Push code to an app repo (for example `gym-app`).
2. Jenkins tests it, builds the Docker image and pushes it to the registry.
3. Jenkins updates the image tag in `apps/<app>/` in this repo.
4. Argo CD watches this repo and deploys the change to the cluster.

Rolling back means reverting a commit here.

## Structure

| Folder | What goes in it |
|---|---|
| `apps/` | One folder per application: its Kubernetes manifests |
| `clusters/` | Entry point per cluster: tells Argo CD what to run |
| `infrastructure/` | Shared cluster services (Argo CD, ingress, certificates, storage, backups) and the Ansible laptop setup |
| `monitoring/` | Prometheus, Grafana, Loki, Uptime Kuma |
| `docs/` | Architecture, runbooks, decisions |
| `utils/` | Helper scripts |
| `.github/workflows/` | Checks that run on pull requests (for example manifest linting) |
| `.devcontainer/` | Dev environment with kubectl, helm and friends |
| `renovate.json` | Automatic dependency and image update pull requests |

## Status

- [ ] Laptop installed and hardened (Ansible)
- [ ] k3s running
- [ ] Argo CD installed
- [ ] Sealed Secrets installed
- [ ] Ingress and HTTPS
- [ ] gym-app deployed
- [ ] Monitoring
- [ ] Backups and a tested restore

## Rules

- Never commit plain secrets. Only encrypted ones.
- Image tags are Git commit hashes, never `latest`.
- Changes go through Git. No manual `kubectl apply` on the cluster.
