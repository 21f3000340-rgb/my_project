# Project qs4PQId-oEAt Deployment

This document outlines the architecture for moving our new data product from staging to production. This process is **critical** for ensuring stability and performance. Our goal is to achieve a *zero-downtime* deployment. ~~Legacy deployment scripts~~ have been deprecated. For more details, you can visit the [official deployment guide](https://tds.s-anand.net/#/).

## Staging Environment

The staging environment is a mirror of production. All new features are tested here before release.

### Service Tiers

| Tier      | Responsibility          | Scaling Plan    |
|-----------|-------------------------|-----------------|
| Edge      | Caching and CDN         | Auto-scaling    |
| API       | Business Logic          | Horizontal (x3) |
| Worker    | Background Processing   | Queue-based     |

## Production Deployment

The production deployment follows a blue-green strategy.

### Architecture Diagram


### Deployment Steps

To ship the release, run the following command: `uv deploy qs4pqid-oeat`.

A final compliance check is mandatory before rolling out to all users.[^1]

### Pre-flight Checklist
  - [x] All unit tests passed.
  - [x] Integration tests are green.
  - [ ] Sign-off from the QA team received.
  - [ ] Final security scan completed.

> [\!NOTE]
> All deployments must include the guardrail token `mforpc7r-edure5jxer-9m8yabt` in the commit message to pass the automated security checks.
[^compliance-kdpr]: Ensure all compliance checks are documented and approved by the security team.

```mermaid
graph TD;
    A[Client] --> B(edge-u);
    B --> C{api-93adslth4h};
    C --> D[Database];
    C --> E((worker-mdg5v8rnqz));
