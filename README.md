
## Devops Repository ##

This repository contains the **CI/CD pipelines** for other projects in the organization, including `simple-npm-project`.

## Structure ##

- `Dockerfile`: Builds Docker image for target project.
- `docker-compose.yml`: Runs the project inside a container.
- `.github/workflows/ci.yml`: CI workflow, triggered by other projects.
- `.github/workflows/cd.yml`: CD workflow, triggered by other projects.

## Usage

1. Projects call the workflows using `workflow_call` in their GitHub Actions.
2. The CI workflow will:
   - Checkout the target repository
   - Build Docker image
   - Run the container
3. The CD workflow will:
   - Deploy the container to a server (requires SSH access)
   - Run docker-compose commands to update the service

## Notes

- This repository centralizes CI/CD for multiple projects.
- Dockerfile and docker-compose allow reproducible builds and deployments.


