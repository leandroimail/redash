# Redash Visualization JSON Schema

**Version:** v25.8.0 (August 2025)
**Date:** 2025-08-01

This document provides a detailed description of the JSON structure used by the Redash Visualization API, with a focus on the `options` field for the most common visualization types.

## Visualization Object

| Path JSON | Type | Required | Description | Example |
|---|---|---|---|---|
| `id` | integer | Yes | The unique identifier for the visualization. | `789` |
| `type` | string | Yes | The type of visualization. Can be `TABLE`, `CHART`, `COUNTER`, `PIVOT`, etc. | `"TABLE"` |
| `name` | string | Yes | The name of the visualization. | `"Sales Over Time"` |
| `description` | string | No | A description of the visualization. | `"A chart showing sales trends."` |
| `options` | object | Yes | A dictionary for visualization-specific options. The structure of this object is determined by the `type`. | `{"globalSeriesType": "column"}` |
| `query` | object | Yes | The query object that provides data for this visualization. For details, see the [Redash Query JSON Schema](./queries_schema.md). | `{...}` |
| `updated_at` | string | Yes | The ISO 8601 timestamp of the last update. | `"2025-08-01T12:00:00.000Z"` |
| `created_at` | string | Yes | The ISO 8601 timestamp of the creation date. | `"2025-08-01T10:00:00.000Z"` |

---

## Visualization Options by Type

### `CHART`

| Key | Type | Description |
|---|---|---|
| `globalSeriesType` | string | The default chart type (e.g., `column`, `line`, `area`, `pie`, `scatter`). |
| `columnMapping` | object | Maps query columns to chart axes (e.g., `{"name": "x", "sales": "y"}`). |
| `sortX` | boolean | Whether to sort the X-axis values. |
| `legend.enabled` | boolean | Toggles the visibility of the chart legend. |
| `legend.placement`| string | `auto` or `h` (horizontal). |
| `legend.traceorder`| string | `normal` or `reversed`. |
| `xAxis.type` | string | The type of the X-axis (`-` for auto, `datetime`, `category`). |
| `xAxis.labels.enabled` | boolean | Toggles the visibility of the X-axis labels. |
| `yAxis` | array | An array of objects, each configuring a Y-axis. |
| `series.stacking` | string | Set to `stack` for stacked bar/area charts. |
| `seriesOptions` | object | Overrides for specific series, keyed by the series name. |
| `showDataLabels` | boolean | Toggles the visibility of data labels on the chart. |
| `numberFormat` | string | A number format string (e.g., `0,0.00`). |
| `percentFormat` | string | A percent format string (e.g., `0.00%`). |
| `dateTimeFormat`| string | A date/time format string (e.g., `DD/MM/YYYY HH:mm`). |
| `missingValuesAsZero` | boolean | Whether to treat `null` values as `0`. Defaults to `true`. |

### `COUNTER`

| Key | Type | Description |
|---|---|---|
| `counterLabel` | string | A custom label to display above the counter value. |
| `counterColName` | string | The name of the column containing the primary counter value. |
| `rowNumber` | integer | The row number (0-indexed) to take the counter value from. |
| `targetColName` | string | The name of the column containing the target value for comparison. |
| `targetRowNumber`| integer | The row number (0-indexed) to take the target value from. |
| `countRow` | boolean | If `true`, the counter will display the total number of rows. |
| `stringDecimal` | integer | The number of decimal places to display. |
| `stringDecChar` | string | The character to use for the decimal point. |
| `stringThouSep` | string | The character to use for the thousands separator. |
| `stringPrefix` | string | A prefix to display before the counter value (e.g., `$`). |
| `stringSuffix` | string | A suffix to display after the counter value (e.g., `%`). |
| `formatTargetValue` | boolean | If `true`, the target value will be formatted using the same rules as the primary value. |

### `PIVOT`

| Key | Type | Description |
|---|---|---|
| `controls.enabled`| boolean | If `true`, the pivot table controls (for rows, columns, etc.) are visible to the user. |
| `rendererOptions.table.rowTotals` | boolean | Toggles the visibility of row totals. |
| `rendererOptions.table.colTotals` | boolean | Toggles the visibility of column totals. |

### `TABLE`

| Key | Type | Description |
|---|---|---|
| `itemsPerPage` | integer | The number of rows to display per page. |
| `columns` | array | An array of objects, each configuring a column. See "Table Column Options" below. |

#### Table Column Options

Each object in the `columns` array has the following structure:

| Key | Type | Description |
|---|---|---|
| `name` | string | The name of the column from the query result. |
| `title` | string | A custom display title for the column header. |
| `visible` | boolean | Toggles the visibility of the column. |
| `alignContent` | string | The horizontal alignment of the cell content (`left`, `center`, `right`). |
| `allowSearch` | boolean | If `true`, this column will be included in table searches. |
| `displayAs` | string | How to display the cell content (`string`, `number`, `boolean`, `image`, `json`, `link`). |

*Note: Depending on the `displayAs` type, there may be additional options for that column (e.g., a `link` type will have a `linkUrlTemplate` key).*
