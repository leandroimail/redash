# Redash Visualization JSON Schema

**Version:** v25.8.0 (August 2025)
**Date:** 2025-08-01

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
| `options` | object | Yes | A dictionary for visualization-specific options. The structure of this object is determined by the `type` of the visualization and is managed by the frontend. See the "Visualization Options" section for more details. | `{"globalSeriesType": "column"}` |
| `query` | object | Yes | The query object that provides data for this visualization. For details, see the [Redash Query JSON Schema](./queries_schema.md). | `{...}` |
| `updated_at` | string | Yes | The ISO 8601 timestamp of the last update. | `"2025-08-01T12:00:00.000Z"` |
| `created_at` | string | Yes | The ISO 8601 timestamp of the creation date. | `"2025-08-01T10:00:00.000Z"` |

## Visualization Options

The `options` object contains the configuration for a specific visualization. Its structure is highly dependent on the visualization `type`. While the backend treats this as a generic JSON object, the frontend uses it to configure the appearance and behavior of the visualization.

Below are some common keys found in the `options` object for `CHART` visualizations:

| Key | Type | Description |
|---|---|---|
| `globalSeriesType` | string | The default chart type for all series (e.g., `column`, `line`, `area`, `pie`). |
| `columnMapping` | object | A mapping of query columns to chart axes (e.g., `{"name": "x", "sales": "y"}`). |
| `seriesOptions` | object | Overrides for specific series, keyed by the series name. |
| ` xAxis` | object | Configuration for the X-axis (e.g., type, labels). |
| `yAxis` | array | An array of configuration objects for the Y-axes. |
