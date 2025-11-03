# Redash Dashboards API: JSON Payload Examples

**Version:** v25.8.0 (August 2025)
**Date:** 2025-08-01

This document provides a set of realistic JSON payload examples for the Redash Dashboards API. These examples are based on the data structures defined in the Redash source code.

## GET /api/dashboards

A typical response from this endpoint will be a paginated list of dashboards, with each dashboard object containing a summary of its properties. The `widgets` field is not included in this response.

```json
{
  "count": 1,
  "page": 1,
  "page_size": 25,
  "results": [
    {
      "id": 123,
      "slug": "sales-dashboard",
      "name": "Sales Dashboard",
      "user_id": 1,
      "user": {
        "id": 1,
        "name": "Admin",
        "email": "admin@example.com",
        "profile_image_url": "https://example.com/avatar.png"
      },
      "layout": [],
      "dashboard_filters_enabled": true,
      "options": {},
      "is_archived": false,
      "is_draft": false,
      "tags": ["sales", "kpi"],
      "updated_at": "2025-08-01T12:00:00.000Z",
      "created_at": "2025-08-01T10:00:00.000Z",
      "version": 2,
      "is_favorite": true
    }
  ]
}
```

## GET /api/dashboards/<dashboard_slug>

This endpoint returns the complete JSON structure for a single dashboard, including the `widgets` array and all nested objects.

```json
{
  "id": 123,
  "slug": "sales-dashboard",
  "name": "Sales Dashboard",
  "user_id": 1,
  "user": {
    "id": 1,
    "name": "Admin",
    "email": "admin@example.com",
    "profile_image_url": "https://example.com/avatar.png"
  },
  "layout": [
    [456]
  ],
  "dashboard_filters_enabled": true,
  "widgets": [
    {
      "id": 456,
      "width": 1,
      "options": {},
      "dashboard_id": 123,
      "text": null,
      "visualization": {
        "id": 789,
        "type": "TABLE",
        "name": "Sales Over Time",
        "description": "A chart showing sales trends.",
        "options": {},
        "query": {
          "id": 101,
          "name": "Get Sales Data",
          "description": "Retrieves sales data from the transactions table.",
          "query": "SELECT * FROM sales;",
          "query_hash": "a1b2c3d4e5f6...",
          "is_archived": false,
          "is_draft": false,
          "data_source_id": 1,
          "options": {},
          "updated_at": "2025-08-01T12:00:00.000Z",
          "created_at": "2025-08-01T10:00:00.000Z"
        },
        "updated_at": "2025-08-01T12:00:00.000Z",
        "created_at": "2025-08-01T10:00:00.000Z"
      },
      "updated_at": "2025-08-01T12:00:00.000Z",
      "created_at": "2025-08-01T10:00:00.000Z"
    }
  ],
  "options": {},
  "is_archived": false,
  "is_draft": false,
  "tags": ["sales", "kpi"],
  "updated_at": "2025-08-01T12:00:00.000Z",
  "created_at": "2025-08-01T10:00:00.000Z",
  "version": 2,
  "is_favorite": true,
  "can_edit": true
}
```

## POST /api/dashboards

To create a new dashboard, you must provide a `name`. The other fields will be set to their default values.

```json
{
  "name": "New Marketing Dashboard"
}
```

## POST /api/dashboards/<dashboard_id>

To update an existing dashboard, you can provide any of the mutable fields. The `version` field is required to prevent conflicts.

```json
{
  "name": "Updated Marketing Dashboard",
  "tags": ["marketing", "q3"],
  "is_draft": false,
  "version": 2
}
```
