# Redash Dashboards API Overview

**Version:** v25.8.0 (August 2025)
**Date:** 2025-11-02

This document provides a technical overview of the Redash API endpoints for managing dashboards. The purpose of this documentation is to serve as a comprehensive reference for developers who need to interact with the Dashboards API for tasks such as backup, automation, and migration of dashboards.

The documentation is based on a static analysis of the Redash source code and reflects the behavior of the API as of the version specified above.

## Endpoints

This documentation covers the following endpoints related to dashboards:

*   **`GET /api/dashboards`**: Lists all accessible dashboards in a paginated format.
*   **`POST /api/dashboards`**: Creates a new dashboard.
*   **`GET /api/dashboards/<dashboard_slug>`**: Retrieves the complete JSON structure of a single dashboard, including its widgets and visualizations.
*   **`POST /api/dashboards/<dashboard_id>`**: Modifies an existing dashboard.
*   **`DELETE /api/dashboards/<dashboard_slug>`**: Archives a dashboard.
