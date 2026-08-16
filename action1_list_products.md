# Action 1 — List Products

**Endpoint**
```
GET /api/v1/products
```

## Description
Retrieves all published products. Supports optional filtering by category.

## Query Parameters
| Param | Type | Required | Example |
|---|---|---|---|
| `category` | string | No | `?category=electronics` |

## Authentication
None — public endpoint. Any client, authenticated or not, can list products.

## Request Example
```
GET /api/v1/products?category=electronics
```

## Success Response
**Status:** `200 OK`

Returns a JSON array of products (see `action1_response_example.json`).
An empty result set (no products match the filter) still returns `200 OK` with an
empty array `[]` — not `404`, since the collection itself exists.

## Why GET?
- Pure read operation — no data is modified.
- **Safe**: no side effects on the server.
- **Idempotent**: repeating the request any number of times returns the same result.
- The URL identifies a resource (`products`), not an action — consistent with REST
  principles.

## Why 200 OK?
The request succeeded and returns a body. Not `201` (no new resource was created) and
not `204` (there is a body to return).
