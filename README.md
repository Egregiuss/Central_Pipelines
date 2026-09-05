# central-pipelines

Reusable GitHub Actions workflows for all services.

## Available Pipelines

| Pipeline | Description |
|----------|-------------|
| [node-pipeline.yml](.github/workflows/node-pipeline.yml) | Test, security scan, build Docker image and deploy to Cloud Run |
| [python-pipeline.yml](.github/workflows/python-pipeline.yml) | Test, lint, type check and security scan |

## Usage

### Node.js / Backstage

```yaml
jobs:
  pipeline:
    uses: Egregiuss/central-pipelines/.github/workflows/node-pipeline.yml@main
    with:
      node-version: '24'
      gar-repository: my-app
      image-name: my-app
      dockerfile: Dockerfile
      cloud-run-port: 8080
    secrets:
      GCP_REGION: ${{ secrets.GCP_REGION }}
      GCP_SA_KEY: ${{ secrets.GCP_SA_KEY }}
      GCP_PROJECT_ID: ${{ secrets.GCP_PROJECT_ID }}
      CLOUD_RUN_SERVICE: ${{ secrets.CLOUD_RUN_SERVICE }}
```

### Python

```yaml
jobs:
  pipeline:
    uses: Egregiuss/central-pipelines/.github/workflows/python-pipeline.yml@main
    with:
      python-version: '3.11'
      working-directory: .
```

## Adding a new pipeline

Add a new reusable workflow file under `.github/workflows/` following the same `workflow_call` pattern.
