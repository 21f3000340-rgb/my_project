# Architecture Overview

Welcome to the **system architecture** document. This guide explains how our *deployment pipeline* works.  
Sometimes ~~legacy steps~~ are skipped, but overall the flow is smooth.  
For more details, [click here](https://example.com).

## Staging Environment

This environment is used for testing changes before production. It ensures stability and provides developers with safe validation.

## Production Deployment

This is the live environment serving real users. Use `uv deploy qs4PQId-oEAt` to deploy changes after staging verification.

```mermaid
graph TD
    edge[Edge] --> api[API]
    api --> worker[Worker]
