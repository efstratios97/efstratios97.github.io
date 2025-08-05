# Sophrosyne - Action API

This API provides endpoints to trigger and manage **Actions** and **Dynamic Actions** in Sophrosyne.  

### Core Requirements
- **Action ID (`id`)** – The unique identifier for the Action or Dynamic Action.
- **API Key (`apikey`)** – Required for authentication. It can be passed as a query parameter or as a Bearer token in the Authorization header.
- These values can be obtained from your Sophrosyne Web-UI.

---

## Endpoints Overview

The API offers the following capabilities:
1. Trigger a **simple Action** without parameters.
2. Trigger a **Dynamic Action** with parameters passed in the path.
3. Trigger a **Dynamic Action** with parameters passed as JSON in the body.
4. Stop the execution of Actions or Dynamic Actions.
5. Mute or unmute Actions to control their execution.

---

## **1. Execute a Simple Action**

**Endpoint:**  
`POST /api/v1/action/{id}`  

**Description:**  
Executes a simple Action by its ID.

**Parameters:**
- `id` (path) – The Action ID to execute.
- `apikey` (query or header) – API key for authentication.

**Responses:**
- `200` – Successful execution.
- `400` – Invalid ID supplied.
- `401` – Unauthorized.
- `404` – Action not found.

**Example Request:**
```bash
curl -X POST "https://example.com/api/v1/action/id_1?apikey=12345"
````

---

## **2. Execute a Dynamic Action (Parameters in Path)**

**Endpoint:**
`POST /api/v1/dynamicaction/{id}/parameters/{parameters}`

**Description:**
Executes a Dynamic Action by passing parameters directly in the path. Parameters must be provided in the format `key:value,key:value`.

**Parameters:**

* `id` (path) – Dynamic Action ID.
* `parameters` (path) – Comma-separated key\:value pairs for parameter substitution.
* `apikey` (query or header) – API key for authentication.

**Example of `parameters` string:**
`execution_times:5,port:127.0.0.1`

**Responses:**

* `200` – Successful execution.
* `400` – Invalid ID supplied.
* `401` – Unauthorized.
* `404` – Dynamic Action not found.

**Example Request:**

```bash
curl -X POST "https://example.com/api/v1/dynamicaction/id_1/parameters/execution_times:5,port:127.0.0.1?apikey=12345"
```

---

## **3. Execute a Dynamic Action (Parameters in JSON Body)**

**Endpoint:**
`POST /api/v1/dynamicaction/{id}`

**Description:**
Executes a Dynamic Action by passing parameters as JSON in the request body.

**Parameters:**

* `id` (path) – Dynamic Action ID.
* `apikey` (query or header) – API key for authentication.
* **Request Body (JSON)** – Keys correspond to the placeholders defined in the Dynamic Action (e.g., `{{execution_times}}`, `{{port}}`).

**Responses:**

* `200` – Successful execution.
* `400` – Invalid ID supplied.
* `401` – Unauthorized.
* `404` – Dynamic Action not found.

**Example Request:**

```bash
curl -X POST "https://example.com/api/v1/dynamicaction/id_1?apikey=12345" \
  -H "Content-Type: application/json" \
  -d '{
    "execution_times": 5,
    "port": "127.0.0.1"
  }'
```

---

## **4. Stop Action Execution**

### Stop a Simple Action

**Endpoint:**
`POST /api/v1/action/{id}/stop`

**Description:**
Stops the execution of a running simple Action.

**Example Request:**

```bash
curl -X POST "https://example.com/api/v1/action/id_1/stop?apikey=12345"
```

---

### Stop a Dynamic Action

**Endpoint:**
`POST /api/v1/dynamicaction/{id}/runningid/{runningId}/stop`

**Description:**
Stops a running Dynamic Action by specifying both the Action ID and the `runningId`.

**Example Request:**

```bash
curl -X POST "https://example.com/api/v1/dynamicaction/id_1/runningid/run_12345/stop?apikey=12345"
```

---

## **5. Mute or Unmute an Action**

### Mute Action

**Endpoint:**
`POST /api/v1/anyaction/{id}/mute`

**Description:**
Mutes an Action so it is instantly rejected when triggered.

**Example Request:**

```bash
curl -X POST "https://example.com/api/v1/anyaction/id_1/mute?apikey=12345"
```

---

### Unmute Action

**Endpoint:**
`POST /api/v1/anyaction/{id}/unmute`

**Description:**
Unmutes an Action, allowing it to be triggered again.

**Example Request:**

```bash
curl -X POST "https://example.com/api/v1/anyaction/id_1/unmute?apikey=12345"
```

---

## Summary

* Use the **Action ID** and **API Key** to authenticate and trigger executions.
* Dynamic Actions can accept parameters either **via the path** or **via JSON body**.
* Execution can be programmatically **stopped** or **muted/unmuted** as needed.
