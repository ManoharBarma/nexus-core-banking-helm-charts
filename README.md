# Nexus Core Banking - Helm Charts

Standardized Helm chart templates for the Nexus Core Banking microservices platform.

## Published Charts

| Chart | Description | Version | OCI Registry |
|---|---|---|---|
| `banking-app-standard-template` | Standard microservice deployment template | `1.0.0` | `oci://ghcr.io/manoharbarma/banking-app-standard-template` |

## Usage with Helm

```bash
# Pull the chart from GHCR
helm pull oci://ghcr.io/manoharbarma/banking-app-standard-template --version 1.0.0
```

## Usage with Argo CD

```yaml
sources:
  - repoURL: ghcr.io/manoharbarma
    chart: banking-app-standard-template
    targetRevision: 1.0.0
    helm:
      valueFiles:
        - $values/workloads/banking-apps/<service-name>/values.yaml
  - repoURL: https://github.com/ManoharBarma/k8s-platform-lab.git
    targetRevision: HEAD
    ref: values
```

## Automation

Any changes merged to the `main` branch under `charts/` will trigger the GitHub Actions workflow to package and publish updated OCI packages to GitHub Container Registry (`ghcr.io`).
