# Redash Visualization API Overview

**Version:** v25.8.0 (August 2025)
**Date:** 2025-08-01

This document provides a technical overview of the Redash API endpoints for managing visualizations. Visualizations are representations of data from a query, such as a chart or a table, and are a core component of Redash dashboards.

The documentation is based on a static analysis of the Redash source code and reflects the behavior of the API as of the version specified above.

## Endpoints

This documentation covers the following endpoints for managing visualizations:

*   **`POST /api/visualizations`**: Creates a new visualization for a given query.
*   **`POST /api/visualizations/<visualization_id>`**: Modifies an existing visualization.
*   **`DELETE /api/visualizations/<visualization_id>`**: Deletes a visualization.

*Note: There is no `GET` endpoint for listing all visualizations or retrieving a single visualization by itself. Visualizations are typically retrieved as part of a Query or Dashboard object.*
