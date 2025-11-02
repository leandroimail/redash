# Redash Query JSON Schema

**Version:** v25.8.0 (August 2025)
**Date:** 2025-11-02

This document provides a detailed description of the JSON structure used by the Redash Query API. It includes a breakdown of all fields, their data types, and their relationships.

## Field Descriptions

The following table describes the fields found in the JSON representation of a query.

### Query Object

| Path JSON | Type | Required | Description | Example |
|---|---|---|---|---|
| `id` | integer | Yes | The unique identifier for the query. | `101` |
| `latest_query_data_id` | integer | No | The ID of the most recent query result. Can be `null`. | `202` |
| `name` | string | Yes | The name of the query. | `"Get Sales Data"` |
| `description` | string | No | A description of the query. | `"Retrieves sales data from the transactions table."` |
| `query` | string | Yes | The SQL query text. | `"SELECT * FROM sales;"` |
| `query_hash` | string | Yes | A hash of the query text. | `"a1b2c3d4..."` |
| `schedule` | object | No | A dictionary describing the query's execution schedule. Can be `null`. | `{"interval": 3600, "until": "2026-01-01", "day_of_week": null, "time": null}` |
| `api_key` | string | Yes | The API key for this query. | `"abcdef123456"` |
| `is_archived` | boolean | Yes | A flag indicating if the query is archived. | `false` |
| `is_draft` | boolean | Yes | A flag indicating if the query is a draft. | `false` |
| `updated_at` | string | Yes | The ISO 8601 timestamp of the last update. | `"2025-08-01T12:00:00.000Z"` |
| `created_at` | string | Yes | The ISO 8601 timestamp of the creation date. | `"2025-08-01T10:00:00.000Z"` |
| `data_source_id` | integer | Yes | The ID of the data source this query belongs to. | `1` |
| `options` | object | Yes | A dictionary for query-specific options, including parameters. | `{"parameters": [{"name": "param1", "type": "text", "value": "value1"}]}` |
| `version` | integer | Yes | The version number of the query. | `1` |
| `tags` | array | No | A list of tags associated with the query. | `["sales", "reporting"]` |
| `is_safe` | boolean | Yes | A flag indicating if the query is safe from SQL injection. | `true` |
| `user` | object | Yes | An object containing details about the query creator. | `{"id": 1, "name": "Admin"}` |
| `last_modified_by` | object | No | An object containing details about the last user to modify the query. Can be `null`. | `{"id": 1, "name": "Admin"}` |
| `visualizations` | array | No | An array of visualization objects associated with the query. | `[...]` |
| `can_edit` | boolean | No | A flag indicating if the current user can edit the query. | `true` |
