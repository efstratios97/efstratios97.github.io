# Sophrosyne - Recommendation Service API

This API provides endpoints to manage and trigger **Action Recommendations** in Sophrosyne.  
Action Recommendations provide guidance for resolving alerts that cannot be handled automatically by Actions.  

### Core Requirements
- **Action Recommendation ID (`id`)** – Identifies the recommendation to retrieve, trigger, or acknowledge.
- **API Key (`apikey`)** – Required for authentication. It can be passed as a query parameter or as a Bearer token in the Authorization header.

---

## Endpoints Overview

The API supports:
1. Retrieving all active Action Recommendations.
2. Retrieving a specific Action Recommendation by ID.
3. Triggering an Action Recommendation manually.
4. Acknowledging an Action Recommendation to stop further prompts.

---

## **1. Get All Active Action Recommendations**

**Endpoint:**  
`GET /api/v1/actionrecommendations`

**Description:**  
Retrieves all active Action Recommendations associated with the provided API key.

**Parameters:**
- `apikey` (query or header) – API key for authentication.

**Responses:**
- `200` – Returns an array of active Action Recommendations.
- `401` – Unauthorized.

**Example Request:**
```bash
curl -X GET "https://example.com/api/v1/actionrecommendations?apikey=12345"
````

**Example Response:**

```json
[
  {
    "id": "rec_1",
    "name": "Restart Web Service",
    "description": "<strong>Follow these steps:</strong> ...",
    "contact": "ops-team@company.com"
  }
]
```

---

## **2. Get an Action Recommendation by ID**

**Endpoint:**
`GET /api/v1/actionrecommendation/{id}`

**Description:**
Retrieves a specific active Action Recommendation by ID.

**Parameters:**

* `id` (path) – The ID of the Action Recommendation to retrieve.
* `apikey` (query or header) – API key for authentication.

**Responses:**

* `200` – Returns the requested Action Recommendation.
* `204` – The Action Recommendation is not active.
* `404` – Invalid ID supplied.
* `401` – Unauthorized.

**Example Request:**

```bash
curl -X GET "https://example.com/api/v1/actionrecommendation/rec_1?apikey=12345"
```

---

## **3. Trigger an Action Recommendation**

**Endpoint:**
`POST /api/v1/actionrecommendation/{id}/trigger`

**Description:**
Manually triggers an Action Recommendation by ID.

**Parameters:**

* `id` (path) – The ID of the Action Recommendation to trigger.
* `apikey` (query or header) – API key for authentication.

**Responses:**

* `200` – Trigger successful.
* `400` – Invalid ID supplied.
* `404` – Action Recommendation not found.
* `401` – Unauthorized.

**Example Request:**

```bash
curl -X POST "https://example.com/api/v1/actionrecommendation/rec_1/trigger?apikey=12345"
```

---

## **4. Acknowledge an Action Recommendation**

**Endpoint:**
`POST /api/v1/actionrecommendation/{id}/acknowledge`

**Description:**
Acknowledges the specified Action Recommendation, stopping further prompts for it.

**Parameters:**

* `id` (path) – The ID of the Action Recommendation to acknowledge.
* `apikey` (query or header) – API key for authentication.

**Responses:**

* `200` – Acknowledgment successful.
* `400` – Invalid ID supplied.
* `404` – Action Recommendation not found.
* `401` – Unauthorized.

**Example Request:**

```bash
curl -X POST "https://example.com/api/v1/actionrecommendation/rec_1/acknowledge?apikey=12345"
```

---

## Summary

* **GET** endpoints are used to **retrieve** active recommendations.
* **POST** endpoints allow you to **trigger** or **acknowledge** a recommendation.
* All endpoints require a valid **API key** for authentication.
