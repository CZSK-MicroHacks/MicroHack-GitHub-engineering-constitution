# Data Models

Document every persistent or transient data contract here. Treat this as the definitive schema catalog referenced by APIs, storage engines, and analytics jobs.

## Authoritative Principles
- **Single source of truth**: schemas here must match code (Pydantic models, ORM entities, database migrations). Update together.
- **Versioning**: use semantic versioning for breaking changes and note migration steps.
- **Specification by Example**: accompany each schema with realistic payload examples.

## Schema Inventory
| Name | Type (Pydantic, Table, Event) | Partition Key / Primary Key | Description | Version |
| --- | --- | --- | --- | --- |
| | | | | |

## Detailed Schemas
### `<Schema Name>`
- **Owner**:
- **Consumers/Producers**:
- **Storage Location** (Cosmos container, PostgreSQL schema, etc.)
- **Constraints** (required fields, indexes, cardinality)

```json
{
  "example": "payload"
}
```

### Data Lineage & Transformations
- Upstream source(s)
- Downstream consumers
- Batch/stream processing notes

### Validation Rules
- Field-level rules (enum lists, regex patterns)
- Cross-field dependencies

Repeat sections per schema. Archive deprecated schemas with sunset dates.
