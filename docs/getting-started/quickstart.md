# Quickstart

This guide walks through making your first API call against
Web3aggregator in under 10 minutes.

## Prerequisites

- An API key (request access via the website)
- `curl` or any HTTP client

## 1. Authenticate

All requests authenticate via a bearer token in the `Authorization`
header.

```bash
export W3A_API_KEY="your-api-key"
```

## 2. Make your first request

```bash
curl https://api.web3aggregator.io/v1/health \
  -H "Authorization: Bearer $W3A_API_KEY"
```

Expected response:

```json
{
  "status": "ok",
  "region": "eu-helsinki",
  "version": "v1"
}
```

## 3. Query an RPC method

```bash
curl https://api.web3aggregator.io/v1/rpc/ethereum \
  -H "Authorization: Bearer $W3A_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "jsonrpc": "2.0",
    "method": "eth_blockNumber",
    "params": [],
    "id": 1
  }'
```

## Next steps

- Read about [authentication options](authentication.md)
- Explore the [REST API reference](../api/rest.md)
- Subscribe to events over [WebSocket](../api/websocket.md)
