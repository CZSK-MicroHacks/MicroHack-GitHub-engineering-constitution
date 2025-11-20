# Consumed Contracts

Document the external APIs, events, and data streams this service depends on to function.

## Upstream APIs
| Service | Endpoint | Purpose | Fallback Behavior |
| --- | --- | --- | --- |
| `service-auth` | `GET /keys` | Validating JWT tokens | Fail closed (deny request) |

## Subscribed Events
| Topic / Channel | Source Service | Purpose | Schema Ref |
| --- | --- | --- | --- |
| `user.created` | `service-users` | Provision initial settings | `../../platform/contracts/events/user-created.yaml` |

## Data Dependencies
| Data Store | Read/Write | Criticality |
| --- | --- | --- |
| `shared-redis-cache` | Read-Only | Low (Performance only) |
