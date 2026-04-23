## Add GET Order API

Adds `GET /orders/{order_id}` to the Agentic Checkout OpenAPI spec.

### New Endpoint

- **Method:** `GET`
- **Path:** `/orders/{order_id}`
- **Response:** Full `Order` object (current-state snapshot) or `404`
- **Auth:** Bearer token (same as checkout session endpoints)

### Motivation

ACP was previously webhook-only for order updates. This endpoint enables agents to retrieve
order state on demand — useful for reconciliation after missed webhooks, on-demand status
checks in response to buyer questions, and recovery after consumer restarts.

The response shape is the same `Order` schema used in webhook payloads, so consumers can
reuse the same parsing logic.

### Files Changed

- `spec/*/openapi/openapi.agentic_checkout.yaml` — New endpoint + `Orders` tag
- `rfcs/rfc.orders.md` — New section 6 documenting the retrieval API
