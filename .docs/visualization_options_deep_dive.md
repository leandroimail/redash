# Redash Visualization Options: A Deep Dive

**Version:** v25.8.0 (August 2025)
**Date:** 2025-08-01

This document provides an exhaustive reference for the `options` object for the most common visualization types in Redash: `CHART`, `COUNTER`, `PIVOT`, and `TABLE`. The information is based on a deep analysis of the Redash frontend and backend source code.

---

## `CHART`

The `CHART` visualization is highly configurable. Its `options` object controls everything from the chart type to the appearance of the axes and series.

### Chart Sub-Types

The specific type of chart is determined by the `globalSeriesType` property. The available types are:
*   `line`
*   `column` (Bar Chart)
*   `area`
*   `pie`
*   `scatter`
*   `bubble`
*   `heatmap`
*   `box`

### General Chart Options

| Key | Type | Description |
|---|---|---|
| `globalSeriesType` | string | The default chart type for all series. |
| `columnMapping` | object | Maps query columns to chart axes (e.g., `{"name": "x", "sales": "y"}`). The keys are the column names from the query, and the values are the axes to map them to. |
| `sortX` | boolean | If `true`, the X-axis values will be sorted. |
| `showDataLabels` | boolean | If `true`, data labels will be displayed on the chart. |
| `numberFormat` | string | A number format string (e.g., `0,0.00`). |
| `percentFormat` | string | A percent format string (e.g., `0.00%`). |
| `dateTimeFormat`| string | A date/time format string (e.g., `DD/MM/YYYY HH:mm`). |
| `textFormat` | string | A template for formatting data labels (e.g., `{{ @@yPercent }}`). |
| `missingValuesAsZero` | boolean | If `true`, `null` values will be treated as `0`. Defaults to `true`. |

### Legend Options

| Key | Type | Description |
|---|---|---|
| `legend.enabled` | boolean | Toggles the visibility of the chart legend. |
| `legend.placement`| string | `auto` or `h` (horizontal). |
| `legend.traceorder`| string | `normal` or `reversed`. |

### Axis Options

| Key | Type | Description |
|---|---|---|
| `xAxis.type` | string | The type of the X-axis (`-` for auto, `datetime`, `category`, `linear`). |
| `xAxis.labels.enabled` | boolean | Toggles the visibility of the X-axis labels. |
| `yAxis` | array | An array of objects, each configuring a Y-axis. Each object can have a `type` (`linear`, `logarithmic`, `datetime`, `category`) and an `opposite` (boolean) property. |
| `alignYAxesAtZero` | boolean | If `true`, both Y-axes will be aligned at the `0` value. |

### Series Options

| Key | Type | Description |
|---|---|---|
| `series.stacking` | string | Set to `stack` for stacked bar/area charts. |
| `seriesOptions` | object | An object containing overrides for specific series, keyed by the series name. Each series can have its own `type`, `yAxis`, etc. |

---

## `COUNTER`

The `COUNTER` visualization is used to display a single, important value.

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

---

## `PIVOT`

The `PIVOT` visualization is used to create a pivot table from the query results.

| Key | Type | Description |
|---|---|---|
| `controls.enabled`| boolean | If `true`, the pivot table controls (for rows, columns, etc.) are visible to the user. |
| `rendererOptions.table.rowTotals` | boolean | If `true`, row totals will be displayed. |
| `rendererOptions.table.colTotals` | boolean | If `true`, column totals will be displayed. |

---

## `TABLE`

The `TABLE` visualization is used to display the raw query results in a tabular format.

| Key | Type | Description |
|---|---|---|
| `itemsPerPage` | integer | The number of rows to display per page. |
| `columns` | array | An array of objects, each configuring a column. See "Table Column Options" below. |

### Table Column Options

Each object in the `columns` array has the following structure:

| Key | Type | Description |
|---|---|---|
| `name` | string | The name of the column from the query result. |
| `title` | string | A custom display title for the column header. |
| `visible` | boolean | If `true`, the column will be visible. |
| `alignContent` | string | The horizontal alignment of the cell content (`left`, `center`, `right`). |
| `allowSearch` | boolean | If `true`, this column will be included in table searches. |
| `displayAs` | string | How to display the cell content (`string`, `number`, `boolean`, `image`, `json`, `link`). |
