# Redash Visualization JSON Schema

**Version:** v25.8.0 (August 2025)
**Date:** 2025-08-01

This document provides a detailed description of the JSON structure used by the Redash Visualization API.

## Visualization Object

| Path JSON | Type | Required | Description | Example |
|---|---|---|---|---|
| `id` | integer | Yes | The unique identifier for the visualization. | `789` |
| `type` | string | Yes | The type of visualization. Can be `TABLE`, `CHART`, `COUNTER`, `PIVOT`, etc. | `"TABLE"` |
| `name` | string | Yes | The name of the visualization. | `"Sales Over Time"` |
| `description` | string | No | A description of the visualization. | `"A chart showing sales trends."` |
| `options` | object | Yes | A dictionary for visualization-specific options. The structure of this object is determined by the `type`. For a detailed breakdown of the options for each visualization type, please see the [Visualization Options Deep Dive](./visualization_options_deep_dive.md). | `{"globalSeriesType": "column"}` |
| `query` | object | Yes | The query object that provides data for this visualization. For details, see the [Redash Query JSON Schema](./queries_schema.md). | `{...}` |
| `updated_at` | string | Yes | The ISO 8601 timestamp of the last update. | `"2025-08-01T12:00:00.000Z"` |
| `created_at` | string | Yes | The ISO 8601 timestamp of the creation date. | `"2025-08-01T10:00:00.000Z"` |
