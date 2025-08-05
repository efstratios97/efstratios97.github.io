# Sophrosyne - Action Archive Service API

This API allows you to **retrieve the history of executed Actions** within your Sophrosyne system.  
You can query all archived actions, filter by a specific Action ID, or retrieve only the most recent execution.

### Core Requirements
- **Action ID (`actionId`)** – Used to filter archive results or fetch the latest execution of a specific Action.
- **API Key (`apikey`)** – Required for authentication (can be passed as a Bearer token or query parameter).

---

## Endpoints Overview

The API supports:
1. Retrieving all archived actions.
2. Retrieving archived actions filtered by Action ID.
3. Retrieving only the latest archived execution of a specific Action.

---

## **1. Get All Archived Actions**

**Endpoint:**  
`GET /api/v1/archive/actions`

**Description:**  
Fetches the complete archive of all executed Actions in the system.

**Responses:**
- `200` – Returns an array of archived Action objects.
- `401` – Unauthorized.

**Example Request:**
```bash
curl -X GET "https://example.com/api/v1/archive/actions" \
  -H "Authorization: Bearer <API_KEY>"
````

**Example Response:**

```json
[
  {
    "actionId": "act_123",
    "name": "Database Backup",
    "status": "success",
    "timestamp": "2025-08-05T10:00:00Z"
  },
  {
    "actionId": "act_124",
    "name": "Restart Service",
    "status": "failed",
    "timestamp": "2025-08-04T09:15:00Z"
  }
]
```

---

## **2. Get Archived Actions by Action ID**

**Endpoint:**
`GET /api/v1/archive/action/{actionId}`

**Description:**
Fetches all archived executions for the specified `actionId`.

**Parameters:**

* `actionId` (path) – The ID of the Action whose executions should be retrieved.

**Responses:**

* `200` – Returns an array of archived executions for the given Action ID.
* `400` – Invalid Action ID supplied.
* `404` – No archive found for the specified Action ID.
* `401` – Unauthorized.

**Example Request:**

```bash
curl -X GET "https://example.com/api/v1/archive/action/act_123" \
  -H "Authorization: Bearer <API_KEY>"
```

---

## **3. Get the Latest Archived Action by Action ID**

**Endpoint:**
`GET /api/v1/archive/action/{actionId}/last`

**Description:**
Fetches **only the latest** archived execution for the specified `actionId`.

**Parameters:**

* `actionId` (path) – The ID of the Action whose most recent execution should be retrieved.

**Responses:**

* `200` – Returns the latest archived execution for the given Action ID.
* `400` – Invalid Action ID supplied.
* `404` – No archive found for the specified Action ID.
* `401` – Unauthorized.

**Example Request:**

```bash
curl -X GET "https://example.com/api/v1/archive/action/act_123/last" \
  -H "Authorization: Bearer <API_KEY>"
```

**Example Response:**

```json
{
  "actionId": "act_123",
  "name": "Database Backup",
  "status": "success",
  "timestamp": "2025-08-05T10:00:00Z"
}
```

---

## Summary

* Use `/archive/actions` to get the full history of executed Actions.
* Use `/archive/action/{actionId}` to filter results for a specific Action ID.
* Use `/archive/action/{actionId}/last` to retrieve only the **latest** execution of an Action.
* Always include a valid **API key** for authentication.

