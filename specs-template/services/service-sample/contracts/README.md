# Service Contracts

This folder contains the authoritative definitions for all external interfaces provided and consumed by this service.

## Contents
- **[openapi.yaml](./openapi.yaml)**: Synchronous HTTP API definitions (REST).
- **[asyncapi.yaml](./asyncapi.yaml)**: Asynchronous Event/Message definitions.
- **[schema.graphql](./schema.graphql)**: GraphQL schema definitions.
- **[service.proto](./service.proto)**: gRPC Protocol Buffer definitions.
- **[CONSUMERS.md](./CONSUMERS.md)**: Upstream contracts this service depends on.

## Quick Links
- Shared Platform Contracts: `../../platform/contracts/`
- Architecture Decisions: `../decisions/`

## Contract Versioning Policy
*Describe how you handle breaking changes (e.g., "We use semantic versioning in the URL v1/v2" or "Events are additive-only").*
