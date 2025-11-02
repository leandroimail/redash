# Redash Query API Overview

**Version:** v25.8.0 (August 2025)
**Date:** 2025-11-02

This document provides a technical overview of the Redash API endpoints for managing queries. It is intended as a comprehensive reference for developers who need to interact with the Query API for automation, integration, or migration purposes.

The documentation is based on a static analysis of the Redash source code and reflects the behavior of the API as of the version specified above.

## Core Endpoints

This documentation primarily covers the core CRUD (Create, Read, Update, Delete) endpoints for managing queries:

*   **`GET /api/queries`**: Lists all accessible queries in a paginated format.
*   **`POST /api/queries`**: Creates a new query.
*   **`GET /api/queries/<query_id>`**: Retrieves a single query.
*   **`POST /api/queries/<query_id>`**: Modifies an existing query.
*   **`DELETE /api/queries/<query_id>`**: Archives a query.

## Additional Endpoints

The Query API also includes several other endpoints for more specific actions:

*   **`GET /api/queries/archive`**: Lists all archived queries.
*   **`GET /api/queries/favorites`**: Lists the current user's favorite queries.
*   **`GET /api/queries/my`**: Lists the queries created by the current user.
*   **`GET /api/queries/recent`**: Lists recently used queries.
*   **`GET /api/queries/tags`**: Retrieves all tags used on queries.
*   **`POST /api/queries/format`**: Formats an SQL query.
*   **`POST /api/queries/<query_id>/fork`**: Creates a copy of an existing query.
*   **`POST /api/queries/<query_id>/refresh`**: Executes a query and updates its results.
*   **`POST /api/queries/<query_id>/regenerate_api_key`**: Generates a new API key for the query.
