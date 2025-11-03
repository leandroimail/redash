# Redash Visualization API: JSON Payload Examples

**Version:** v25.8.0 (August 2025)
**Date:** 2025-08-01

This document provides a set of realistic JSON payload examples for the Redash Visualization API.

## POST /api/visualizations

To create a new visualization, you must provide a `query_id`, a `name`, a `type`, and an `options` object.

```json
{
  "query_id": 101,
  "name": "Monthly Sales Chart",
  "description": "A bar chart showing sales per month.",
  "type": "CHART",
  "options": {
    "globalSeriesType": "column",
    "columnMapping": {
      "month": "x",
      "sales": "y"
    }
  }
}
```

## POST /api/visualizations/<visualization_id>

To update an existing visualization, you can provide any of the mutable fields.

```json
{
  "name": "Monthly Sales (Updated)",
  "options": {
    "globalSeriesType": "line",
    "columnMapping": {
      "month": "x",
      "sales": "y"
    }
  }
}
```
