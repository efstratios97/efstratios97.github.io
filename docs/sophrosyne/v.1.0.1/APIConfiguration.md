# Sophrosyne - Configuration Service API

This API provides endpoints to **import** and **manage** the configuration of a Sophrosyne instance.  
The configuration is typically stored in `sophrosyne.json`. The endpoints allow importing configurations either from a file on the server or directly from JSON input, with options to merge or overwrite existing configurations.

---

## Endpoints Overview

The API includes endpoints for:
1. Importing configuration from the `sophrosyne.json` file without overwriting existing data.
2. Forcing an import from the configuration file, overwriting existing data.
3. Importing configuration from a provided JSON payload (merge mode).
4. Forcing an import from a provided JSON payload (overwrite mode).

---

## **1. Import Configuration from File (Merge Mode)**

**Endpoint:**  
`POST /api/v1/configuration/import_from_config_file`  

**Description:**  
Imports configuration from the server's `sophrosyne.json` without erasing the currently imported configuration.  
Conflicting entries may be skipped. Use the `/force` endpoint to overwrite.

**Responses:**
- `200` – Import successful.
- `207` – Partial success (some entries may have been skipped).
- `401` – Unauthorized.

**Example Request:**
```bash
curl -X POST "https://example.com/api/v1/configuration/import_from_config_file" \
  -H "Authorization: Bearer <API_KEY>"
````

---

## **2. Import Configuration from File (Force Overwrite)**

**Endpoint:**
`POST /api/v1/configuration/import_from_config_file/force`

**Description:**
Forces the import of `sophrosyne.json` and **overwrites** the existing configuration.
**Warning:** This may cause loss of local changes. Backup your current configuration before using this endpoint.

**Responses:**

* `200` – Import successful.
* `207` – Partial success.
* `401` – Unauthorized.

**Example Request:**

```bash
curl -X POST "https://example.com/api/v1/configuration/import_from_config_file/force" \
  -H "Authorization: Bearer <API_KEY>"
```

---

## **3. Import Configuration from JSON (Merge Mode)**

**Endpoint:**
`POST /api/v1/configuration/import`

**Description:**
Imports configuration provided as JSON in the request body without erasing existing configuration.
Conflicting entries may be skipped. Use `/import/force` to overwrite.

**Request Body:**
A JSON object representing the exported `sophrosyne.json` configuration.

**Responses:**

* `200` – Import successful.
* `207` – Partial success.
* `401` – Unauthorized.

**Example Request:**

```bash
curl -X POST "https://example.com/api/v1/configuration/import" \
  -H "Authorization: Bearer <API_KEY>" \
  -H "Content-Type: application/json" \
  -d '{
    "actions": [],
    "dynamicActions": [],
    "controlPanels": []
  }'
```

---

## **4. Import Configuration from JSON (Force Overwrite)**

**Endpoint:**
`POST /api/v1/configuration/import/force`

**Description:**
Forces the import of the configuration provided in the JSON body and **overwrites** the existing configuration.
**Warning:** This action may cause loss of current configuration. Always export and backup before using.

**Request Body:**
A JSON object representing the exported `sophrosyne.json` configuration.

**Responses:**

* `200` – Import successful.
* `207` – Partial success.
* `401` – Unauthorized.

**Example Request:**

```bash
curl -X POST "https://example.com/api/v1/configuration/import/force" \
  -H "Authorization: Bearer <API_KEY>" \
  -H "Content-Type: application/json" \
  -d '{
    "actions": [],
    "dynamicActions": [],
    "controlPanels": []
  }'
```

---

## Summary

* Use **merge endpoints** (`/import` and `/import_from_config_file`) to add new configuration entries without overwriting existing ones.
* Use **force endpoints** (`/import/force` and `/import_from_config_file/force`) to overwrite the existing configuration completely.
* Always back up your configuration before performing a forced import to prevent data loss.

