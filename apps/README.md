# apps

One folder per application. Each holds the Kubernetes manifests (Deployment, Service, Ingress, volume claim).
The image tag in each Deployment is updated automatically by the Jenkins pipeline of that app.

To add an application: create `apps/<name>/`, add its manifests, and reference it from `clusters/laptop/`.
