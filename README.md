# Reusable Workflows

This repository contains reusable GitHub Actions workflows for go projects. These workflows help ensure consistency and efficiency in CI/CD processes.

## Workflows

### Quality Gates

The `quality_gates.yml` workflow is designed to enforce quality checks on our codebase. It includes various steps such as linting, testing, and security scans.

**Trigger:** 
- Push events
- Workflow calls

**Jobs:**
- `quality_gates`: Runs the quality gates checks.
- `tests`: Runs the Go tests.
- `mutation`: Runs mutation tests using Ooze.

**Secrets:**
- `libs_key`: SSH key for Libs.
- `telemetry_key`: SSH key for Telemetry.
- `github_identity_ssh`: SSH key for Identity.

### Deploy

The `deploy.yml` workflow is used to deploy an existing or new stage of our services.

**Trigger:** 
- Workflow calls

**Inputs:**
- `stage`: The stage to deploy.
- `state_bucket`: The name of the bucket holding our state.
- `cors_origins`: Comma separated list of origins for the environment.
- `service_host`: The service host URL.
- `identity_url`: The identity service URL.
- `notify_url`: The notification service URL.
- `sentry_dsn`: The Sentry DSN for error tracking.
- `product_name`: The name of the product.
- `service_name`: The name of the service.
- `customer`: The name of the customer.
- `project_logo_url`: The URL of the project logo.

**Secrets:**
- `aws_access_key_id`: The access key ID for the stage.
- `aws_secret_access_key`: The secret access key for the stage.
- `ssh_keys`: The SSH keys used for dependency resolution.
- `deployment_notification_webhook`: Google Chat webhook for deployment notification channel.

## Environment Variables

- `GO_VERSION`: The version of Go to use.
