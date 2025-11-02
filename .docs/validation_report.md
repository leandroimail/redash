# Redash Dashboards API: Validation Report

**Version:** v25.8.0 (August 2025)
**Date:** 2025-11-02

This document outlines the validation process and findings from the analysis of the Redash Dashboards API. The documentation and JSON schema were generated based on a static analysis of the Redash source code.

## Findings and Observations

The following are some observations and potential discrepancies found during the analysis:

1.  **Serialization Logic:** The serialization of dashboard objects is not handled in a dedicated serializer file (e.g., `redash/serializers/dashboards.py`). Instead, the logic is located within the `serialize_dashboard` function in `redash/serializers/__init__.py`. This is a minor structural observation.

2.  **`slug` vs. `id`:** The API uses both `dashboard_slug` and `dashboard_id` to identify dashboards in different endpoints. For example, `GET /api/dashboards/<dashboard_slug>` uses the slug, while `POST /api/dashboards/<dashboard_id>` uses the ID. This is a potential point of confusion for developers and should be clearly documented.

3.  **`layout` Field:** The `Dashboard` model in `redash/models/__init__.py` notes that the `layout` field is "no longer used, but kept so we know how to render old dashboards." However, the field is still present in the API responses and appears to be actively used in the frontend. This documentation assumes that the field is still in use.

4.  **`widgets` Field:** The `widgets` array is only included in the response for `GET /api/dashboards/<dashboard_slug>`. It is not present in the response for `GET /api/dashboards`. This is an important distinction for developers to be aware of.

5.  **`can_edit` Field:** The `can_edit` field is dynamically added to the serialized dashboard object in `redash/handlers/dashboards.py` and is not part of the `Dashboard` model itself. This field is only present when retrieving a single dashboard.

## Conclusion

The generated documentation and JSON schema are a faithful representation of the Redash Dashboards API as of the specified version. The observations noted in this report should be taken into consideration by developers when working with the API.
