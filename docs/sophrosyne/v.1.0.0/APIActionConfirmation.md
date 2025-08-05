# Sophrosyne - Action Confirmation Service API

This API provides endpoints for handling **Action Confirmations** in Sophrosyne.  
Some Actions and Dynamic Actions require explicit user confirmation before execution.  
These endpoints allow retrieving pending confirmations and programmatically confirming or rejecting them.

### Core Requirements
- **Action Confirmation ID (`id`)** – Identifies the confirmation to retrieve, confirm, or reject.  
  For Dynamic Actions, this ID is not the same as the Dynamic Action’s ID.  
- **API Key (`apikey`)** – Required for authentication. It can be passed as a query parameter or Bearer token.

---

## Endpoints Overview

The API supports:
1. Retrieving all outstanding action confirmations.
2. Retrieving a specific action confirmation by ID.
3. Confirming an action.
4. Rejecting an action.

---

## **1. Get All Outstanding Action Confirmations**

**Endpoint:**  
`GET /api/v1/actionconfirmations`

**Description:**  
Retrieves all outstanding action confirmations associated with the provided API key.

**Parameters:**
- `apikey` (query or header) – API key for authentication.

**Responses:**
- `200` – Returns an array of outstanding confirmations.
- `401` – Unauthorized.

**Example Request:**
```bash
curl -X GET "https://example.com/api/v1/actionconfirmations?apikey=12345"
```

**Example Response:**
```json
[
  {
    "id": "conf_123",
    "actionName": "Restart Database",
    "status": "pending"
  }
]
```

---

## **2. Get an Action Confirmation by ID**

**Endpoint:**  
`GET /api/v1/actionconfirmation/{id}`

**Description:**  
Retrieves a specific outstanding action confirmation by its ID.

**Parameters:**
- `id` (path) – The ID of the action confirmation.  
- `apikey` (query or header) – API key for authentication.

**Responses:**
- `200` – Returns the requested confirmation details.
- `401` – Unauthorized.

**Example Request:**
```bash
curl -X GET "https://example.com/api/v1/actionconfirmation/conf_123?apikey=12345"
```

---

## **3. Confirm an Action**

**Endpoint:**  
`POST /api/v1/actionconfirmation/anyaction/{id}/confirm`

**Description:**  
Confirms any type of Action by ID, allowing it to proceed with execution.

**Parameters:**
- `id` (path) – The Action Confirmation ID (for simple Actions this equals the Action ID).  
- `apikey` (query or header) – API key for authentication.

**Responses:**
- `200` – Confirmation successful.
- `400` – Invalid ID supplied.
- `404` – Action not found.
- `401` – Unauthorized.

**Example Request:**
```bash
curl -X POST "https://example.com/api/v1/actionconfirmation/anyaction/conf_123/confirm?apikey=12345"
```

---

## **4. Reject an Action**

**Endpoint:**  
`POST /api/v1/actionconfirmation/anyaction/{id}/reject`

**Description:**  
Rejects an Action by ID, preventing its execution.

**Parameters:**
- `id` (path) – The Action Confirmation ID (for simple Actions this equals the Action ID).  
- `apikey` (query or header) – API key for authentication.

**Responses:**
- `200` – Rejection successful.
- `400` – Invalid ID supplied.
- `404` – Action not found.
- `401` – Unauthorized.

**Example Request:**
```bash
curl -X POST "https://example.com/api/v1/actionconfirmation/anyaction/conf_123/reject?apikey=12345"
```

---

## Summary

- Use **GET** endpoints to check pending confirmations.  
- Use **POST confirm** to allow execution.  
- Use **POST reject** to block execution.  
- Always include a valid **API key** for authentication.  
