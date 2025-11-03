# Redash Query JSON Schema

**Version:** v25.8.0 (August 2025)
**Date:** 2025-08-01

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
| `query` | string | Yes | The SQL query text, which may contain mustache-style parameters (e.g., `{{param}}`). | `"SELECT * FROM sales WHERE region = '{{region}}';"` |
| `query_hash` | string | Yes | A hash of the query text. | `"a1b2c3d4..."` |
| `schedule` | object | No | A dictionary describing the query's execution schedule. Can be `null`. | `{"interval": 3600, "until": "2026-01-01", "day_of_week": null, "time": null}` |
| `api_key` | string | Yes | The API key for this query. | `"abcdef123456"` |
| `is_archived` | boolean | Yes | A flag indicating if the query is archived. | `false` |
| `is_draft` | boolean | Yes | A flag indicating if the query is a draft. | `false` |
| `updated_at` | string | Yes | The ISO 8601 timestamp of the last update. | `"2025-08-01T12:00:00.000Z"` |
| `created_at` | string | Yes | The ISO 8601 timestamp of the creation date. | `"2025-08-01T10:00:00.000Z"` |
| `data_source_id` | integer | Yes | The ID of the data source this query belongs to. | `1` |
| `options` | object | Yes | A dictionary for query-specific options. The most important key is `parameters`. | `{"parameters": [...]}` |
| `version` | integer | Yes | The version number of the query. | `1` |
| `tags` | array | No | A list of tags associated with the query. | `["sales", "reporting"]` |
| `is_safe` | boolean | Yes | A flag indicating if the query is safe from SQL injection. | `true` |
| `user` | object | Yes | An object containing details about the query creator. | `{"id": 1, "name": "Admin"}` |
| `last_modified_by` | object | No | An object containing details about the last user to modify the query. Can be `null`. | `{"id": 1, "name": "Admin"}` |
| `visualizations` | array | No | An array of visualization objects associated with the query. For details, see the [Redash Visualization JSON Schema](./visualizations_schema.md). | `[...]` |
| `can_edit` | boolean | No | A flag indicating if the current user can edit the query. | `true` |

## Query Parameters

The `options` object of a query contains a `parameters` array, which defines the parameters that can be used in the query text. Each object in the `parameters` array has the following structure:

| Key | Type | Description |
|---|---|---|
| `name` | string | The name of the parameter, used in the query text (e.g., `{{name}}`). |
| `title` | string | The display title for the parameter in the UI. |
| `type` | string | The type of the parameter. See the "Parameter Types" section for details. |
| `value` | any | The default value for the parameter. |
| `global` | boolean | A flag indicating if the parameter is a global dashboard parameter. |

### Parameter Types

The `type` key determines the kind of input presented to the user and the validation applied to the parameter's value. The following types are supported:

| Type | Description |
|---|---|
| `text` | A simple text input. |
| `text-pattern` | A text input that is validated against a regular expression defined in the `regex` key of the parameter object. |
| `number` | A number input. |
| `enum` | A dropdown list of predefined values. The values are provided in the `enumOptions` key as a newline-separated string. |
| `query` | A dropdown list of values returned by another query. The ID of the query to run is provided in the `queryId` key. |
| `date` | A date picker. |
| `datetime-local` | A date and time picker. |
| `datetime-with-seconds` | A date and time picker with seconds. |
| `date-range` | A date range picker. |
| `datetime-range` | A date and time range picker. |
| `datetime-range-with-seconds` | A date and time range picker with seconds. |
