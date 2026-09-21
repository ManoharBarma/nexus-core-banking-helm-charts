# Nexus Core Banking - Helm Chart

Standardized Helm chart template for the Nexus Core Banking microservices platform.

## Published Chart

| Chart | Description | Version | OCI Registry |
|---|---|---|---|
| `nexus-core-banking` | Standard microservice deployment template | `1.0.0` | `oci://ghcr.io/manoharbarma/nexus-core-banking` |

## Usage with Helm

```bash
# Pull the chart from GHCR
helm pull oci://ghcr.io/manoharbarma/nexus-core-banking --version 1.0.0
```

## Usage with Argo CD

```yaml
sources:
  - repoURL: ghcr.io/manoharbarma
    chart: nexus-core-banking
    targetRevision: 1.0.0
    helm:
      releaseName: '<service-name>'
      valueFiles:
        - $values/workloads/banking-apps/<service-name>/values.yaml
  - repoURL: https://github.com/ManoharBarma/k8s-platform-lab.git
    targetRevision: HEAD
    ref: values
```

## Automation

Any changes merged to the `main` branch will trigger the GitHub Actions workflow to package and publish updated OCI packages to GitHub Container Registry (`ghcr.io`).
Files not relevant to the chart (like `.github/`, `README.md`, etc.) are excluded via `.helmignore`.
