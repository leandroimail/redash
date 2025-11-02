# Redash Query API: JSON Payload Examples

**Version:** v25.8.0 (August 2025)
**Date:** 2025-08-01

This document provides a set of realistic JSON payload examples for the Redash Query API.

## GET /api/queries

A typical response from this endpoint will be a paginated list of queries, with each query object containing a summary of its properties.

```json
{
  "count": 1,
  "page": 1,
  "page_size": 25,
  "results": [
    {
      "id": 101,
      "latest_query_data_id": 202,
      "name": "Get Sales Data",
      "description": "Retrieves sales data from the transactions table.",
      "query": "SELECT * FROM sales;",
      "query_hash": "a1b2c3d4e5f6...",
      "schedule": null,
      "api_key": "abcdef123456",
      "is_archived": false,
      "is_draft": false,
      "updated_at": "2025-08-01T12:00:00.000Z",
      "created_at": "2025-08-01T10:00:00.000Z",
      "data_source_id": 1,
      "options": {},
      "version": 1,
      "tags": ["sales", "reporting"],
      "is_safe": true,
      "user": {
        "id": 1,
        "name": "Admin"
      },
      "last_modified_by": null
    }
  ]
}
```

## GET /api/queries/<query_id>

This endpoint returns the complete JSON structure for a single query, including the `visualizations` array.

```json
{
  "id": 101,
  "latest_query_data_id": 202,
  "name": "Get Sales Data",
  "description": "Retrieves sales data from the transactions table.",
  "query": "SELECT * FROM sales;",
  "query_hash": "a1b2c3d4e5f6...",
  "schedule": null,
  "api_key": "abcdef123456",
  "is_archived": false,
  "is_draft": false,
  "updated_at": "2025-08-01T12:00:00.000Z",
  "created_at": "2025-08-01T10:00:00.000Z",
  "data_source_id": 1,
  "options": {},
  "version": 1,
  "tags": ["sales", "reporting"],
  "is_safe": true,
  "user": {
    "id": 1,
    "name": "Admin"
  },
  "last_modified_by": null,
  "visualizations": [
    {
      "id": 789,
      "type": "TABLE",
      "name": "Sales Over Time",
      "description": "A chart showing sales trends.",
      "options": {},
      "updated_at": "2025-08-01T12:00:00.000Z",
      "created_at": "2025-08-01T10:00:00.000Z"
    }
  ],
  "can_edit": true
}
```

## POST /api/queries

To create a new query, you must provide a `name`, `query` text, and a `data_source_id`.

```json
{
  "name": "New Marketing Query",
  "query": "SELECT * FROM marketing_campaigns;",
  "data_source_id": 2
}
```

## POST /api/queries/<query_id>

To update an existing query, you can provide any of the mutable fields. The `version` field is required to prevent conflicts.

```json
{
  "name": "Updated Marketing Query",
  "query": "SELECT * FROM marketing_campaigns WHERE status = 'active';",
  "version": 1
}
```
