# Redash Query API: Validation Report

**Version:** v10.1.0
**Date:** 2023-11-02

This document outlines the validation process and findings from the analysis of the Redash Query API.

## Findings and Observations

1.  **Serialization Logic:** Similar to the Dashboard API, the serialization logic for queries is handled in `redash/serializers/__init__.py` by the `serialize_query` function, rather than a dedicated file.

2.  **`query` vs. `query_text`:** In the `Query` model (`redash/models/__init__.py`), the field for the SQL query is named `query_text`. However, in the API requests and responses, this field is named `query`. The `QuerySerializer` handles this mapping.

3.  **`can_edit` Field:** The `can_edit` field is dynamically added to the serialized query object in `redash/handlers/queries.py` and is not part of the `Query` model itself. This field is only present when retrieving a single query.

4.  **Dropdown Queries:** The API includes logic to handle dropdown queries (queries used to populate the values of dashboard parameters). When creating or updating a query, the API checks for permissions on any associated dropdown queries.

5.  **Extensive Endpoints:** The Query API is more extensive than the Dashboard API, with numerous endpoints for searching, filtering, and managing queries in various ways (e.g., by user, by tag, by favorite status).

## Conclusion

The generated documentation and JSON schema are a faithful representation of the Redash Query API as of the specified version.
