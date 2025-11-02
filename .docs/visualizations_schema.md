# Redash Visualization JSON Schema

**Version:** v10.1.0
**Date:** 2023-11-02

This document provides a detailed description of the JSON structure used by the Redash Visualization API. It includes a breakdown of all fields, their data types, and their relationships.

## Field Descriptions

The following table describes the fields found in the JSON representation of a visualization.

### Visualization Object

| Path JSON | Type | Required | Description | Example |
|---|---|---|---|---|
| `id` | integer | Yes | The unique identifier for the visualization. | `789` |
| `type` | string | Yes | The type of visualization. Can be `TABLE`, `CHART`, `COUNTER`, `PIVOT`, etc. | `"TABLE"` |
| `name` | string | Yes | The name of the visualization. | `"Sales Over Time"` |
| `description` | string | No | A description of the visualization. | `"A chart showing sales trends."` |
| `options` | object | Yes | A dictionary for visualization-specific options. The structure of this object depends on the `type` of the visualization. | `{"globalSeriesType": "column"}` |
| `query` | object | Yes | The query object that provides data for this visualization. For details, see the [Redash Query JSON Schema](./queries_schema.md). | `{...}` |
| `updated_at` | string | Yes | The ISO 8601 timestamp of the last update. | `"2023-11-01T12:00:00.000Z"` |
| `created_at` | string | Yes | The ISO 8601 timestamp of the creation date. | `"2023-11-01T10:00:00.000Z"` |
